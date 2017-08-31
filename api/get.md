## 查詢

---

## Request 上行

### 格式

| 項目 | 內容 |
| :--- | :--- |
| Http Method | POST |
| 路徑 | api/mail/get |

### Header

| Header Key | Header Value |
| :--- | :--- |
| Content-Type | application/json |

### Body

| 欄位 | 值 | 說明 |
| :--- | :--- | :--- |
| project | all | 所有專案的郵件資訊 |
|  | 專案代號 | 請求專案P之所有郵件資訊 |

### 範例

```js
{
    "project": "專案代號"
}
```

---

## Response 下行

### Header

不需處理

### Body

| 欄位 | 參數類型 | 說明 |
| :--- | :--- | :--- |
| subject | String | 標題 |
| from | String | 寄件人email |
| to | String | 收件人email，以逗號分隔 |

### 範例

```js
{
  "code": "0000",
  "msg": " OK",
  "time": "2017-08-31",
  "datas": {
    "subject": "排程的郵件主旨",
    "from": "rd@gmail.com",
    "to": "boss@gmail.com,user@gmail.com"
  }
}
```

## 



