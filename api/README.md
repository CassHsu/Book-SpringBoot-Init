# API規劃

---

* 使用JSON格式進行資料交換
* 此範例中設計為求清楚易懂故盡量簡化

## API

---

[查詢](/api/query.md)

[設定](/api/setting.md)

## API回應格式

---

| 欄位 | 說明 |
| :--- | :--- |
| code | Response Code 回應代碼 |
| msg | 回應訊息，預設為OK |
| time | 後端回應時間 |
| datas | 回應資料集物件 |



### Response Code 代碼表

| code | 說明 |
| :--- | :--- |
| 0000 | 成功 |
| 9487 | 無資料 |
| 9999 | 其他錯誤，參考msg欄位或洽管理員 |

無資料範例：

```js
{
  "code": "9487",
  "msg": "OK",
  "time": "2017-08-31",
  "datas": null
}
```



