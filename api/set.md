## 設定

---

## Request 上行

### 格式

| 項目 | 內容 |
| :--- | :--- |
| Http Method | POST |
| 路徑 | api/mail/set |

### Header

| Header Key | Header Value |
| :--- | :--- |
| Content-Type | application/json |

### Body

project為必填，其餘要重新指定之欄位才填

| 欄位 | 參數類型 | 必填 | 說明 |
| :--- | :--- | :--- | :--- |
| project | String | 是 | 專案代號 |
| subject | String | 否 | 欲設定之標題 |
| from | String | 否 | 欲指定之寄件人 |
| to | String | 否 | 收件人列表，以逗號分隔 |

### 範例

欲修改主旨與寄件人

```js
{
    "project": ""
    "subject": "新主旨",
    "to": "boss@gmail.com,user@gmail.com,user2@gmail.com"
}
```

---

## Response 下行

### Header

不需處理

### Body

同基本API回應格式

### 範例

設定成功

```js
{
  "code": "0000",
  "msg": "OK",
  "time": "2017-08-31",
  "datas": null
}
```



