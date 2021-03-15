## TCP/IP Attack Lab

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

  1. Syn Flood Attack 
  2. TCP RST Attack on Telnet
  3. TCP RST Attack on SSH
  4. TCP RST Attack on Video Streaming
  5. DNS and Firewall Exploration





1. First ordered list item
2. Another item
⋅⋅* Unordered sub-list. 
1. Actual numbers don't matter, just that it's a number
⋅⋅1. Ordered sub-list
4. And another item.

⋅⋅⋅You can have properly indented paragraphs within list items. Notice the blank line above, and the leading spaces (at least one, but we'll use three here to also align the raw Markdown).

⋅⋅⋅To have a line break without a paragraph, you will need to use two trailing spaces.⋅⋅
⋅⋅⋅Note that this line is separate, but within the same paragraph.⋅⋅
⋅⋅⋅(This is contrary to the typical GFM line break behaviour, where trailing spaces are not required.)

* Unordered list can use asterisks
- Or minuses
+ Or pluses
