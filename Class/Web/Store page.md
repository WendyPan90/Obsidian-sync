# Browsing store page
文字敘述 
影片教學 https://www.youtube.com/watch?v=RhISPOmlD2w

## 目標
進入商店連結之後，可以在左上角看到使用者的"名字"和"餘額"，並有一"下拉式"清單可以供使用者挑選商品，點選商品之後可以看到"商品展示圖"、"價錢"及"庫存"。

## 步驟
1. 新增新的頁面。
	1. 在最外層檔案加入新的**web表單**。
		![[Pasted image 20231012193937.png]]
		![[Pasted image 20231012193949.png]]
		選擇web表單之後，重新命名。
		![[Pasted image 20231012194111.png]]
2. 將"**進入商店link**"連結到該頁面。
	1. 將"進入商店link"屬性中的"**postbackUrl**"設定成新開的表單。
		* 屬性。
			![[Pasted image 20231012194406.png]]
		* 選擇檔案後確定。
			![[Pasted image 20231012194443.png]]
		* 結果
			![[Pasted image 20231012194514.png]]
3. 對商店頁面做設定。
	1. 選擇商店內容呈現的檔案(store)，並在設計頁面做基本設定。(如firstpage)
		* 插入背景
		* 跳整背影大小
		* 設標題
		* 在body中新增background size
	2. 顯示使用者"**名稱**"及"**餘額**"。
		* 插入表格。(放在表格比較好管理，表格數量可以之後再做插入或刪除)
			![[Pasted image 20231012195729.png]]
		* 在 工具箱 >> 標準 >> Label，拉入表格並改名稱(ID)。
			![[Pasted image 20231012200432.png]]
			![[Pasted image 20231012200445.png]]
			![[Pasted image 20231012200340.png]]
		* 到store的cs檔案(要將其展開)。
			![[Pasted image 20231012200554.png]]
		* 在載入頁面後顯示使用者資料。(透過之前設定的"工作階段狀態"做)
			輸入code
			![[Pasted image 20231012201035.png]]
		* 回到"**伺服器總館**"內，顯示資料表資料。
			![[Pasted image 20231012201423.png]]
		* 輸入money值。
			![[Pasted image 20231012201515.png]]
	3. 插入提供商品展示的"**下拉式清單**"。
		* 在 工具箱 >> 標準 >> **DropDownList**，再拉入2個Label分別顯示"**價格**"，"**庫存**"，最後再拉一個"**image**"做商品展示圖。
			下拉式清單:
			![[Pasted image 20231012202832.png]]
			圖片:
			![[Pasted image 20231012202950.png]]
		* 將各自項目做命名。
			* 下拉式選單: DrinkList (ID)
			* 價格Label: DrinkPriceLB (ID) / X 元 (Text)
			* 庫存Label: DrinkQtLB (ID) / 庫存 : X 個 (Text)
			* 圖片: DrinkImage (ID)
4. 建立新的商品資料表。
	1. 到伺服器總管的資料表中新增資料表。
		![[Pasted image 20231012204105.png]]
	2. 在table中新增項目。
		* 先將id的主索引移除。
			![[Pasted image 20231012204406.png]]\
		* 新增項目。
			![[Pasted image 20231012204600.png]]
		* 更改table名稱。
			![[Pasted image 20231012204635.png]]
		* 設定drink_id的屬性，將"**識別規格**"設定為true，"**識別值種子**"為0。(在table點drink_id就可以設定屬性)
			![[Pasted image 20231012204849.png]]
			種子的用意是最初始的id值，隨著量增加跟著識別值增量(+1)增加。
		* 更新 >> 更新資料庫。
	3. 設定資料表資料內容。
		* 在剛剛創建的table做"顯示資料表內容"。
			![[Pasted image 20231012205209.png]]
		* 新增項目。
			![[Pasted image 20231012205436.png]]
	4. 回到default (firstpage)設計頁面，在工作欄的"資料"中插入2個"**查詢器(SqlDataSource)**"和1個"**DetailsView**"。
		1. SqlDataSource:
			命名: DrinkData (ID) >> 提供下拉式清單選項
			命名: DrinkDataSelect (ID) >> 
			![[Pasted image 20231012205724.png]]
		2. DetailsView:
			命名: DrinkDetailsView (ID)
			![[Pasted image 20231012205809.png]]
		3. 設定查詢器 (DrinkData):
			* 設定資料來源:
				![[Pasted image 20231012210256.png]]
				選擇所使用的database
				![[Pasted image 20231012210414.png]]
			* 選擇設定輸出的項目。
				![[Pasted image 20231012210504.png]]
			* 下一步 >> 完成。
		4. 設定下拉式清單:
			* 選擇資料來源。
				![[Pasted image 20231012210647.png]]
			* 選擇剛剛設定的DrinkData。(要改一下顯示的資料ㄌㄢ)
				![[Pasted image 20231012210756.png]]
			* 