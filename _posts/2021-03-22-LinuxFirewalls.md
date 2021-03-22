# Linux Firewall

In this lab I explore the insights on how firewalls work by experimenting with network security rules using firewall software and implement a simplified packet filtering firewall. 
We use ufw to set up some firewall policies, and observe the behaviors of your system after the policies become effective.

## Tools used
Linux has a tool called iptables, which is essentially a firewall. It has a nice front-end program called ufw. 
ufw is a front-end for netfilter/iptables, the Linux mechanism for routing and filtering internet traffic. ufw(uncomplicated firewall) : The default firewall configuration tool for Ubuntu is ufw. Developed to ease iptables firewall configuration, ufw provides a user-friendly way to create an IPv4 or IPv6 host-based firewall. By default, UFW is disabled.

•	You can find the manual of ufw: *$ man ufw*

•	Check the status of ufw as below : *$ sudo ufw status*

## Pre-requisites
Before starting the task, go to the default policy file /etc/default/ufw. Find the following entry and change the rule from DROP to ACCEPT; otherwise, all the incoming traffic will be dropped by default.

![firewall0](/assets/networksecurity/firewall0.png){:height="75%" width="75%"}

## Tasks to be performed

1. Prevent Machine A from doing telnet to Machine B
  *$ sudo ufw deny out from Ip_of_A to Ip_of_B port 23*

2. Prevent Machine B from doing telnet to Machine A
  *$ sudo ufw deny in from Ip_of_B to Ip_of_A port 23*
  
  ![firewall3](/assets/networksecurity/firewall3.png){:height="75%" width="75%"}
  
3. Prevent Machine A from visiting an external web site. You can choose any web site that you like to block, but keep in mind, some web servers have multiple IP addresses. 

i) Traceroute the website to find the IP address:
			*$ traceroute www.facebook.com*
		
ii) Block the IP address(blocks the entire subnet)
			*$ sudo ufw deny out to 157.240.3.0/24*
		
iii) Result below :

![firewall3](/assets/networksecurity/firewall3.png){:height="75%" width="75%"}


### Glossary (ufw Cheat Sheet)

1. Allow connection for specific IP address : 
	# sudo ufw allow from 10.211.55.3

2. Allow connection for specific IP address :
	# sudo ufw allow from 10.211.55.3

3. Allow TCP connections on port 80 : 
	# sudo ufw allow 80/tcp
	# sudo ufw deny 80/udp

4. Allow interface rules : 
	# sudo ufw allow in on eth0 to any port 80

5. Block outgoing connection on ports :
	# sudo ufw deny out 3389

6. Combinations :- 
	i) Allow specific IP to port 22
		# sudo ufw allow from 10.211.55.4 to any port 22
7. Delete certain rules we created.
	# sudo ufw delete allow 80

	Or Delete rule by number :
	Syntax : # Sudo ufw status numbered
	Eg : 	       # sudo ufw status 8080

