# TCP Session Hijack

The objective of the TCP Session Hijacking attack is to hijack an existing TCP connection (session) between two victims by injecting malicious contents into this session. 

If this connection is a telnet session, attackers can inject malicious commands (e.g. deleting an important file) into this session, causing the victims to execute the malicious commands. 

![telnethijack](/assets/networksecurity/telnethijack.png){:height="75%" width="75%"}

Steps:

1. Create TCP connection between two VMs, here we do Telnet, say A(User) and B(Server), by running following command on A’s terminal:
	*$ sudo telnet ip_of_B*

2. Use Wireshark on Attacker machine(Machine C) to observe the latest TCP connection’s sequence number.

*Note: If you use Wireshark to observe the network traffic, you should be aware that when Wireshark displays the TCP sequence number, by default, it displays the relative sequence number, which equals to the actual sequence number minus the initial sequence number. If you want to see the actual sequence number in a packet, you need to right click the TCP section of the Wireshark output, and select "Protocol Preference". In the popup window, uncheck the "Relative Sequence Number and Window Scaling" option. *

3. Observe the last data packet sent from User to Server in wireshark pcap captures. It has two sequence numbers, (i) “Sequence number”, and (ii) “Next sequence number”. 
We should use the second number, which equals to the first number plus the length of the data we want to send.

4. From the sniffed packet, we also get the source and the destination port numbers.

5. The attacker uses *Netwox Tool 40* as below from the attacker’s machine. Below figure shows Netwox toolnumber 40 parameters:

![netwox40](/assets/networksecurity/netwox40.png){:height="75%" width="75%"}

6. To find *"mixed_data"*, we can use Python to convert a command into hex. Here, we want to simply run ls command and see the folder files on server’s machine. Go to terminal and type : 	
      *$python*
	    *>>”ls”.encode(“hex”)*

7. Perform the attack using: *$ sudo netwox 40 --ip4-src 10.211.55.3 --ip4-dst 10.211.55.4 --tcp-src 55642 --tcp-dst 23 --tcp-seqnum 2122485892 --tcp-data '6c73'*. This will show the packet we constructed, as below:
    ![spoofedtcpnetwox40](/assets/networksecurity/spoofedtcpnetwox40.png){:height="75%" width="75%"}

8. See that Wireshark displays the traffic appears, when attack is successful.  Alternatively, use : *netstat -tna*


Results: 

If the attack is successful, we see that the telnet session of the user freezes the application, and Wireshark displays retransmission packets between User and Server. In reality, deadlock between the client and the server is reached. One side will keep resending their data to each other and the other side keeps dropping the data. TCP will disconnect the connection after it reaches maximum retransmission tries.






