# Browsing page
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
		* 插入表格。(2*3)
			