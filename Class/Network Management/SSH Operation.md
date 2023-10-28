## SSH Operation
* a secure protocol that uses TCP port 22.
* SSH provides security for remote connections by providing strong encryption when a device is authenticated (username and password) and also for the transmitted data between the communicating devices.
* Use the ==**show version**== command on the switch to see which IOS the switch is currently running.
	![[Pasted image 20231002174547.png]]
* On a PC, an SSH client such as PuTTY, is used to connect to an SSH server. For example, assume the following is configured:
	1. SSH is enabled on switch S1
	2. Interface VLAN 99 (SVI) with IPv4 address 172.17.99.11 on switch S1
	3.  PC1 with IPv4 address 172.17.99.21
	The figure shows the PuTTY settings for PC1 to initiate an SSH connection to the SVI VLAN IPv4 address of S1.
	![[Pasted image 20231002174559.png]]