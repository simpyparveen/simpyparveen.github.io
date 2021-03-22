## Network Security

The vulnerabilities in the TCP/IP protocols represent a special genre of vulnerabilities in protocol designs and implementations. 

### What is TCP/IP 
TCP/IP or Transmission Control Protocol/Internet Protocol, is a suite of end-to-end communication protocols that specifies exchanged of information over the internet using two protocols TCP protocol and IP protocol. These protocols identify and manage how it should be broken into packets, addressed, transmitted, routed and received at the destination. 

TCP handles communication channels for the application, across a network, that involves:

  1. Assemble and reassembly 
  2. Order of delivery of transmitted packets over the internet

IP defines:

  1. How to address and route each packet to make sure it reaches the right destination. 
  2. Each gateway computer on the network checks this IP address to determine where to forward the message.

In the following experiements, I conduct several attacks on the TCP/IP protocols to demonstrate invaluable lesson as to why security should be designed in from the beginning, rather than being added as an afterthought. 

  1. [Syn Flood Attack](https://simpyparveen.github.io/blog/2021/03/21/TCPSessionHijack)
  2. [TCP RST Attack](https://simpyparveen.github.io/blog/2021/03/15/TCP-RESETAttack)
  3. [TCP Session Hijack](https://simpyparveen.github.io/blog/2021/03/21/TCPSessionHijack)
  4. [Linux Firewall Exploration](https://simpyparveen.github.io/blog/2021/03/22/Linux-Firewalls)
  5. [Heartbleed Attack Lab] ()
