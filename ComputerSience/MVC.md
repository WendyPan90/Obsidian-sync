# MVC
### What is MVC ?
Model-View-Controller，軟體開發的架構與邏輯，不論網頁是使用[PHP網頁](https://www.ibest.tw/php-website-design.php "PHP網頁設計")還是ASP網頁開發，都可使用相同的邏輯，主要目的是用來簡化應用程式的開發與增強程式的可維護性。

### Each meaning:
* **Model**模型: 邏輯和資料處理。(實現演算法)
	> 封裝與應用程式的業務邏輯相關的資料以及對資料的處理方法，有對資料直接存取的權力，例如對資料庫的存取。用於監視此 Model 的 View 必須事先在此 Model 上註冊，從而View 可以了解在資料 Model 上發生的改變。	
* **View**視圖: UI介面。
	>並不是必須的，用於顯示所需的資訊。為了實現 View 上的重新整理功能，View 需要存取它監視的資料模型（Model），因此應該事先在被它監視的資料那裡註冊。
* **Controller**: 接收請求，協調Model與View回應結果。
	>起到不同層面間的組織作用，用於控制應用程式的流程。它處理事件並作出回應。「事件」包括用戶的行為和資料 Model 上的改變。
		
![[MVC.png]]


* 網頁開發導入MVC架構，能讓開發的過程中更明確的區分「**邏輯處理**」與「**資料呈現**」，明確的區分各元件的功能，提高系統的擴充性、可用性。此外，導入MVC更容易進行分工，團隊每個人可以在各自負責的部份進行開發，不會互相衝突或干擾。

### Adventages:
*  擴充性高
*  方便管理
*  使程式結構更直覺
*  有利於團隊分工

### Disadventages:
* 需要嚴謹的系統規劃，開發時間可能會拉長
* 系統結構複雜，不適合小型專案
* 系統肥大，效能降低

> iBest 解決了MVC的缺點也保留了其優點，效率更高

![[Pasted image 20230924122824.png]]
![[Pasted image 20230924122912.png]]
![[Pasted image 20230924123214.png]]
