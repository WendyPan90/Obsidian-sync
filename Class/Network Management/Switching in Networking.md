## Switching in Networking
* The decision on how a switch forwards traffic is made based on the flow of that traffic. There are two terms associated with frames entering and leaving an interface:
	* ==**Ingress**== - This is used to describe the port where a frame enters the device.
	* ==**Egress**== - This is used to describe the port that frames will use when leaving the device.
* A LAN switch forwards traffic based on the **ingress port** and the **destination MAC address** of an Ethernet frame.
* an Ethernet frame with a given destination address always exits the same egress port, regardless of the ingress port it enters.
* An Ethernet frame will never be forwarded out the same port it was on which it was received.
	![[Pasted image 20231002175331.png]]
* Switches use destination MAC addresses to direct network communications through the switch, out the appropriate port, toward the destination.
* ==**MAC address table**==: 
	* stored in content addressable memory (CAM內容可定址記憶體) which is a special type of memory used in high-speed searching applications.
	* sometimes also called the CAM table.
* LAN switches determine how to handle incoming data frames by maintaining the MAC address table.
* The Switch learn and forward method:
	* Step 1. Learn - Examining(檢查) the Source MAC Address.
	* Step 2. Forward - Examining the Destination MAC Address.
* Layer 2 switches use one of two methods to switch frames:
		* ==**Store-and-forward switching**== - This method makes a forwarding decision on a frame after it has received the entire frame and checked the frame for errors using a mathematical error-checking mechanism known as a cyclic redundancy check (CRC). Store-and-forward switching is Cisco’s primary LAN switching method.
	- ==**Cut-through switching**== - This method begins the forwarding process after the destination MAC address of an incoming frame and the egress port have been determined.