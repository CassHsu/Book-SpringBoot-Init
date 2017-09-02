# Table Schema 資料表設計

---

| 欄位 | 型態 | 鍵值 | 可否為空 | 說明 |
| :--- | :--- | :--- | :--- | :--- |
| pno | int | PK | false | 自動遞增之流水號，做為專案編號 |
| proj\_name | vchart |  | false | 專案名稱 |
| subject | vchart |  | false | 郵件主旨 |
| sender | vchart |  | false | 寄件者 |
| receivers | vchart |  | false | 收件者串列，逗號分隔 |



