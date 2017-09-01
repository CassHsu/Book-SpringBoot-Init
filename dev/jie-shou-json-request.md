# 接收JSON Request

---

上行格式也為JSON，故須將Request Body內的JSON格式對應為基礎的Java類別。



## 1. 查詢

---

## 1.1 建立接收對應類別

1. 建立新package com.example.demo.request
2. 建立新類別ReqGetBdy.java
3. 依照查詢的上行電文建立屬性

```java
package com.example.demo.request;

public class ReqGetBdy {
    public String project;
	
    public ReqGetBdy() {
	// 需有無引數的預設建構子
    }
}
```

### 1.2 修改Controller內的查詢Method

1. mailGet\(\)的引數括號內新增@RequestBody ReqGetBdy body
2. 宣告要接收Request Body，由ReqGetBdy body物件承接

```java
@RequestMapping(value="/api/mail/get", method = RequestMethod.POST, produces = "application/json")
public @ResponseBody Response mailGet(@RequestBody ReqGetBdy body){
    
    //接收查詢值
    String projNo = body.project;
		
    ResGetDatas datas = new ResGetDatas();
    datas.proj_name = "某排程P";
    datas.subject = "排程的郵件主旨";
    datas.from = "rd@gmail.com";
    datas.to = "boss@gmail.com,user@gmail.com";
		
    Response res = new Response();
    res.code = "0000";
    
    //將查詢的值設定在msg回傳驗證
    res.msg = "project in request body : " + projNo;
    res.time = "2017-09-01";
    res.datas = datas;
    return res;
}
```

### 1.3 執行電文檢視查詢結果

* Postman工具記得指定： Content-Type: application/json
* 需有Request Body：

```js
{
    "project": "all"
}
```

結果如下![](/assets/json_req_01.png)

### 設定



