# 資料庫

---

此範例採用 MariaDB \(or MySQL\)

官方網站 [https://mariadb.com/](https://mariadb.com/)

請依照所使用之系統自行下載安裝

## 安裝

---

### Mac

Mac使用者建議Homebrew安裝：

[https://mariadb.com/kb/en/the-mariadb-library/installing-mariadb-on-macos-using-homebrew/](https://mariadb.com/kb/en/the-mariadb-library/installing-mariadb-on-macos-using-homebrew/)

### Ubuntu

**官方網站加入apt-get教學**

[https://downloads.mariadb.org/mariadb/repositories/\#mirror=ossplanet&distro=Ubuntu&distro\_release=xenial--ubuntu\_xenial&version=10.2](https://downloads.mariadb.org/mariadb/repositories/#mirror=ossplanet&distro=Ubuntu&distro_release=xenial--ubuntu_xenial&version=10.2)

## 初次設定

---

#### 執行mysql\_secure\_installation

1. 重設root密碼

2. Disallow root login remotely? \[Y/n\] Y

3. Remove test database and access to it? \[Y/n\] Y

4. Reload privilege tables now? \[Y/n\] Y

5. 使用mysql -p root -p 輸入密碼看是否能登入

   1. ERROR 1698 \(28000\): Access denied for user 'root'@'localhost'

   2. 那就sudo吧

6. 確認是否使用 utf-8，修改 /etc/mysql/my.cnf

   1. sudo vim /etc/mysql/my.cnf

   2. 在\[mysqld\]中加上此行  
      \[mysqld\]  
      character-set-server=utf8

   3. 重啟mariadb，service mysql restart

   4. 最後確認是否使用utf8

## 使用root登入

---

在終端機輸入 mysql -u root -p

輸入密碼即可進入mysql （畫面如下）

![](/assets/mysql-console.png)

## 建立新帳號 & 新資料庫

---

範例中的資料庫username、password請自行代換

此例中提供帳號admin，db為learn

資料庫Command Line指令可參考：

```
create user 'admin' identified by '123456789';
CREATE DATABASE learn;
GRANT ALL PRIVILEGES ON learn.* TO 'admin';
```

上述步驟為：

1. 新增使用者與設定密碼
2. 建立資料庫
3. 授與新帳號使用資料庫權限



