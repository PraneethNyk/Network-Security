# Security key-based network access control in cloud instances

## Problem Statement
To provide a secure key-based network authentication for headless Linux systems in cloud instances that use network access control (NAC) and prevent credential leakage via virtual machine (VM) disk images. This involves implementing certificate-based authentication in netplan and utilizing encrypted file systems or disk volumes to ensure zero-leakage of authentication credentials. The goal is to obtain fine-grained identity information (user, instance/device) from network logs to improve security in cloud instances, especially as they are increasingly being used for cybercrime hosting services.

## Encrypting the keys stored in file system
We have used LUKS to encrypt the partition in our linux system. We have used some commands that you can see in report as well as presentation.We have provided screenshots also for your reference.Actually this tool (LUKS) is only we have used to encrypt file system.

## Certificate based authentication using radius server
We have modified the netplan file of our allocated VM such that it will be useful in certificate based authentication. First of all we have created second interface for connection as don't want to be disconnected after modifying the netplan using \
netplan apply  command    \
For radius server testing we have used command: radtest -x xt21t001 U6bnQmHY 192.168.50.7 -0 testing123 radiussrv   \
Above command is also written in report and presentation.   \
We have captured traffic while authentication we have used command: sudo tcpdump -i ens7 -w radtest.pcap “not port ssh”  \
For more of work, we have also provided commands in presentation and report also.

## Conclusion
1. Using LUKS, we can encrypt the partition and the certificates are stored in the
encrypted partition. So, there wont be any problem as passphrase is required to access
certificates.  
2. By modifying NETPLAN configuration file, the networking on our sytem can be
configured.ex, managing interfaces,authentication methods, etc.
 