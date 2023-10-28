## Cut-Through Switching
* 交換器接收到Frame時，會先抓取目的端MAC位址(也就是接在preamble後面的前6個bytes)。然後，LAN交換器會在它的交換表(switch table)中檢查目的MAC位址，並確定輸出介面埠，再將Frame轉發到目標位址。
   過程中不會執行CRC錯誤檢查。因此，所有的Frame(不論有無錯誤)都會被轉發到接收端交換器。由接收端進行錯誤檢查，以確保傳輸無差錯。
   為了改善這種情況，採用fragment free模式來彌補Cut-Through的缺點。
   在fragment free模式下，長度小於64位元組的frame會被丟棄，並减少資料傳輸中的後期衝突。
* The store-and-forward switching method drops frames that do not pass the FCS check.
* the cut-through switching method may forward invalid frames because no FCS check is performed.
* has the ability to perform rapid frame switching. (the switch can make a forwarding decision as soon as it has looked up the destination MAC address of the frame in its MAC address table)
* The switch does not have to wait for the rest of the frame to enter the ingress port before making its forwarding decision.
	![[Pasted image 20231002181402.png]]
	![[Pasted image 20231002181416.png]]