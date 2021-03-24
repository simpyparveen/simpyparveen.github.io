# Transport layer Security (TLS)
It is the most widely used protocol security protocol; that provides authentication, confidentiality, and integrity to ensure data exchange. 

TLS is composed of two protocols: 
(i) TLS handshake protocol, that starts a connection between a client and server to agree upon a shared secret and cipher suites, and 
(ii) TLS record protocol, that starts once the handshake is complete and exchanges data protected with negotiated keys and cipher suites. 


Although TLS 1.2 protocol is considered much more reliable than previous versions, TLS 1.3, released in 2018, provides a more secure and faster handshake than using state-of-the-art cryptographic algorithms with no known vulnerabilities. 
The major differences between TLS 1.2 and TLS 1.3 include: 
(a) AEAD-only ciphers for encryption and authentication at record layer 
(b) 0-RTT mode was added, saving a round-trip at connection setup 
(c) forward secrecy is mandatory using public-key based key exchange mechanisms. 
(d) compression methods are removed. 
(e) the handshake messages after the *Server Hello* is encrypted in TLS 1.3, while TLS 1.2 started encrypting with the first finished message. 
(f) key derivation functions to use HMAC-based Extract-and-Expand Key Derivation Function (HKDF).

TLS is normally implemented on top of TCP in order to encrypt Application Layer protocols such as HTTP, FTP, SMTP, etc.

[Ref:TLS Handshake Explained](https://www.thesslstore.com/blog/explaining-ssl-handshake/#the-tls-12-handshake-step-by-step)



### TLS/SSL Handshake Explanation Using Wireshark

1. Start Wireshark on your machine.
2. Browse a website such as cibc.com.
3. Stop Wireshark Capture and look at the packets after filtering ssl traffic, as shown below: 

![ws-tls1](/assets/applicationsecurity/ws-tls1.png){:height="75%" width="75%"}

4. We can choose to see the ssl stream: Click on one packet and right click to Follow-> SSL Stream. This might not show any useful data but will put a filter. We also add “&& ssl” to the filter expression.

![ws-tls2](/assets/applicationsecurity/ws-tls2.png){:height="75%" width="75%"}

5. In the above screenshot we see packets containing: Client Hello, Server Hello, Certificate, etc. 

6. Click on Client Hello and see the content:

![ws-tls3](/assets/applicationsecurity/ws-tls3.png){:height="75%" width="75%"}

7. There are 14 Cipher suite supported by the default browser from which server negotiates and chooses one of them:
  
  ![ws-tls4](/assets/applicationsecurity/ws-tls4.png){:height="75%" width="75%"}
  
8. When we see the corresponding Server Hello, we see that Cipher suite selected by the server. 

![ws-tls5](/assets/applicationsecurity/ws-tls5.png){:height="75%" width="75%"}

9. We can also see the certificate provided by the server as below :

![ws-tls6](/assets/applicationsecurity/ws-tls6.png){:height="75%" width="75%"}


### Can Wireshark capture https request? How to Decrypt SSL and TLS Traffic Using Wireshark ?

Wireshark captures all traffic on a network interface. The thing with HTTPS is that it is application layer encryption. Wireshark is not able to decrypt the content of HTTPS. This is because HTTPS encrypts point to point between applications.

#### Attack Goal: This article describes how to decrypt SSL and TLS traffic using the Wireshark network protocol analyzer. 

In Wireshark, the SSL dissector is fully functional and supports advanced features such as decryption of SSL, if the encryption key is provided. 

Tools Needed: 
1.	Wireshark 
2.	SSL with decryption keys. (Details is given in the Overview)
3.	Captured SSL packets. (Details is given in the Overview)

*Note: The Diffie Hellman (DHE) ciphers cannot be decrypted. The server certificate cipher suite can be seen in the server hello/certificate frame during the SSL handshake.*


Complete the following steps to decrypt SSL and TLS traffic using the Wireshark network protocol analyzer:

i.	Go to [link](https://wiki.wireshark.org/SampleCaptures?action=AttachFile&do=get&target=snakeoil2_070531.tgz) given in the references and search for description “SSL with decryption keys”. Download the file: snakeoil2_070531.tgz

ii.	Unzip the file and you see an example of SSL encrypted HTTPS traffic and the key to decrypt it.

iii.	Setting up Wireshark to use the decryption keys : *Wireshark -> Edit -> Preferences... -> Protocol -> SSL*
 ![ssldecrypt1](/assets/applicationsecurity/ssldecrypt1.png){:height="75%" width="75%"}
 
![ssldecrypt2](/assets/applicationsecurity/ssldecrypt2.png){:height="75%" width="75%"}

iv. 	RSA keys list must be selected from the keys downloaded above :
![ssldecrypt3](/assets/applicationsecurity/ssldecrypt3.png){:height="75%" width="75%"}

v. Browse to the location of your log file(decrypt already captured file given in the example downloaded above).
![ssldecrypt4](/assets/applicationsecurity/ssldecrypt4.png){:height="75%" width="75%"}

vi. This is more along the lines of what we normally see when look at a TLS packet :
![ssldecrypt5](/assets/applicationsecurity/ssldecrypt5.png){:height="75%" width="75%"}


vii. This is what it looks like when you switch to the “Decrypted SSL Data” tab.  Note that we can now see the request information in plain-text. 
![ssldecrypt6](/assets/applicationsecurity/ssldecrypt6.png){:height="75%" width="75%"}


#### Conclusion 
The idea here is that HTTPS traffic that travels over the Internet is confidential, a random router or person who happens to capture your packages cannot decrypt the HTTPS without the decryption key.

*So bottomline: Wireshark cannot decrypt HTTPS traffic without the decryption key.*

