# Transferring Files between two machines 
Just some utility that might help transfer files between two machines easier. 

FileZilla is an application software to use when you want to transfer files from your local machine to a remote machine(vm) or server.

Here are the steps for installation and usage:

1) Download filezilla software as per your OS from : [link](https://filezilla-project.org/)

2) Left side is your local machine file structure and right side is empty because you are not connected to server where to/from you want to exchange files.

![filezilla1](/assets/networksecurity/filezilla1.png){:height="75%" width="75%"}

3) Connect to remote host – server or virtual machine
	  Host: 		IP address of the vm or server (we want to connect to seed vm)
	  Username: 	seed
	  Password: 	dees
	  Port: 		22     (This is SFTP file transfer protocol) 

![filezilla2](/assets/networksecurity/filezilla2.png){:height="75%" width="75%"}

4) After connecting to remote host, you see the folder structures of it as shown below :

![filezilla3](/assets/networksecurity/filezilla3.png){:height="75%" width="75%"}

5) Drag and Drop files you want to transfer from and to the remote and local hosts. As you see below, I dragged and dropped premaster.txt from my local machine to remote host.

![filezilla4](/assets/networksecurity/filezilla4.png){:height="75%" width="75%"}


Easy right !! 
