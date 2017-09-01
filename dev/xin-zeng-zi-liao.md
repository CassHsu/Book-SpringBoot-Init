# 新增資料

---

等等，只有查詢跟設定，那資料哪裡來？

好吧，雖然我們關注的目標是查詢跟設定，但還是開一個介面來新增預設資料。

### 1. Controller新增Method

新增一Method如下，預設使用Http GET

* 呼叫後生成一個預設資料
* 寫入資料庫
* 回傳寫入結果
* 將結果透過Response回覆使用者（可看到其pno）

```java
@RequestMapping("/api/mail/add")
public @ResponseBody MailEntity addMailProj() {
		
    MailEntity mail = new MailEntity();
    mail.projName = "default name";
    mail.subject = "default subject";
    mail.sender = "";
    mail.receivers = "";
		
    mail = mailRepository.save(mail);
    mailRepository.flush();
		
    return mail;
}
```

### 2. 實際查詢

啟動App，利用Postman或瀏覽器呼叫/api/mail/add

![](/assets/add_default.png)

### 3. 檢視資料庫

確實存在編號為1的資料

```
+-----+--------------+-----------+--------+-----------------+
| pno | proj_name    | receivers | sender | subject         |
+-----+--------------+-----------+--------+-----------------+
|   1 | default name |           |        | default subject |
+-----+--------------+-----------+--------+-----------------+
```







