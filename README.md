# EC-website-project

## 一.介紹
### 1. 計畫說明：
過去工作上花費不少時間在研究電商的使用者行為，但通常只能小幅度調整對方的電商網站，這次就自己來打造一個滿意的電商吧！\
[電商前台](http://shop.sun-jie.com/) \
[電商後台](http://admin.sun-jie.com/)


### 2.使用技術：
* 後端： 使用 docker-compose (flask + Nginx) 架設於 Google Compute Engine 使用 F1 主機*2 
* 資料庫： Google Cloud Platform 的 Cloud Sql (Mysql)
* 前端： Bootstrap4 + jQuery 
* 數據追蹤： Google Anayltics 加強型電子商務


## 二.開發進度：
電商前台主架構建設(完成) > 商品資料庫設計(完成) > 電商後台主架構建設(完成) > 綠界金流串接(完成) > 前台細節調整 > 後台細節調整


### 1.[電商前台](http://shop.sun-jie.com/)
- [x] 完成week1 - 會員註冊頁
- [x] 完成week1 - 首頁
- [x] 完成week1 - 商品頁
- [x] 完成week1 - 加入購物車頁
- [x] 完成week1 - 結帳頁面

![image](https://github.com/hsuanchi/EC-website-project/blob/master/img/shop-home.png)


### 2.商品資料庫 (資料庫從 Firebase 改成 MySQL)
- [x] 完成week2 - 主頁和商品頁的資料庫修改 
- [x] 完成week3 - ORM 和關聯式資料庫設計筆記如下：
  * [Flask教學 - Flask-SQLAlchemy 資料庫連線&設定入門(一)](https://www.maxlist.xyz/2019/11/10/flask-sqlalchemy-setting/)
  * [Flask教學 - Flask-SQLAlchemy 資料庫操作-ORM篇(二)](https://www.maxlist.xyz/2019/10/30/flask-sqlalchemy/)
  * [Flask教學 - Flask-SQLAlchemy -ORM 一對多關聯篇 (三)](https://www.maxlist.xyz/2019/11/24/flask-sqlalchemy-orm/)
  * [Flask教學 - Flask-SQLAlchemy -ORM 多對多關聯篇 (四)](https://www.maxlist.xyz/2019/11/24/flask-sqlalchemy-orm2/)
  * [Flask教學 - Flask-SQLAlchemy 資料庫操作-SQL指令篇(五)](https://www.maxlist.xyz/2019/11/09/sqlalchemy-sql/)
- [x] 完成week4 - 會員加入購物車 & 購買頁面的資料庫修改
- [x] 完成week4 - 會員註冊將 Firebase 改成 MySQL

#### E-R Model 購物車
![image](https://github.com/hsuanchi/EC-website-project/blob/master/img/addToCart.png)
#### E-R Model 結帳
![image](https://github.com/hsuanchi/EC-website-project/blob/master/img/transaction.png)

### 3.[電商後台](http://admin.sun-jie.com/)

#### 商品管理
- [x] 完成week5 - 商品新增頁面
- [x] 完成week5 - 商品更新頁面
- [x] 完成week5 - 商品刪除頁面
- [x] 完成week5 - 登入頁面

![image](https://github.com/hsuanchi/EC-website-project/blob/master/img/admin-product-crud.png)

#### 會員管理
- [x] 完成week19 - 顯示會員名單
- [x] 完成week19 - 可調整為管理員權限

目前後台的登入會員，並沒有額外寫後台帳號註冊的機制。
所有的會員都只能在前台註冊，由後台可以將前台的註冊會員升級為管理員，然後使用前台的擁有管理員權限的會員帳號即可進入後台。

未來要補充的功能
  1. 未來需要再新增後台可以直接建立管理員權限的帳號機制
  2. 權限目前只設定是管理員跟普通會員，未來新增能瀏覽無法修改的限制權限

![image](https://github.com/hsuanchi/EC-website-project/blob/master/img/admin-member-crud.png)

#### 訂單管理
 - [x] 完成week20 訂單管理頁 
 - [x] 完成week20 訂單管理細節頁 
 
  完成訂單管理的頁面，可以看到目前所有的訂單狀態 (已出貨、待處理、已取消)以及訂單收件人細節。
  在點擊單筆訂單狀態時，會彈出此筆訂單的下單產品細節，在出完貨之後可以再修改此筆訂單狀態。

![image](https://github.com/hsuanchi/EC-website-project/blob/master/img/admin-order-crud.png)


### 5.金流 
- [x]  綠界金流串接 (目前金流使用測試環境，待產品上線後，會切換正式環境)
    - [x] 購物車頁面，新增收件人資訊 (Name & Phone & Address)
    - [x] 購物車頁面增加 POST 按鈕，傳送收件人資訊，並跳轉至綠界支付
    - [x] 處理接收綠界交易後 POST 回傳資訊
    - [x] 處理交易成功後，資料庫購物車狀態修改
    - [x] 處理交易成功後，資料庫交易紀錄增加
    - [x] 刻交易成功頁面
    - [x] 刻交易失敗頁面
    - [x] Issue 處理：如果購物車沒有商品，則無法傳送交易資訊 
    - [x] Issue 處理：地址部分新增市和區選單，不要讓使用者自己填寫
    - [x] Issue 處理：資料庫地址切成三份(城市、區、地址)
    

> 新版購物車頁面比較清爽一些，未來確定要用哪一家物流後，還要再加運費和物流名稱上去
![trade](https://github.com/hsuanchi/EC-website-project/blob/master/img/shopping_cart.png)

> 綠界信用卡失敗後跳轉頁面，已經保存上次填寫的收件人資訊，並且能讓使用者可以直接再次刷卡
![fail](https://github.com/hsuanchi/EC-website-project/blob/master/img/trade_fail.png)


### 6.前台細節 (待處理)
- [x] 會員權益頁面 (SEO - EAT 頁面)
- [x] 隱私權頁面 (SEO - EAT 頁面)
- [x] 品牌故事頁面 (SEO - EAT 頁面)

![image](https://github.com/hsuanchi/EC-website-project/blob/master/img/brand.png)

- [ ] 首頁
- [ ] 產品頁
- [ ] 產品分類頁


### 7.後台細節 (待處理)
- [ ] 會員介面
    * - [x] 顯示會員名單
    * - [x] 可調整為管理員權限 
- [ ] 訂單介面
    * - [x] 訂單管理總覽
    * - [x] 單筆訂單細節顯示 
    * - [ ] dashboard 顯示訂單狀態
    * - [ ] 客戶過去訂單總覽 (uid)+ 細項
- [ ] 商品管理
    * - [x] 商品資訊
    * - [ ] 商品內容管理 (所見即所得控制編輯器)
    
## 三.關於    
感謝 Huli 的每週固定時間討論專案和指導須改進的地方，以及[前端引路人計劃](https://medium.com/@hulitw/mentorship-program-350db93d5c9c)
1. 2019-08-16 [前端引路人計劃](https://medium.com/@hulitw/mentorship-program-350db93d5c9c)正式開始
2. 2020-08-16 計畫結束
