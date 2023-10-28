## Network Access Layer Issues
* The output from the **show interfaces** command is useful for detecting common media issues. For example: 
	![[Pasted image 20231002174339.png]]
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
	