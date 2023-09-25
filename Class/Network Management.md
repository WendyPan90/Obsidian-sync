## Duplex Communication
* ==**Full-duplex communication**== increases bandwidth efficiency by allowing both ends of a connection to transmit and receive data simultaneously.
* ==**Half-duplex communication**== creates performance issues because data can flow in only one direction at a time, often resulting in collisions.
![[Pasted image 20230325113345.png]]

## Switch Ports
![[Pasted image 20230325113653.png]]
* ==**Autonegotiation**== is useful when the speed and duplex settings of the device connecting to the port are unknown or may change.

## Auto-MDIX
* Switch-to-switch or switch-to-router connections required using different Ethernet cables.
* When auto-MDIX is enabled, the interface automatically detects the required cable connection type (straight-through or crossover) and configures the connection appropriately.
* straight-through cables must be used to connect to devices such as servers, workstations, or routers. Crossover cables must be used to connect to other switches or repeaters.
* to enable auto-MDIX:
	![[Pasted image 20230325114845.png]]
	**Note**: The auto-MDIX feature is enabled by default on Catalyst 2960 and Catalyst 3560 switches

## Verify Switch Port Configuration
* The ==**show running-config**== command can be used to verify that the switch has been correctly configured.
	![[Pasted image 20230325115506.png]]
	* The ==**show interfaces**== command is another commonly used command, which displays status and statistics information on the network interfaces of the switch. It's frequently used when configuring and monitoring network devices.
	* 
## Network Access Layer Issues
* The output from the **show interfaces** command is useful for detecting common media issues. For example: 
	![[Pasted image 20230325120008.png]]
	* possible problems can be fixed as follows:
		1. If the interface is up and the line protocol is down, a problem exists. There could be an encapsulation type mismatch, the interface on the other end could be error-disabled, or there could be a hardware problem.
		2.  If the line protocol and the interface are both down, a cable is not attached, or some other interface problem exists. For example, in a back-to-back connection, the other end of the connection may be administratively down.
		3. If the interface is administratively down, it has been manually disabled (the **shutdown** command has been issued) in the active configuration.
		### **Error Type**
		**Input Errors**
			Total number of errors. It includes runts, giants, no buffer, CRC, frame, overrun, and ignored counts.
		**Runts**
			Frames that are discarded because they are smaller than the minimum frame size for the medium. For instance, any Ethernet frame that is less than 64 bytes is considered a runt.
		**Giants**
			Frames that are discarded because they exceed the maximum frame size for the medium. For example, any Ethernet frame that is greater than 1,518 bytes is considered a giant.
		**CRC**
			CRC errors are generated when the calculated checksum is not the same as the checksum received.
		**Output Errors**
			Sum of all errors that prevented the final transmission of datagrams out of the interface that is being examined.
		**Collisions**
			Number of messages retransmitted because of an Ethernet collision.
		**Late Collisions**
			A collision that occurs after 512 bits of the frame have been transmitted.
	

## Interface Input and Output Errors
* “==**Input errors**==” is the sum of all errors in datagrams that were received on the interface being examined.The reported input errors from the **show interfaces** command include the following:
	-   ==**Runt Frames**== - Ethernet frames that are shorter than the 64-byte minimum allowed length are called runts. Malfunctioning NICs are the usual cause of excessive runt frames, but they can also be caused by collisions.
	-   ==**Giants**== - Ethernet frames that are larger than the maximum allowed size are called giants.
	-   ==**CRC errors**== - On Ethernet and serial interfaces, CRC errors usually indicate a media or cable error. Common causes include electrical interference, loose or damaged connections, or incorrect cabling. If you see many CRC errors, there is too much noise on the link and you should inspect the cable. You should also search for and eliminate noise sources.
* “==**Output errors**==” is the sum of all errors that prevented the final transmission of datagrams out the interface that is being examined. The reported output errors from the **show interfaces** command include the following:
	* -   ==**Collisions**== - Collisions in half-duplex operations are normal. However, you should never see collisions on an interface configured for full-duplex communication.
	-   ==**Late collisions**== - A late collision refers to a collision that occurs after 512 bits of the frame have been transmitted. Excessive cable lengths are the most common cause of late collisions. Another common cause is duplex misconfiguration. For example, you could have one end of a connection configured for full-duplex and the other for half-duplex. You would see late collisions on the interface that is configured for half-duplex. In that case, you must configure the same duplex setting on both ends. A properly designed and configured network should never have late collisions.


## SSH Operation
* a secure protocol that uses TCP port 22.
* SSH provides security for remote connections by providing strong encryption when a device is authenticated (username and password) and also for the transmitted data between the communicating devices.
* Use the ==**show version**== command on the switch to see which IOS the switch is currently running.
	![[Pasted image 20230325123829.png]]
* On a PC, an SSH client such as PuTTY, is used to connect to an SSH server. For example, assume the following is configured:
	1. SSH is enabled on switch S1
	2. Interface VLAN 99 (SVI) with IPv4 address 172.17.99.11 on switch S1
	3.  PC1 with IPv4 address 172.17.99.21
	The figure shows the PuTTY settings for PC1 to initiate an SSH connection to the SVI VLAN IPv4 address of S1.
	![[Pasted image 20230325125311.png]]

## Basic Router
* to be able to send and receive data outside of your network, you will have to configure routers.

## Dual Stack Topology
* The dual stack topology in the figure is used to demonstrate the configuration of router IPv4 and IPv6 interfaces.
	![[Pasted image 20230325131216.png]]

## Configure Router Interfaces
* an interface must be:
	* ==**Configured with at least one IP address**== - Use the **ip address** _ip-address subnet-mask_ and the **ipv6 address** _ipv6-address/prefix_ interface configuration commands.
	- ==**Activated**== - By default, LAN and WAN interfaces are not activated (**shutdown**). To enable an interface, it must be activated using the **no shutdown** command. (This is similar to powering on the interface.) The interface must also be connected to another device (a hub, a switch, or another router) for the physical layer to be active.
	- ==**Description**== - Optionally, the interface could also be configured with a short description of up to 240 characters. It is good practice to configure a description on each interface. On production networks, the benefits of interface descriptions are quickly realized as they are helpful in troubleshooting and in identifying a third-party connection and contact information.

## IPv4 Loopback Interfaces
* The loopback interface is a logical interface that is internal to the router.
* is considered a software interface that is automatically placed in an “up” state, as long as the router is functioning.
*  is useful in testing and managing a Cisco IOS device because it ensures that ==**at least one**== interface will always be available.
*  are also commonly used in lab environments to create additional interfaces.
* **Multiple** loopback interfaces can be enabled on a router.
* The IPv4 address for each loopback interface must be unique and unused by any other interface.
	![[Pasted image 20230325134123.png]]

## Interface Verification Commands
* The following commands are especially useful to quickly identify the status of an interface:
	-   ==**show ip interface brief**== and ==**show ipv6 interface brief**== - These display a summary for all interfaces including the IPv4 or IPv6 address of the interface and current operational status.
	-   ==**show running-config interface**== _interface-id_ - This displays the commands applied to the specified interface.
	-   ==**show ip route**== and ==**show ipv6 route**== - These display the contents of the IPv4 or IPv6 routing table stored in RAM. In Cisco IOS 15, active interfaces should appear in the routing table with two related entries identified by the code ‘**C**’ (Connected) or ‘**L**’ (Local). In previous IOS versions, only a single entry with the code ‘**C**’ will appear.
* The following two commands are used to gather more detailed interface information:
	-   ==**show interfaces**==- Displays interface information and packet flow count for all interfaces on the device.
	-   ==**show ip interface**== and ==**show ipv6 interface**== - Displays the IPv4 and IPv6 related information for all interfaces on a router.

## Switching in Networking
* The decision on how a switch forwards traffic is made based on the flow of that traffic. There are two terms associated with frames entering and leaving an interface:
	* ==**Ingress**== - This is used to describe the port where a frame enters the device.
	* ==**Egress**== - This is used to describe the port that frames will use when leaving the device.
* A LAN switch forwards traffic based on the **ingress port** and the **destination MAC address** of an Ethernet frame.
* an Ethernet frame with a given destination address always exits the same egress port, regardless of the ingress port it enters.
* An Ethernet frame will never be forwarded out the same port it was on which it was received.
	![[Pasted image 20230325143034.png]]
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
	- 
## Store-and-Forward Switching
* 交換器會先把Frame完全接收下來，然後才進行轉發。LAN交換器會把每個完整的Frame儲存到switch的記憶體緩衝區中，並且在轉發之前檢查錯誤。
   迴圈冗餘校驗(Cyclic redundancy check，簡稱”CRC”)，是一種資傳輸檢錯功能，透過數學公式來校驗接收到的Frame。
   通過CRC檢查後，Frame才會被轉發到目的端MAC位址；如果檢查失敗，損壞的Frame就會被丟棄。此過程能夠確保高品質的資料傳輸，因為接收端不會受到損壞Frame的影響。
* following two primary characteristics:
	* ==**Error checking**== - After receiving the entire frame on the ingress port, the switch compares the frame check sequence (FCS) value in the last field of the datagram against its own FCS calculations. The FCS is an error checking process that helps to ensure that the frame is free of physical and data-link errors. If the frame is error-free, the switch forwards the frame. Otherwise, the frame is dropped.
	- ==**Automatic buffering**== - The ingress port buffering process used by store-and-forward switches provides the flexibility to support any mix of Ethernet speeds. For example, handling an incoming frame traveling into a 100 Mbps Ethernet port that must be sent out a 1 Gbps interface would require using the store-and-forward method. With any mismatch in speeds between the ingress and egress ports, the switch stores the entire frame in a buffer, computes the FCS check, forwards it to the egress port buffer and then sends it.
	![[Pasted image 20230325150230.png]]

## Cut-Through Switching
* 交換器接收到Frame時，會先抓取目的端MAC位址(也就是接在preamble後面的前6個bytes)。然後，LAN交換器會在它的交換表(switch table)中檢查目的MAC位址，並確定輸出介面埠，再將Frame轉發到目標位址。
   過程中不會執行CRC錯誤檢查。因此，所有的Frame(不論有無錯誤)都會被轉發到接收端交換器。由接收端進行錯誤檢查，以確保傳輸無差錯。
   為了改善這種情況，採用fragment free模式來彌補Cut-Through的缺點。
   在fragment free模式下，長度小於64位元組的frame會被丟棄，並减少資料傳輸中的後期衝突。
* The store-and-forward switching method drops frames that do not pass the FCS check.
* the cut-through switching method may forward invalid frames because no FCS check is performed.
* has the ability to perform rapid frame switching. (the switch can make a forwarding decision as soon as it has looked up the destination MAC address of the frame in its MAC address table)
* The switch does not have to wait for the rest of the frame to enter the ingress port before making its forwarding decision.
	![[Pasted image 20230325165705.png]]
![[Pasted image 20230325172313.png]]


## Collision and Broadcast Domains
### Collision Domains
* The network segments that **share the same bandwidth** between devices are known as collision domains.
* There are no collisions when switch ports are operating in full-duplex.
* there could be a collision domain if a switch port is operating in half-duplex.
![[Pasted image 20230325211657.png]]
### Broadcast Domains
* Only a network layer device, such as a router, can divide a Layer 2 broadcast domain.
* Routers are used to segment broadcast domains, but will also segment a collision domain.
* The Layer 2 broadcast domain is referred to as the MAC broadcast domain. Consists of all devices on the LAN that receive broadcast frames from a host.
* Each device connected to the switch receives a **copy** of the broadcast frame and processes it.
* necessary for initially locating other devices and network services.
* reduce network efficiency.
* Network bandwidth is used to propagate the broadcast traffic.
### Alleviate Network Congestion
* LAN switches have special characteristics that help them alleviate network congestion.
* Full-duplex connections have dramatically increased LAN network performance.
* Switches interconnect LAN segments, use a MAC address table to determine egress ports, and can lessen or eliminate collisions entirely.
* Characteristics of switches that alleviate network congestion include the following:
	* ==**Fast port speeds**== - Ethernet switch port speeds vary by model and purpose. For instance, most access layer switches support 100 Mbps and 1 Gbps port speeds. Distribution layer switches support 100 Mbps, 1 Gbps, and 10 Gbps port speeds and core layer and data center switches may support 100 Gbps, 40 Gbps, and 10 Gbps port speeds. Switches with faster port speeds cost more but can reduce congestion.
	- ==**Fast internal switching**== - Switches use a **fast internal bus** or **shared memory** to provide high performance.
	- ==**Large frame buffers**== - Switches use large memory buffers to temporarily store more received frames before having to start dropping them. This enables ingress traffic from a faster port (e.g., 1 Gbps) to be forwarded to a slower (e.g., 100 Mbps) egress port **without losing frames**.
	- ==**High port density**== - A high port density switch lowers overall costs because it reduces the number of switches required. For instance, if 96 access ports were required, it would be less expensive to buy two 48-port switches instead of four 24-port switches. High port density switches also help keep traffic local, which helps alleviate congestion.

## Overview of VLANs
### VLAN Definitions
* ==**Virtual LANs (VLANs)**== provide segmentation and organizational flexibility in a switched network.
* VLANs are based on logical connections, instead of physical connections.
![[Pasted image 20230326011815.png]]
* Packets destined for devices that do not belong to the VLAN must be forwarded through a device that supports routing.
* Each VLAN is considered a separate logical network.
* Any switch port can belong to a VLAN.
* Multiple IP subnets can exist on a switched network, without the use of multiple VLANs.
* VLANs improve network performance by separating large broadcast domains into smaller ones.
* If a device in one VLAN sends a broadcast Ethernet frame, all devices in the VLAN receive the frame, but devices in other VLANs do not.
* Each switch port can be assigned to only one VLAN.
### Benefits of a VLAN Design
* Each VLAN in a switched network corresponds to an IP network.
* VLAN design must take into consideration the implementation of a hierarchical(分層的) network-addressing scheme.
* Blocks of contiguous network addresses are reserved for and configured on devices in a specific area of the network.
	![[Pasted image 20230326101225.png]]
* The table lists the benefits of designing a network with VLANs:
	![[Pasted image 20230326101749.png]]
### Types of VLANs
1. ==**Default VLAN**==
	* The default VLAN on a Cisco switch is VLAN 1.
	* By default, all Layer 2 control traffic is associated with VLAN 1.
	* Important facts to remember about VLAN 1 include the following:
		*  All ports are assigned to VLAN 1 by default.
		-  The native VLAN is VLAN 1 by default.
		-  The management VLAN is VLAN 1 by default.
		-  VLAN 1 cannot be renamed or deleted.
		![[Pasted image 20230326103231.png]]
2. ==**Data VLAN**==
	* to separate user-generated traffic.
	* Note that voice and network management traffic should not be permitted on data VLANs.
3. ==**Native VLAN**==
	* User traffic from a VLAN must be tagged with its **VLAN ID** when it is sent to another switch.
	* **Trunk** ports are used between switches to support the transmission of tagged traffic.
	* A switch may also have to send untagged traffic across a trunk link. Untagged traffic is generated by a switch and may also come from legacy devices. The 802.1Q trunk port places untagged traffic on the native VLAN. The native VLAN on a Cisco switch is VLAN 1 (i.e., default VLAN).
	* as an unused VLAN, distinct from VLAN 1 and other VLANs.
4. ==**Management VLAN**==
	* a data VLAN configured specifically for **network management traffic** including SSH, Telnet, HTTPS, HTTP, and SNMP.
	* By default, VLAN 1 is configured as the management VLAN on a Layer 2 switch.
5. ==**Voice VLAN**==
	* A separate VLAN is needed to support Voice over IP (VoIP). VoIP traffic requires the following:
		- Assured bandwidth to ensure voice quality
		- Transmission priority over other types of network traffic
		- Ability to be routed around congested areas on the network
		- Delay of less than 150 ms across the network
		![[Pasted image 20230326104556.png]]

## VLANs in a Multi-Switched Environment
### Defining VLAN Trunks
* VLAN trunks allow all VLAN traffic to propagate(傳播) between switches.
* This enables devices connected to different switches but in the same VLAN to communicate without going through a router.
* A trunk is a **point-to-point link** between two network devices that carries more than one VLAN.
* A VLAN trunk extends VLANs across an entire network.
* A VLAN trunk does not belong to a specific VLAN.
* it is a conduit(管道) for multiple VLANs between switches and routers.
* A trunk could also be used between a network device and server or another device that is equipped with an appropriate 802.1Q-capable NIC.
* By default, on a Cisco Catalyst switch, **all VLANs** are supported on a trunk port.
* This network could not function without VLAN trunks. (yellow line)
	![[Pasted image 20230326110112.png]]
### Network with VLANs
*  A VLAN is the equivalent(相等的) to an IP network (or subnet).
* VLANs are configured on the switch, whereas IP addressing is configured on the device.
![[Pasted image 20230326111426.png]]
### VLAN Identification with a Tag
* The standard Ethernet frame header does not contain information about the VLAN to which the frame belongs.
* ==**Tagging**== :  accomplished(完成) by using the IEEE 802.1Q header, specified in the IEEE 802.1Q standard. The 802.1Q header includes a 4-byte tag inserted within the original Ethernet frame header, specifying the VLAN to which the frame belongs.
* When the switch receives a frame on a port configured in access mode and assigned a VLAN, the switch:
	1. inserts a VLAN tag in the frame header
	2. recalculates the Frame Check Sequence (FCS)
	3. sends the tagged frame out of a trunk port.
* **VLAN Tag Field Details**
	![[Pasted image 20230326114612.png]]
	* **Type** - A 2-byte value called the tag protocol ID (TPID) value. For Ethernet, it is set to hexadecimal 0x8100.
	-   **User priority** - A 3-bit value that supports level or service implementation.
	-   **Canonical Format Identifier (CFI)** - A 1-bit identifier that enables Token Ring frames to be carried across Ethernet links.
	-   **VLAN ID (VID)** - A 12-bit VLAN identification number that supports up to 4096 VLAN IDs.
* After the switch inserts the tag control information fields, it recalculates the FCS(frame check sequence) values and inserts the new FCS into the frame.
### Native VLANs and 802.1Q Tagging
* The IEEE 802.1Q standard specifies a native VLAN for trunk links, which defaults to VLAN 1.
* Management frames that are sent between switches is an example of traffic that is typically untagged.
* If the link between two switches is a trunk, the switch sends the **untagged** traffic on the **native VLAN**.
* **Tagged Frames on the Native VLAN**
	* Some devices that support trunking add a VLAN tag to native VLAN traffic.
	* **Control traffic** sent on the native VLAN should not be tagged.
	* If an 802.1Q trunk port receives a tagged frame with the VLAN ID that is the same as the native VLAN, it drops the frame.
* **Untagged Frames on the Native VLAN**
	* When a Cisco switch trunk port receives untagged frames (which are unusual in a well-designed network), it forwards those frames to the native VLAN.
	* If there are no devices associated with the native VLAN (which is not unusual) and there are no other trunk ports (which is not unusual), then the frame is dropped.
	* The default native VLAN is VLAN 1.
	* When configuring an 802.1Q trunk port, a default Port VLAN ID (PVID) is assigned the value of the native VLAN ID.
	* All untagged traffic coming in or out of the 802.1Q port is forwarded based on the PVID value.
	* If the native VLAN has not been reconfigured, the PVID value is set to VLAN 1.
		![[Pasted image 20230326120734.png]]
		Tagged traffic on the trunk received by PC1 is dropped. This scenario reflects poor network design for several reasons:
					- it uses a hub.
					- it has a host connected to a trunk link.
					- >>and it implies that the switches have access ports assigned to the native VLAN.
### Voice VLAN Tagging
* This enables quality of service (QoS) and security policies to be applied to voice traffic.
* A Cisco IP phone connects directly to a switch port. 
* An IP host can connect to the IP phone to gain network connectivity as well. 
* The access port connected to the Cisco IP phone can be configured to use two separate VLANs. 
	* One VLAN is for voice traffic
	* and the other is a data VLAN to support the host traffic.
* The link between the switch and the IP phone simulates a trunk link to carry both voice VLAN traffic and data VLAN traffic.
* Specifically, the Cisco IP Phone contains an integrated three-port 10/100 switch. The ports provide dedicated connections to the following devices:
	-   Port 1 connects to the switch or other VoIP device.
	-   Port 2 is an internal 10/100 interface that carries the IP phone traffic.
	-   Port 3 (access port) connects to a PC or other device.
* The switch access port sends CDP packets instructing the attached IP phone to send voice traffic in one of three ways. The method used varies based on the type of traffic:
	-   Voice VLAN traffic must be tagged with an appropriate Layer 2 class of service (CoS) priority value
	-   Access VLAN traffic can also be tagged with a Layer 2 CoS priority value
	-   Access VLAN is not tagged (no Layer 2 CoS priority value)
* In the figure, the student computer PC5 is attached to a Cisco IP phone, and the phone is attached to switch S3. VLAN 150 is designed to carry voice traffic, while PC5 is in VLAN 20, which is used for student data.
	![[Pasted image 20230326124154.png]]
## VLAN Configuration
### VLAN Ranges on Catalyst Switches
* ==**Normal Range VLANs**==
	* They are used in all small- and medium-sized business and enterprise networks.
	- They are identified by a VLAN ID between 1 and 1005.
	- IDs 1002 through 1005 are reserved for legacy network technologies (i.e., Token Ring and Fiber Distributed Data Interface).
	- IDs 1 and 1002 to 1005 are automatically created and cannot be removed.
	- Configurations are stored in the switch flash memory in a VLAN database file called vlan.dat.
	- When configured, VLAN trunking protocol (VTP), helps synchronize the VLAN database between switches.
* ==**Extended Range VLANs**==
	* They are used by service providers to service multiple customers and by global enterprises large enough to need extended range VLAN IDs.
	- They are identified by a VLAN ID between 1006 and 4094.
	- Configurations are saved, by default, in the running configuration.
	- They support fewer VLAN features than normal range VLANs.
	- Requires VTP(VLAN Trunking Protocol) transparent mode configuration to support extended range VLANs.
* **Note**: 4096 is the **upper boundary** for the number of VLANs available on Catalyst switches, because there are 12 bits in the VLAN ID field of the IEEE 802.1Q header.
### VLAN Creation Commands
* When configuring normal range VLANs, the configuration details are stored in **flash memory** on the switch in a file called vlan.dat.
	![[Pasted image 20230326143329.png]]
### VLAN Creation Example
* In the topology, the student computer (PC2) has not been associated with a VLAN yet, but it does have an IP address of 172.17.20.22, which belongs to VLAN 20.
	![[Pasted image 20230326143603.png]]
	The example shows how the student VLAN (VLAN 20) is configured on switch S1.
	![[Pasted image 20230326143622.png]]
* **Note**: In addition to entering a single VLAN ID, a series of VLAN IDs can be entered separated by commas, or a range of VLAN IDs separated by hyphens using the **vlan** _vlan-id_ command. For example, entering the **vlan 100,102,105-107** global configuration command would create VLANs 100, 102, 105, 106, and 107.
### VLAN Port Assignment Commands
* After creating a VLAN, the next step is to assign ports to the VLAN.
* Access mode indicates that the port belongs to a single VLAN and will not negotiate to become a trunk link.
* **Note**: Use the **interface range** command to simultaneously configure multiple interfaces.
![[Pasted image 20230326144317.png]]
### VLAN Port Assignment Example
* In the figure, port F0/6 on switch S1 is configured as an access port and assigned to VLAN 20. Any device connected to that port will be associated with VLAN 20. Therefore, in our example, PC2 is in VLAN 20.
	![[Pasted image 20230326144729.png]]
	The example shows the configuration for S1 to assign F0/6 to VLAN 20.
	![[Pasted image 20230326144804.png]]
* VLANs are configured on the **switch port** and not on the end device.
### Data and Voice VLANs
* An access port can belong to ==**only one**== data VLAN at a time.
* A port can also be associated to a voice VLAN.
* For example, a port connected to an IP phone and an end device would be associated with two VLANs: one for voice and one for data.
* ![[Pasted image 20230326145218.png]]
	To implement this configuration, a data VLAN and a voice VLAN are created.
*  Data and Voice VLAN Example
	* Use the **switchport voice vlan** _vlan-id_ interface configuration command to assign a voice VLAN to a port.
	* LANs supporting voice traffic typically also have quality of service (QoS) enabled.
		![[Pasted image 20230326145600.png]]

### Verify VLAN Information
* The ==**show vlan**== command displays a list of all configured VLANs.
* The table describes the **show vlan** command options.
	![[Pasted image 20230326150046.png]]

### Delete VLANs
* The ==**no vlan**== _vlan-id_ global configuration mode command is used to remove a VLAN from the switch vlan.dat file.
* **Caution**: Before deleting a VLAN, reassign all member ports to a different VLAN first. Any ports that are not moved to an active VLAN are unable to communicate with other hosts after the VLAN is deleted and until they are assigned to an active VLAN.
* **Note**: To restore a Catalyst switch to its factory default condition, unplug(拔掉) all cables except the console and power cable from the switch. Then enter the **erase startup-config** privileged EXEC mode command followed by the **delete vlan.dat** command.
## VLAN Trunks
### Trunk Configuration Commands
* To enable trunk links, configure the interconnecting ports with the set of interface configuration commands shown in the table.
	![[Pasted image 20230326153655.png]]
* Trunk Configuration Example:
	![[Pasted image 20230326153820.png]]
	The example shows the configuration of port F0/1 on switch S1 as a trunk port. The native VLAN is changed to VLAN 99 and the allowed VLAN list is restricted to 10, 20, 30, and 99.
	![[Pasted image 20230326153915.png]]
* **Note**: Always configure both ends of a trunk link with the same native VLAN.
### Verify Trunk Configuration
* The configuration is verified with the **show interfaces** _interface-ID_ **switchport** command.
* **Note**: Another useful command for veryfing trunk interfaces is the ==**show interface trunk**== command.
### Reset the Trunk to the Default State
* Use the ==**no switchport trunk allowed vlan**== and the ==**no switchport trunk native vlan**== commands to remove the allowed VLANs and reset the native VLAN of the trunk.
* The example shows the commands used to reset all trunking characteristics of a trunking interface to the default settings.
	![[Pasted image 20230326155016.png]]
	![[Pasted image 20230326155036.png]]
	![[Pasted image 20230326155115.png]]
	-----
	This sample output shows the commands used to remove the trunk feature from the F0/1 switch port on switch S1. The **show interfaces f0/1 switchport** command reveals that the F0/1 interface is now in static access mode.
	-----
	![[Pasted image 20230326155340.png]]

## Dynamic Trunking Protocol
* https://www.jannet.hk/dynamic-trunking-protocol-dtp-zh-hant/
* ==**DTP**==: Some Cisco switches have a proprietary protocol that lets them automatically negotiate trunking with a neighboring device.
* can **speed up** the configuration process for a network administrator.
* Ethernet trunk interfaces(相互聯繫) support different trunking modes.
* An interface can be set to trunking or nontrunking, or to negotiate trunking with the neighbor interface.
* Trunk negotiation is managed by DTP, which operates on a point-to-point basis only, between network devices.
* DTP manages trunk negotiation only if the port on the neighbor switch is configured **in a trunk mode** that supports DTP.
* To enable trunking from a Cisco switch to a device that does not support DTP, use the ==**switchport mode trunk**== and ==**switchport nonegotiate**== interface configuration mode commands.This causes the interface to become a trunk, but it will not generate DTP frames.
	![[Pasted image 20230326160500.png]]
* To re-enable dynamic trunking protocol use the ==**switchport mode dynamic auto**== command.
	![[Pasted image 20230326160548.png]]
* If the ports connecting two switches are configured to ignore all DTP advertisements with the ==**switchport mode trunk**== and the ==**switchport nonegotiate**== commands, the ports will stay in trunk port mode.
* If the connecting ports are set to dynamic auto, they will not negotiate a trunk and will stay in the access mode state, creating an inactive trunk link.
* When configuring a port to be in trunk mode, use the ==**switchport mode trunk**== command.
![[Pasted image 20230326162321.png]]
### Negotiated Interface Modes
* The **switchport mode** command has additional options for negotiating the interface mode. The full command syntax is the following:
	![[Pasted image 20230326162535.png]]
* The options are described in the table.
	![[Pasted image 20230326162612.png]]
* Use the ==**switchport nonegotiate**== interface configuration command to stop DTP negotiation.
### Results of a DTP Configuration
![[Pasted image 20230326163425.png]]
### Verify DTP Mode
* To determine the current DTP mode, issue the **show dtp interface** command as shown in the output.
	![[Pasted image 20230326163935.png]]
* **Note**: A general best practice is to set the interface to **trunk** and **nonegotiate** when a trunk link is required. On links where trunking is not intended, DTP should be turned off.

## Inter-VLAN Routing
### Inter-VLAN Routing
* hosts in one VLAN cannot communicate with hosts in another VLAN unless there is a **router** or a Layer 3 switch to provide routing services.
* Inter-VLAN routing is the process of forwarding network traffic from one VLAN to another VLAN.
* There are three inter-VLAN routing options:
	-   ==**Legacy Inter-VLAN routing**== - This is a legacy solution. It does not scale well.
	-   ==**Router-on-a-Stick**== - This is an acceptable solution for a small to medium-sized network.
	-   ==**Layer 3 switch using switched virtual interfaces (SVIs)**== - This is the most scalable solution for medium to large organizations.
### Legacy Inter-VLAN Routing
* The first inter-VLAN routing solution relied on using a router with multiple Ethernet interfaces.
* Each router interface was connected to a switch port in different VLANs.
* The router interfaces served as the default gateways to the local hosts on the VLAN subnet.
* For example, refer to the topology where R1 has two interfaces connected to switch S1.
	![[Pasted image 20230326183337.png]]
* Notice in the example MAC address table of S1 is populated as follows:
	-   Fa0/1 port is assigned to VLAN 10 and is connected to the R1 G0/0/0 interface.
	-   Fa0/11 port is assigned to VLAN 10 and is connected to PC1.
	-   Fa0/12 port is assigned to VLAN 20 and is connected to the R1 G0/0/1 interface.
	-   Fa0/24 port is assigned to VLAN 20 and is connected to PC2.
* Mac address table for S1:
	![[Pasted image 20230326183907.png]]
	When PC1 sends a packet to PC2 on another network, it forwards it to its default gateway 192.168.10.1. R1 receives the packet on its G0/0/0 interface and examines the destination address of the packet. R1 then routes the packet out its G0/0/1 interface to the F0/12 port in VLAN 20 on S1. Finally, S1 forwards the frame to PC2.
* Legacy inter-VLAN routing using physical interfaces works, but it has a significant limitation.
	*  It is not reasonably scalable because routers have a limited number of physical interfaces.
	* Requiring one physical router interface per VLAN quickly exhausts the physical interface capacity of a router.
* **Note**: This method of inter-VLAN routing is no longer implemented in switched networks.
### Router-on-a-Stick Inter-VLAN Routing
* overcomes the limitation of the legacy inter-VLAN routing method. It ==**only requires one**== physical Ethernet interface to route traffic between multiple VLANs on a network.
* A Cisco IOS router Ethernet interface is configured as an 802.1Q trunk and connected to a trunk port on a Layer 2 switch.
* the router interface is configured using subinterfaces to identify routable VLANs.
	* The configured subinterfaces are software-based virtual interfaces.
	* (subinterfaces) Each is associated with a single physical Ethernet interface.
	* Subinterfaces are configured in software on a router.
	* Each subinterface is independently configured with an IP address and VLAN assignment.
	* Subinterfaces are configured for different subnets that correspond to their VLAN assignment.
	* This facilitates logical routing.
* After a routing decision is made based on the destination IP network address, the router determines the exit interface for the traffic.
* If the exit interface is configured as an 802.Q subinterface, the data frames are VLAN-tagged with the new VLAN and sent back out the physical interface.
#### Router-on-a-Stick Scenario:
![[Pasted image 20230326224406.png]]
To route between VLANs, the R1 GigabitEthernet 0/0/1 interface is logically divided into three subinterfaces, as shown in the table. The table also shows the three VLANs that will be configured on the switches.
![[Pasted image 20230326224442.png]]
Assume that R1, S1, and S2 have initial basic configurations. Currently, PC1 and PC2 cannot **ping** each other because they are on separate networks. Only S1 and S2 can **ping** each other, but they but are unreachable by PC1 or PC2 because they are also on different networks.

To enable devices to ping each other, the switches must be configured with VLANs and trunking, and the router must be configured for inter-VLAN routing.
### Inter-VLAN Routing on a Layer 3 Switch
* The modern method of performing inter-VLAN routing is to use **Layer 3 switches** and **switched virtual interfaces (SVI)**.
* An SVI is a virtual interface that is configured on a Layer 3 switch.
* **Note**: A Layer 3 switch is also called a multilayer switch as it operates at Layer 2 and Layer 3. However, in this course we use the term Layer 3 switch.
![[Pasted image 20230326222950.png]]
* Inter-VLAN SVIs are created the same way that the management VLAN interface is configured.
* The SVI is created for a VLAN that **exists** on the switch.
* The following are advantages of using Layer 3 switches for inter-VLAN routing:
	* much faster than router-on-a-stick because everything is hardware switched and routed.
	* no need for external links from the switch to the router for routing.
	* not limited to one link because Layer 2 EtherChannels can be used as trunk links between the switches to increase bandwidth.
	* Latency is much lower because data does not need to leave the switch in order to be routed to a different network.
	* more commonly deployed in a campus LAN than routers.
* The only disadvantage is that Layer 3 switches are more expensive.

### S1 VLAN and Trunking Configuration
* Complete the following steps to configure S1 with VLANs and trunking:
	* **Step 1**. Create and name the VLANs.
	* ***Step 2**. Create the management interface.
	* ***Step 3**. Configure access ports.
	* ***Step 4**. Configure trunking ports.
		![[Pasted image 20230326225208.png]]

		1. ==**Create and name the VLANs.==
			VLANs are only created after you exit out of VLAN subconfiguration mode.
			![[Pasted image 20230326225322.png]]
		2. ==**Create the management interface.**==
			the management interface is created on VLAN 99 along with the default gateway of R1.
			![[Pasted image 20230326225418.png]]
		3. ==**Configure access ports.**==
			Next, port Fa0/6 connecting to PC1 is configured as an access port in VLAN 10. Assume PC1 has been configured with the correct IP address and default gateway.
			![[Pasted image 20230326225844.png]]
		4. ==**Configure trunking ports.**==
			Finally, ports Fa0/1 connecting to S2 and Fa05 connecting to R1 are configured as trunk ports.
			
