# TCP RESET Attack
The TCP RST Attack can terminate an established TCP connection between two victims. For example, if there is an established telnet connection (TCP) between two users A and B, attackers can spoof a RST packet from A to B, breaking this existing connection. To succeed in this attack, attackers need to correctly construct the TCP RST packet. 


## On Telnet
In this task, I launch an TCP RST attack from C to break an existing telnet connection between A and B, as shown in below diagram:

![reset](/assets/resettelnet.png){:height="50%" width="50%"}

Follow steps to perform the attack:

1. Create Telnet connection between two VMs, say A and B, by running following command on A’s terminal: *sudo telnet ip_of_B* 
    
    Let’s assume User (10.0.2.18) and Server (10.0.2.17).

2. Retrieve the Destination port, Destination IP, Source port number , Source IP and sequence number from Wireshark captured packet. 

We look at the most recent TCP packet from the User to the Server. We spoof the packet to Server, here. (Attacker can send RESET spoof packet to either Server or User).
Preparing Spoofed RST Packet. The following fields need to be set correctly:
    * Source IP address, Source Port
    * Destination IP address, Destination Port
    * Sequence number (within the receiver’s window)

*Right-click on sequence number field and select Protocol Preferences and uncheck relative sequence number.*
 
 Before attack, observe wireshark packets: 
 
 ![reset](/assets/telnetbeforeattack.png){:height="50%" width="50%"}
 
3. Use Netwox Tool 40 as below from the attacker’s machine. Use netwox --help to find the manual. Using netwox tool 40, we can generate a spoofed RST packet to the client or server as follows:

4. If the attack is successfulll, the victim machine will shows “Connection termination” message on the terminal.

![reset](/assets/telnetafterattack.png){:height="50%" width="50%"}

Observe that wireshark packet capture shows TCP RST packet with the RST flag set to 1.

![reset](/assets/telnet1.png){:height="50%" width="50%"}

5. What happens when I try RESET attack on ssh connection ???

## On SSH
Performing similar attack to reset SSH connection results in broken pipe. So, if we try to perform any terminal task, the SSH shows connection termination. 

![reset](/assets/resetsshsuccess.png){:height="70%" width="70%"}


Observe that wireshark packet capture shows TCP RST packet with the RST flag set to 1.

![reset](/assets/sshsuccessreset.png){:height="50%" width="50%"}





