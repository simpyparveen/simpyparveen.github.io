## Heartbleed-Attack

### SSL Certificate
Secure communication on the Internet is built around the trust of digital certificates offered by Public Key Infrastructure. A certificate is a message signed by a publicly trusted authority (Certificate Authority) which includes a public key and additional data, such as expiration date, serial number and information regarding the key and the subject entity. 
There are many well-known commercial CAs such as Verisign, Entrust, Globalsign, Comodo. Web servers present a digital certificate to browsers as authentication, synonymous to people presenting an official picture ID as proof of identity. When the browser is satisfied that all certificates in the chain are valid and have not been revoked, the connection can proceed.
The CAs can perform revocation of certificates for its servers at any time and for any reason, however, some of the common reasons include: the private key corresponding to the certificate has been lost or stolen, the domain name of the subject has changed or the subject is no longer in service.  
The problem of certificate revocation is getting more and more crucial with the development of wide spread PKIs. 


### Heartbeat Protocol
Heartbeat protocol is used by SSL/TLS to keep the connection alive. Occasionally, one of the computers will send an encrypted piece of data, called a heartbeat request and length parameter of the encrypted data, to the other. The second computer stores this data to its memory, later replies back with the exact same encrypted piece of data by reading from the memory for length that was provided, proving that the connection is still in place. 

Heartbeat Request: Alice ----------------(*Enc_data, length*)------------------------> Bob
                                                                                     // Stores encrypted data in memory
                                                                                     // Prepares back reply by reading *length* bytes from memory 

Heartbeat Response: Alice <--------(*Enc_data+#$^$@^#^##@%$@#&^%@&, length*)------- Bob


### Heartbleed Vulnerability
The vulnerability occurs because the second computer does not validate if the length of the encrypted data matches the length field that was send with the request.

The vulnerability is in the implementation of the implementation of OpenSSL version range is from 1.0.1 to 1.0.1f. It is considered as one of the worst flaw in the OpenSSL library, that allows adversary to read unauthorized memory of the victim. The contents of the unauthorized memory location could have critical information, such as, private keys, TLS session keys, user names, passwords, credit cards, etc. 

The recent Heartbleed vulnerability (CVE-2014-0160) resulted in thousands of revoked SSL certificates from vulnerable servers that should no longer be trusted. Revocation checking is inevitably a required step whenever a certificate or digital signature is accepted. 


### Countermeasure
Industries took three main remediations to counter the Heartbleed bug:
1. Software Patching: Update your software to the latest versions of OpenSSL
2. Creation of New Private Keys: Creating new private keys will prevent an attacker, who already exploited the flaw before patching, from being able to spy on your encrypted.
3. Issuing of New SSL Certificates: To remove the ability of possible phising threats by any adversary.
