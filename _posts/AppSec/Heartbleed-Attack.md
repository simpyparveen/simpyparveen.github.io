## Heartbleed-Attack

### SSL Certificate
Secure communication on the Internet is built around the trust of digital certificates offered by Public Key Infrastructure. A certificate is a message signed by a publicly trusted authority (Certificate Authority) which includes a public key and additional data, such as expiration date, serial number and information regarding the key and the subject entity. 
There are many well-known commercial CAs such as Verisign, Entrust, Globalsign, Comodo. Web servers present a digital certificate to browsers as authentication, synonymous to people presenting an official picture ID as proof of identity. When the browser is satisfied that all certificates in the chain are valid and have not been revoked, the connection can proceed.
The CAs can perform revocation of certificates for its servers at any time and for any reason, however, some of the common reasons include: the private key corresponding to the certificate has been lost or stolen, the domain name of the subject has changed or the subject is no longer in service.  
The problem of certificate revocation is getting more and more crucial with the development of wide spread PKIs. 


### Heartbleed Vulnerability
The recent Heartbleed vulnerability resulted in thousands of revoked certificates from vulnerable servers that should no longer be trusted. Revocation checking is inevitably a required step whenever a certificate or digital signature is accepted. 


### Tools


### Performing the Attack


### Countermeasure
