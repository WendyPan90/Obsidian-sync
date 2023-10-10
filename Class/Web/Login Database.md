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
	7. 回到default檔案的設計頁面，在工具箱中把"**DetailsView**" (方便查看資料) 和"**SqlDataSource**" (網頁和資料庫的連結) 放入頁面中。
		![[Pasted image 20231006171346.png]]
![[Pasted image 20231006171402.png]]
![[Pasted image 20231006171410.png]]
![[Pasted image 20231006171423.png]]
![[Pasted image 20231006171433.png]]
![[Pasted image 20231006171443.png]]
![[Pasted image 20231006171452.png]]
![[Pasted image 20231006171508.png]]
![[Pasted image 20231006171525.png]]
![[Pasted image 20231006171543.png]]
![[Pasted image 20231006171557.png]]
![[Pasted image 20231006171803.png]]
![[Pasted image 20231006171817.png]]
![[Pasted image 20231006171826.png]]
![[Pasted image 20231006171849.png]]
![[Pasted image 20231006171859.png]]
![[Pasted image 20231006172350.png]]
![[Pasted image 20231006172403.png]]
![[Pasted image 20231006172418.png]]
![[Pasted image 20231006172434.png]]
![[Pasted image 20231006172451.png]]
![[Pasted image 20231006172514.png]]
![[Pasted image 20231006172555.png]]
![[Pasted image 20231006172612.png]]
![[Pasted image 20231006172811.png]]
