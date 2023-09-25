### 架設linux環境
https://github.com/DamionGans/ubuntu-wsl2-systemd-script\

### 導入jdbc驅動程式

導入 JDBC 驅動程式是將 JDBC 驅動 JAR 文件添加到你的 Java 項目中的過程。這樣你的項目才能夠使用這個驅動程式來連接到指定的數據庫。以下是一個一般的步驟來導入 JDBC 驅動程式：
1. **下載 JDBC 驅動程式 JAR 文件**：
    - 首先，你需要從 MySQL 官方網站或其他可信的來源下載適用於你的 MySQL 版本的 JDBC 驅動程式 JAR 文件。這個 JAR 文件通常具有類似 `mysql-connector-java-x.x.x.jar` 的名稱。
2. **導入 JAR 文件到你的項目**：
    - 打開你的 Java 項目，找到你的項目目錄中的「lib」或「依賴庫」目錄。如果這個目錄不存在，你可以手動創建它。
    - 複製下載的 JDBC 驅動程式 JAR 文件到這個目錄中。
3. **設置 Build Path（構建路徑）**：
    - 打開你的 Java 項目，選擇你的 IDE 中的「Build Path」或「構建路徑」選項。
    - 將下載的 JDBC 驅動程式 JAR 文件添加到你的項目的構建路徑中。這可能涉及到將 JAR 文件拖放到 IDE 界面中的「構建路徑」區域，或通過選擇「新增外部 JARs」選項來添加。
4. **確認導入成功**：
    - 確保 JAR 文件已經被成功導入到你的項目中。你應該能夠在 IDE 的構建路徑中看到這個 JAR 文件的引用。
5. **編寫和執行程式**：
    - 現在，你可以在你的 Java 程式中使用這個 JDBC 驅動程式來建立連接和執行操作。

請注意，每個 IDE 的步驟可能有所不同。以上步驟提供了一個一般的指導，你需要根據你所使用的 IDE 進行相應的操作。同時，確保你的 JDBC 驅動程式版本與你所使用的 MySQL 版本相符。


### JDBC連接MYSQL

1. **下載 MySQL JDBC 驅動程式**： 首先，你需要下載 MySQL 的 JDBC 驅動程式（JAR 文件）。你可以從 MySQL 官方網站下載或使用 Maven 或 Gradle 等來管理依賴項。
2. **導入 JDBC 驅動程式**： 在你的 Java 項目中，將下載的 JDBC 驅動程式（JAR 文件）添加到你的項目中。這通常涉及將 JAR 文件放入你的項目的 lib 或依賴庫目錄中。
3. **編寫 Java 代碼**:    編寫 Java 代碼來建立與 MySQL 數據庫的連接，執行 SQL 查詢和操作。以下是一個簡單的示例：(檔案位置:D:\Wendy\\FJU\\Project\\)
	import java.sql.*;

	public class JDBCDemo {

	    public static void main(String[] args) {
	        String jdbcUrl = "jdbc:mysql://localhost:3306/your-database";
	        String username = "your-username";
	        String password = "your-password";

	        try (Connection connection = DriverManager.getConnection(jdbcUrl, username, password);
		    Statement statement = connection.createStatement()) {

	        // 執行 SQL 查詢
	        String selectQuery = "SELECT * FROM your_table";
	        ResultSet resultSet = statement.executeQuery(selectQuery);
	        while (resultSet.next()) {
	            String column1Value = resultSet.getString("column1");
	            String column2Value = resultSet.getString("column2");
	            System.out.println("Column 1: " + column1Value + ", Column 2: " + column2Value);
	        }

	        // 執行 SQL 更新
	        String updateQuery = "UPDATE your_table SET column1 = 'new value' WHERE column2 = 'value'";
	        int rowsUpdated = statement.executeUpdate(updateQuery);
	        System.out.println("Rows updated: " + rowsUpdated);

	        } catch (SQLException e) {
	            e.printStackTrace();
	        }
	    }
	}

在這個示例中，你需要將 `jdbcUrl`、`username` 和 `password` 替換為你的 MySQL 數據庫的相關信息。然後你可以使用 `Connection` 和 `Statement` 來建立連接並執行 SQL 查詢和更新。
請注意，這只是一個簡單的示例，實際應用可能需要更多的錯誤處理和設計。同時，確保在使用 JDBC 過程中遵循最佳實踐，比如使用 PreparedStatement 來預防 SQL 注入等。


### setup connection資料

(使用MYSQL workbench)
在 MySQL Workbench 中，「設定連線」是用來建立到 MySQL 資料庫的連接的一個步驟。以下是你需要提供的一些資訊來填寫「設定連線」的表單：
1. **Connection Name（連線名稱）**：這是你為這個連線設定的名稱，可以自行取一個方便識別的名稱。
2. **Connection Method（連線方式）**：這通常可以選擇「Standard TCP/IP over SSH」（標準 TCP/IP 透過 SSH）或「Standard TCP/IP」（標準 TCP/IP）。
    - 如果選擇「Standard TCP/IP over SSH」，你需要提供 SSH 連線的相關資訊，如 SSH 主機、SSH 用戶名、SSH 私鑰等。
    - 如果選擇「Standard TCP/IP」，你只需要提供 MySQL 伺服器的主機名和端口。
3. **Hostname（主機名）**：這是 MySQL 伺服器的主機名或 IP 地址。
4. **Port（埠號）**：MySQL 伺服器的埠號，通常是 3306。
5. **Username（用戶名）**：用於連接到 MySQL 資料庫的用戶名。
6. **Password（密碼）**：與上述用戶名相對應的密碼。
7. **Default Schema（預設資料庫）**：你希望連接到的預設資料庫名稱。如果你不確定，可以保留空白。
8. **SSH Hostname（SSH 主機名）**：僅在使用 SSH 連線時需要填寫，這是用於 SSH 連線的主機名或 IP 地址。
9. **SSH Username（SSH 用戶名）**：僅在使用 SSH 連線時需要填寫，這是用於 SSH 連線的用戶名。
10. **SSH Key File（SSH 私鑰文件）**：僅在使用 SSH 連線時需要填寫，這是用於 SSH 身份驗證的私鑰文件路徑。
    

根據你的 MySQL 資料庫的設定，填寫上述資訊並確保它們正確無誤。然後，你可以點擊「測試連線」來確認是否能夠成功連接到 MySQL 資料庫。如果測試成功，你可以保存這個連線設定，並在 MySQL Workbench 中使用它來管理和操作資料庫。

### 看資料介面

(使用MYSQL workbench)
1. **安裝和設置 MySQL Workbench**：
    - 下載並安裝 MySQL Workbench 軟體，可以從 MySQL 官方網站或其他可信的來源獲取。
1. **設定伺服器連接**：
    - 打開 MySQL Workbench，點擊「新增連接」，然後輸入資料庫連接相關的信息，如主機名、用戶名、密碼等。
2. **連接資料庫**：
    - 點擊「連接」按鈕，連接到你的 MySQL 資料庫。
4. **瀏覽和管理資料**：
    - 在 MySQL Workbench 中，你可以使用 GUI 界面瀏覽資料庫、查看和編輯表格、執行 SQL 查詢、進行備份和還原等操作。


### 程式編寫

可以在任何你能夠編寫和執行 Java 程式的環境中，撰寫 Kafka Producer、Consumer 以及將數據存儲到 MySQL 的程式。以下是一個簡單的步驟：
1. **安裝 Java 開發環境**： 首先，確保你已經在你的計算機上安裝了 Java 開發環境。你可以下載並安裝 Java Development Kit (JDK)。你可以從 Oracle 官方網站或其他可信的來源下載。
2. **編寫 Java 程式**： 使用你喜歡的集成開發環境（IDE）或純文本編輯器，創建並編寫 Java 程式。你可以在程式中使用 Kafka 的 Java 客戶端庫來創建 Producer 和 Consumer。同時，你也可以使用 JDBC 库來處理 MySQL 連接和操作。
3. **編譯和執行程式**： 使用 Java 編譯器（`javac`）將你的程式編譯成字節碼。然後，使用 Java 虛擬機（`java`）來執行你的程式。你需要在終端中運行以下命令：
    
    javac YourProgram.java
    java YourProgram
    
    這將編譯並執行你的 Java 程式。
    

以下是一個簡單的範例，展示如何使用 Kafka Producer、Consumer，以及將數據存儲到 MySQL。請注意，這只是一個基本的示例，實際應用可能需要更多的配置和錯誤處理。

`import org.apache.kafka.clients.producer.*;`
`import org.apache.kafka.clients.consumer.*;`
`import java.util.*;`
`import java.sql.*;`

`public class KafkaDemo {

	public static void main(String[] args) {
	         // Kafka Producer
	        Properties producerProps = new Properties();
	        producerProps.put("bootstrap.servers", "localhost:9092");         
	        producerProps.put("key.serializer","org.apache.kafka.common.serialization.StringSerializer");
	        producerProps.put("value.serializer","org.apache.kafka.common.serialization.StringSerializer");
	        
	        KafkaProducer<String, String> producer = new KafkaProducer<>(producerProps);
	        ProducerRecord<String, String> record = new ProducerRecord<>("topic-name", "key", "value");
	        producer.send(record);
	        producer.close();
	        
	        // Kafka Consumer
	        Properties consumerProps = new Properties();         
	        consumerProps.put("bootstrap.servers", "localhost:9092");         
	        consumerProps.put("key.deserializer","org.apache.kafka.common.serialization.StringDeserializer");
	        consumerProps.put("value.deserializer", "org.apache.kafka.common.serialization.StringDeserializer");
	        consumerProps.put("group.id", "test-group");
	        
	        KafkaConsumer<String, String> consumer = new KafkaConsumer<>(consumerProps);
	        consumer.subscribe(Collections.singletonList("topic-name"));
	        ConsumerRecords<String, String> records = consumer.poll(Duration.ofMillis(100));
	        for (ConsumerRecord<String, String> record : records) {
		        System.out.println("Key: " + record.key() + ", Value: " + record.value());
		    }
		    consumer.close();
		
		    // MySQL JDBC
		    String jdbcUrl = "jdbc:mysql://localhost:3306/your-database";
		    String username = "your-username";
		    String password = "your-password";
		    try (Connection connection = DriverManager.getConnection(jdbcUrl, username, password);
			    Statement statement = connection.createStatement()) {
			    String insertQuery = "INSERT INTO your_table (column1, column2) VALUES ('value1', 'value2')";
			    statement.executeUpdate(insertQuery);
			} catch (SQLException e) {
				e.printStackTrace();
			}
	}
}

在這個示例中，你需要將 Kafka 主題名稱、MySQL 資料庫名稱、用戶名和密碼以及其他相關信息替換為你的實際配置。同時，你也需要確保你的 Java 環境中已經添加了相關的 Kafka 和 JDBC 庫。
請注意，這只是一個簡單的示例，實際情況可能更加複雜。你可能需要添加更多的配置、錯誤處理和併發處理，以達到你的需求。

### 確認 kafka & mysql 連線

確認 MySQL 是否已經和 Kafka 建立連線的過程可能稍微複雜，因為這涉及到不同系統的互動。基本上，你需要確保你已經實施了以下步驟：
1. **Kafka 生產者（Producer）將數據寫入 Kafka 主題（Topic）**：
    - 確保你已經寫了一個 Kafka 生產者程式，將數據發送到指定的 Kafka 主題。這個主題通常對應到你想要從中讀取數據的 MySQL 表格。
2. **Kafka 消費者（Consumer）從 Kafka 主題讀取數據**：
    - 在你的 Kafka 消費者程式中，確保你已經設置了對應的 Kafka 主題來讀取數據。這個主題對應到你之前設定的 Kafka 生產者將數據寫入的主題。
3. **數據處理與儲存**：
    - 在 Kafka 消費者程式中，將從 Kafka 主題讀取的數據進行處理，並將其儲存到 MySQL 資料庫中。你的消費者程式需要使用 JDBC 來建立與 MySQL 的連接，並執行 SQL 操作。
4. **確認 MySQL 資料表有被更新**：
    - 當你的 Kafka 消費者程式運行時，它應該會將數據寫入到 MySQL 資料庫中的指定資料表。你可以使用 MySQL 客戶端工具（如 MySQL Workbench 或命令列工具）來檢查這個資料表，確保數據已經被正確地寫入。
5. **確認數據正確性**：
    - 確保在數據從 Kafka 主題傳送到 MySQL 資料表的過程中，數據的正確性得到保證。這可能涉及到對數據進行驗證、處理錯誤等。

以上是基本的步驟，以確保 Kafka 和 MySQL 之間的連線。要確保整個過程運行正常，你需要仔細檢查每個步驟，進行測試並進行錯誤處理。同時，建議在每個關鍵步驟加入適當的日誌記錄，以便在需要時進行故障排除。




1. 重新安裝mysql所有東西 (server+Connector+Mysql workbench)
	1. mysql password: userpass!@12
	2. mysql user: root
	3. windows service name: MySQL80
	4. ![[Pasted image 20230823160833.png]]
2. 更改基本設定(0.0.0.0 & grep)
3. 建立database (可以的話，有個內容或是先有個範例)
4. 和kafka連線 (可以問是要甚麼kafka帳號嗎or連線)
5. 確認有連線成功


## ubuntu linux
https://linuxhint.com/installing_mysql_workbench_ubuntu/
https://zhima-mochi.medium.com/%E5%9C%A8-linux-ubuntu-%E5%AE%89%E8%A3%9D-mysql-%E4%B8%A6%E9%80%8F%E9%81%8E-java-%E9%80%A3%E6%8E%A5-513d566db878

![[Pasted image 20230823233416.png]]


## Kafka
https://www.omniwaresoft.com.tw/techcolumn/kafka-techcolumn/using-kafka-for-cdc-with-mongodb/