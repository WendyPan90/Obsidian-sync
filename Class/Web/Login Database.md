# Login 頁面連接資料庫

文字敘述 file:///D:/Wendy/FJU/classes%20information/web/%E7%B6%B2%E9%A0%81%E7%A8%8B%E5%BC%8F%E8%A8%AD%E8%A8%88-%E7%B7%B4%E7%BF%922(%E7%99%BB%E5%85%A5%E7%B3%BB%E7%B5%B1).html
影片教學 https://www.youtube.com/watch?v=Zcv3MJ5OOzs

## 目標

連上後端資料庫，若輸錯帳密會顯示訊息"帳號密碼錯誤"，若輸入正確帳密，則在登入鍵按下後旁邊會出現進入商店的連結。

## 步驟

1. 建立資料庫
	1. 在App Data檔案按右鍵，選擇加入"新增項目"。
		![[Pasted image 20231006170247.png]]
		![[Pasted image 20231006170257.png]]
	2. 選擇C#中的資料，點選SQL Server資料庫，並將它重新命名後新增。
		![[Pasted image 20231006170332.png]]
	3. 新增結束後，對mdf按兩下進入"**伺服器總管**"，並對mdf(剛剛建的database)點兩下連線。
		![[Pasted image 20231006170356.png]]
		![[Pasted image 20231006170408.png]]
	4. 對資料表按右鍵新增新的資料表，會進到一個table。
		![[Pasted image 20231006170424.png]]
		![[Pasted image 20231006170728.png]]
	5.  直接在table內加入要的elements，並選擇相對應的type，最後將id (用不到) 刪除，並在下面指令將table重新命名 (這裡取為userData)。
		![[Pasted image 20231006170745.png]]
		(下面的指令最後會長這樣)![[Pasted image 20231006170756.png]]
	6. 確認好了之後點選左上角的"**更新**">>"**更新資料庫**"。
		![[Pasted image 20231006170812.png]]
		![[Pasted image 20231006170845.png]]
2. 網頁連結資料庫。
	1. 回到default (firstpage) 檔案的設計頁面，在工具箱中把"**DetailsView**" (方便查看資料) 和"**SqlDataSource**" (網頁和資料庫的連結) 放入頁面中。
		![[Pasted image 20231006171346.png]]
	2. 將剛剛拉近設計頁面的元素重新命名(ID)。
	3. **連接資料庫**: 
		* 點選SqlDataSource，右邊會出現一個箭頭，點下去。
			![[Pasted image 20231006171402.png]]
		* 點選"設定資料來源"。
			![[Pasted image 20231006171410.png]]
		* 選擇剛剛建立的資料庫，並按兩次"下一步"。
			![[Pasted image 20231006171423.png]]
			(這裡不用改，直接下一步)![[Pasted image 20231006171433.png]]
		* ==綁定資料庫==(有兩種方法，這裡介紹==第一種==)，選擇"指定資料表或檢視的資料行"，點選要方便看到的資料內容 (會輸出到DetailsView，讓其顯示)。
			![[Pasted image 20231006171443.png]]
		* 點選旁邊的"**WHERE**"作條件篩選。
			![[Pasted image 20231006171452.png]]
		* 設定要判斷的值 (帳號密碼)，像是針對帳號變數，設定參數控制項為設計頁面中的accountTB，設定好就按下加入。
			![[Pasted image 20231006171508.png]]
			帳號密碼都設定好的結果，最後按下確定 >> 下一步。
			![[Pasted image 20231006171525.png]]
		* 點選"**測試查詢**"，看剛剛設定的變數是否正確，或是要再調整的地方，確認好後按下"**完成**"。
			![[Pasted image 20231006171543.png]]
			在此可以看到資料的比對類型。![[Pasted image 20231006171557.png]]
		> 	==第二種綁定資料庫方法==: (以下圖都是截用影片教學中的畫面)
		> 	1. 在此選擇上面的方法。
		> 		![[Pasted image 20231010103540.png]]
		> 	2. 點選"**查詢產生器**"。
		> 		![[Pasted image 20231010103627.png]]
		> 	3. 選擇剛剛建立的資料表，按下加入後關閉視窗(右下關閉)。
		> 		![[Pasted image 20231010103813.png]]
		> 	4. 選擇要設定的項目 (這裡選擇 : name & money & password)。
		> 		![[Pasted image 20231010103938.png]]
		> 	5. 在下面的table終將沒有要顯示的項目 (password) 在"輸出"中取消勾選。
		> 		![[Pasted image 20231010104152.png]]
		> 	6. 在"**篩選**"中填入 "=@" + 該IＤ，此設定好之後按下確定。
		> 		在SQL篩選設定語法中，參數開頭名稱要有@，後面名稱將對應"選擇參數集合"中的物件名。(也就是要和前面的ID名稱相同，這裡只要設定帳號及密碼)
		> 		![[Pasted image 20231010104539.png]]
		> 	7. 按"下一步"。
		> 		![[Pasted image 20231010105943.png]]
		> 	8. 設定參數 (和上面設定accountTB一樣，帳號密碼都要設定)，從屬性中將"**TYPE**"改成"**string**"，都設定好了之後按"下一步"。
		> 		![[Pasted image 20231010110057.png]]
		> 		![[Pasted image 20231010110220.png]]
		> 	9. 點選"測試查詢"。

	4. 回到設計頁面，點選"DetailsView"右邊的箭頭，選擇剛剛設地好的SqlDataSource。
		![[Pasted image 20231006171803.png]]
		![[Pasted image 20231006171817.png]]
		設定好之後顯示出的資料就會是剛剛設定要顯示的資料(name & money)![[Pasted image 20231006171826.png]]
3. 登入功能設定。
	1. "雙擊"登入按鍵，進到code頁面。
		![[Pasted image 20231006171849.png]]
		![[Pasted image 20231006171859.png]]
	2. 可以在登入案件的"屬性"中改事件的名稱。(可以不用改)
		![[Pasted image 20231010111119.png]]
	3. code設定。
		* 在"**載入事件**"中新增code，讓網頁載入時就幫忙做資料綁定。
			![[Pasted image 20231010112650.png]]
		* 按下按鈕時:
			* 希望"進入商店LINK"以及"DetailsView"可以做隱藏。
			* 將TB的內容傳給伺服器，做資料比對。
			*  判斷資料是否有抓到資料，再將link和datasview顯示出來。
			1. 將"DetailsView"和"進入商店link"隱藏。
				![[Pasted image 20231010113941.png]]
			2. 判斷是否有抓到資料，如果有就將"**工作階段狀態**"儲存並將"進入商店link"啟用 ; 若資料抓取有錯誤，則將"工作階段狀態"設為null並將"DetailsView"顯示。
				![[Pasted image 20231010114200.png]]
		* 完整code:
			
			![[Pasted image 20231006172350.png]]
	4. 回到default頁面 (firstpage)，把連結按鈕(lo)
![[Pasted image 20231006172403.png]]
![[Pasted image 20231006172418.png]]
![[Pasted image 20231006172434.png]]
![[Pasted image 20231006172451.png]]
![[Pasted image 20231006172514.png]]
![[Pasted image 20231006172555.png]]
![[Pasted image 20231006172612.png]]
![[Pasted image 20231006172811.png]]
