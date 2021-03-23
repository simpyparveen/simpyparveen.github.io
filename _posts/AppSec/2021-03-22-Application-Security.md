## Application Security
Application security is important because today’s applications, although are better user expereience, it also increases the attack vector for the adversaries. These increasing vulnerabilities to security threats and breaches, calls for to not only ensure security at the network level but also within applications themselves. Application security testing can reveal weaknesses at the application level, helping to prevent these attacks.


### Types of application security

Different types of application security features include authentication, authorization, encryption, logging, and application security testing. Developers can also code applications to reduce security vulnerabilities.

Authentication: When software developers build procedures into an application to ensure that only authorized users gain access to it. Authentication procedures ensure that a user is who they say they are. This can be accomplished by requiring the user to provide a user name and password when logging in to an application. Multi-factor authentication requires more than one form of authentication—the factors might include something you know (a password), something you have (a mobile device), and something you are (a thumb print or facial recognition).
Authorization: After a user has been authenticated, the user may be authorized to access and use the application. The system can validate that a user has permission to access the application by comparing the user’s identity with a list of authorized users. Authentication must happen before authorization so that the application matches only validated user credentials to the authorized user list.
Encryption: After a user has been authenticated and is using the application, other security measures can protect sensitive data from being seen or even used by a cybercriminal. In cloud-based applications, where traffic containing sensitive data travels between the end user and the cloud, that traffic can be encrypted to keep the data safe. 
Logging: If there is a security breach in an application, logging can help identify who got access to the data and how. Application log files provide a time-stamped record of which aspects of the application were accessed and by whom. 
Application security testing: A necessary process to ensure that all of these security controls work properly.

### Threat modeling frameworks
Among so many commercially available threat modelling techniques to find vulnerabilities in applications and software, I personally used following to study, work, research and tutor. 

1) OWASP Top 10

The Open Web Application Security Project (OWASP) Top 10 is mostly used threat model used at enterprises for securing web applications, to feed rules when developing web application firewall softwares used to be used as analytics tools to detect the common or dangerous vulnerabilities in web applications. The OWASP Top Ten list is a typically used when performing a threat modeling for web applications, however, it is can generally be applied to other types of software as well.

2) MITRE ATT&CK Framework and CWE
 
The research and development center (FFRDC) of the US government funds MITRE, for cybersecurity research, and therefore developed MITRE ATT&CK framework.
This is a multipurpose framework that covers grounds on threat modeling, penetration testing, defense development and similar cybersecurity exercises. MITRE ATT&CK breaks the lifecycle of a cyberattack into fourteen stages (called “Tactics” by MITRE). Each of these Tactics describes a specific goal that an attacker may need to achieve on their way to achieving their overall objective such as escalating privileges or gaining access to account credentials.

Additionly, MITRE also maintains the Common Weakness Enumeration, as a resource comprehensive list of potential security issues and includes a list of the top 25 threats based on the probability of exploitation and impact of different CWEs, to describe the common vulnerabilities and other issues that can exist within an application.

I used MITRE Attac model as IoCs(Indicators of Compromise), to find the intrusion with high degree of confidence. It can only address known threats. Egs: Antivirus signatures, unexpected hashes, malicious file names, IP address, URL and domains.

It uses behavioral model based on 5 principles: 
i. Include post-comprmise detetction: For identifying theats thatbypass established defenses
ii. Focus n behaviour: Helps address limitations of signatures
iii. Use threat model approach: To ensure detections are effective
iv. Iterate by design: Accounts for changing behaviour of the adversary. Eg: sematically creating various versions of same malware signature. 
v. Develop and test in realistic environment.



3) STRIDE threat modeling
This is really cool stuff by Microsoft!! I taught several in-class interactive excercises to tutor STRIDE method of threat modelling

The STRIDE threat model is focused on the potential impacts of different threats to a system:
i. Spoofing: Violates security property *Authentication*
ii. Tampering: Violates security property *Integrity*
iii. Repudiation: Violates security property *nNon-repudiation*
iv. Information disclosure: Violates security property *Confidentiality*
v. Denial of service: Violates security property *Availability*
vi. Escalation of privileges: Violates security property *Authorization*

#### When, during the SDLC, do we perform threat modelling??
At the beginning of system model, as well as throughout the development of features. We first apply top-down then work across breadth-first, before diving deep into any components.  

#### Alternatives: Attack libraries and Attack trees
STRIDE may be too high-level approach, it is easier to use an existing library what has similar goal as your system design. Attack libraries at rescue.

Attack trees are alternative to STRIDE method. It provides logical and systematic approach to evaluate security of our system based on various attacks as if we are the RED Team. We formualte a tree structure where the root is the goal of the attacker, and leaf nodes describing ways to reach the parent node.


