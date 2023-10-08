# Firstpage Design
文字敘述 file:///D:/Wendy/FJU/classes%20information/web/hw1_firstpage/%E7%B6%B2%E9%A0%81%E7%A8%8B%E5%BC%8F%E8%A8%AD%E8%A8%88-%E7%B7%B4%E7%BF%921.html 
影片教學 https://www.youtube.com/watch?v=a6zkxmHtncI
1. **create new project**
	1. 新增專案。
		![[Pasted image 20230924135517.png]]
	2. 選擇要新增的模板。
		![[Pasted image 20230924141602.png]]
	3. 設定新專案名稱及位置。
		![[Pasted image 20230924141916.png]]
	4. 選擇webform檔案並修改進階選項 (取消https)。
		![[Pasted image 20230924142152.png]]
		![[Pasted image 20230924142202.png]] 
 	注意事項:
	 	記得創建時在進階部分取消勾選https選項，讓它不會被chrome擋。

	5. 刪除Default檔案，此為預設網站頁面。
	![[Pasted image 20230924142614.png]]
	6. 重新創建一個default。
		* 在外層檔案先按右鍵。
			![[Pasted image 20230924142837.png]]
		* 加入新的項目。
			![[Pasted image 20230924142909.png]]
		* 點選新增web表單並重新命名。(在此要做首頁頁面，所以取為firstpage)
			![[Pasted image 20230924143106.png]]
	7. 設定網頁背景。
		* 先將想要的圖片下載。
		* 在外層檔案按右鍵。
			![[Pasted image 20230924142837.png]]
		* 選擇加入現有檔案，加入後在現有的方案總管中可以找到圖片。
			![[Pasted image 20230924144036.png]]
		* 將圖片加入到網頁背景中 : 
			* 點選firstpage檔案，找到body的部分。
				![[Pasted image 20230924144603.png]]
			* 找到屬性頁面 (可以直接按F4) ，並在裡面找到style。
				![[Pasted image 20230924145104.png]]
			* 選擇背景並在background-image點選瀏覽加入圖片。
				注意事項:
					此時的背景不會填滿網頁頁面或是隨著視窗縮放做size的更動。
					![[Pasted image 20230924145505.png]]
					(可以點選下面的設計看到目前做的頁面或是調整內容，點選原始擋回到code頁面)
			* 打開屬性中的style，選擇背景，做以下的調整。
				![[Pasted image 20230924145928.png]]
			* 調整背景覆蓋到整個網頁，在屬性code中新增一個size的cover指令。
				![[Pasted image 20230924151348.png]]
	8. 設計登入頁面。(此都在設計頁面做)
		* 在body下打入標題，並調整字體、大小、顏色...。
			![[Pasted image 20230924152217.png]]
		* 上方選擇表格 >> 插入表格 >> 3 x 3 >> 確定。
			![[Pasted image 20230924152411.png]]
		* 將表格選起，點選上方格式 >> 選擇設定位置 >> 相對。 (讓裡面的物件可以隨著視窗縮放改變相對位置)
			![[Pasted image 20230924155154.png]]
		* 在工具箱終將需要的選項拉到想要的位置。
			![[Pasted image 20230924152926.png]]
			* 工具箱可以從上方的 "**檢視**"中新增。
			* 文字部分使用label。
			* 能夠打字的格子使用textbox。
			* 按鍵使用button。
			* 連結字使用linkbutton。
			![[Pasted image 20230924152958.png]]
			可以再調整他們的位置，如:置中、顏色、大小、拉距離。
	9. 修改物件屬性。
		* 點選要修改的物件。(在此選擇label字串)
			![[Pasted image 20230924153247.png]]
		* 更改其text和id。
			Text :
			![[Pasted image 20230924153340.png]]
			ID : (養成習慣要改ID，類似物件名稱)
			![[Pasted image 20230924153419.png]]
			在物件上顯示出的資訊 :
			![[Pasted image 20230924153450.png]]
	成果 :
		![[Pasted image 20230924155738.png]]