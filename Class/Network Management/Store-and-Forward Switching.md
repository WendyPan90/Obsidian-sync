## Store-and-Forward Switching
* 交換器會先把Frame完全接收下來，然後才進行轉發。LAN交換器會把每個完整的Frame儲存到switch的記憶體緩衝區中，並且在轉發之前檢查錯誤。
   迴圈冗餘校驗(Cyclic redundancy check，簡稱”CRC”)，是一種資傳輸檢錯功能，透過數學公式來校驗接收到的Frame。
   通過CRC檢查後，Frame才會被轉發到目的端MAC位址；如果檢查失敗，損壞的Frame就會被丟棄。此過程能夠確保高品質的資料傳輸，因為接收端不會受到損壞Frame的影響。
* following two primary characteristics:
	* ==**Error checking**== - After receiving the entire frame on the ingress port, the switch compares the frame check sequence (FCS) value in the last field of the datagram against its own FCS calculations. The FCS is an error checking process that helps to ensure that the frame is free of physical and data-link errors. If the frame is error-free, the switch forwards the frame. Otherwise, the frame is dropped.
	- ==**Automatic buffering**== - The ingress port buffering process used by store-and-forward switches provides the flexibility to support any mix of Ethernet speeds. For example, handling an incoming frame traveling into a 100 Mbps Ethernet port that must be sent out a 1 Gbps interface would require using the store-and-forward method. With any mismatch in speeds between the ingress and egress ports, the switch stores the entire frame in a buffer, computes the FCS check, forwards it to the egress port buffer and then sends it.
	![[Pasted image 20231002180859.png]]