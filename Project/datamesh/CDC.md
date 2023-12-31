* 簡介:
當在一個系統中的資料庫中儲存資料時，資料庫可能會隨時間改變，這可能是因為使用者更新了資料、新增了新的資料或者刪除了某些資料。 Change Data Capture (CDC) 是一種軟體設計模式，它監視這些變化，並在資料庫中的資料發生更改時自動偵測這些變化，並捕捉並保存這些變化的詳細資訊。這些變化的資訊可以幫助您的應用程式維護最新的資料，而無需為了得到最新資料而進行複雜的資料庫查詢。CDC通常用於分散式系統，其中多個應用程式需要存取相同的資料庫。
CDC 的原文是 Change Data Capture，常被稱為「異動資料擷取」，在資料庫的領域裡，它是一組軟體設計模式，目的是在資料庫發生變更異動時，能夠時序式地記錄追蹤狀態和變動內容，然後達到資料同步的效果，甚至再應用到資料轉移、資料庫備份、災難復原的場合。

特別是在資料倉儲的環境裡，企業在數據整合的維運過程，針對異質資料來源，進行資料狀態的記錄和辨識，依照時序追蹤資料異動，引導後續的資料梳理和應用，這些正是資訊部門的日常核心作業。以金融或製造業為例，日常作業流程必須要不斷昇級優化，同時間內，必須對既有核心系統效減少衝擊，這樣才能滿足數位轉型下，大數據營運和商務分析的需求挑戰。

資料同步是我們想要的結果，但實作方法和工具卻不只一種，資訊部門需要考量多種面向的需求，像是資料庫功能的支援狀況、對現有資料庫壓力衝擊的耐受度、同步的即時性要求，依據這些限制條件，再決定出最適合自己的技術方案和佈署路徑。現在有越來越多資料庫支援進階的 CDC 功能，促使大家重新思考：是否有機會導入更好的資料同步方案和工具？

* 和資料庫的結合:
要使用CDC，您需要使用支援CDC的資料庫或軟體。大多數主要的關聯式資料庫管理系統都提供了內建的CDC功能，例如Oracle、Microsoft SQL Server、PostgreSQL和MySQL。此外，也有一些第三方CDC工具，例如Debezium和Maxwell等，它們可以與不同的資料庫系統搭配使用。

在啟用CDC之後，資料庫將開始監聽更改，並將更改的詳細資訊儲存在稱為日誌或記錄的特殊資料庫中。CDC工具可以定期檢查這些日誌，捕捉最新的更改並將其轉換為易於處理的格式，例如JSON或AVRO。這些更改的資訊可以傳遞到其他系統，例如分析系統、資料倉儲或其他應用程式，以實時更新它們的資料。

* 有支援CDC的資料庫:
	現在，大多數主要的關聯式資料庫管理系統都支援CDC功能，以下是一些主要的資料庫系統和它們支援的CDC技術：

	1.  Oracle：Oracle資料庫支援使用LogMiner進行CDC。
	2.  Microsoft SQL Server：Microsoft SQL Server支援使用Change Data Capture (CDC)進行CDC。
	3.  MySQL：MySQL支援使用MySQL Binary Log進行CDC。
	4.  PostgreSQL：PostgreSQL支援使用Logical Replication進行CDC。
	5.  MongoDB：MongoDB支援使用MongoDB Connector for Apache Kafka進行CDC。

	此外，還有一些第三方CDC工具，如Debezium和Maxwell等，它們可以與多種資料庫系統搭配使用，包括MySQL、PostgreSQL、MongoDB、Oracle和SQL Server等。