# 專案目標

說在前面，這是教學的範例。實際達成此目的不需如此費功夫。

---

練習掌握Spring Boot開發Web站台基礎

* 以Spring Boot建立Java Base的API Server
* 系統資料儲存於資料庫中透過API Server存取
* 前端網頁採用AJAX以API與後台Server溝通
* 打包部署

## 系統概念

---

系統架構概念圖如下：

![](/assets/spring_boot_init_arch.png)

## 使用情境

---

有一排程程式P，執行完畢後會將執行結果發送email給管理者。  
但因爲人員有可能會異動，故需有一個後台介面可以方便設定接收email之對象，與指定合宜之標題。

#### 需求：

* 建立一個管理後台
* 提供API給所需之系統
* 提供管理介面供使用者設定修改
* 資料需要持久化儲存

## Use Case

---

![](/assets/spring_boot_init_uc.png)

