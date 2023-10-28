## Interface Verification Commands
* The following commands are especially useful to quickly identify the status of an interface:
	-   ==**show ip interface brief**== and ==**show ipv6 interface brief**== - These display a summary for all interfaces including the IPv4 or IPv6 address of the interface and current operational status.
	-   ==**show running-config interface**== _interface-id_ - This displays the commands applied to the specified interface.
	-   ==**show ip route**== and ==**show ipv6 route**== - These display the contents of the IPv4 or IPv6 routing table stored in RAM. In Cisco IOS 15, active interfaces should appear in the routing table with two related entries identified by the code ‘**C**’ (Connected) or ‘**L**’ (Local). In previous IOS versions, only a single entry with the code ‘**C**’ will appear.
* The following two commands are used to gather more detailed interface information:
	-   ==**show interfaces**==- Displays interface information and packet flow count for all interfaces on the device.
	-   ==**show ip interface**== and ==**show ipv6 interface**== - Displays the IPv4 and IPv6 related information for all interfaces on a router.