### Collision Domains
* The network segments that **share the same bandwidth** between devices are known as collision domains.
* There are no collisions when switch ports are operating in full-duplex.
* there could be a collision domain if a switch port is operating in half-duplex.
![[Pasted image 20231002182726.png]]
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