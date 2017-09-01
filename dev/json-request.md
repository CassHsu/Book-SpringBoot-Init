# 接收JSON Request

---

上行格式也為JSON，故須將Request Body內的JSON格式對應為基礎的Java類別。

此段落目標為：

* 於Controller內以Java類別接收上行電文內JSON格式之內容
* 將內容解開回傳於Response內驗證是否接收成功

## 1. 查詢

---

### 1.1 建立接收對應類別

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

    ResGetDatas req = new ResGetDatas();
    req.proj_name = "某排程P";
    req.subject = "排程的郵件主旨";
    req.from = "rd@gmail.com";
    req.to = "boss@gmail.com,user@gmail.com";

    Response res = new Response();
    res.code = "0000";

    //將查詢的值設定在msg回傳驗證
    res.msg = "project in request body : " + projNo;
    res.time = "2017-09-01";
    res.datas = req;
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

執行結果如下![](/assets/json_req_01.png)

## 2. 設定

---

### 2.1 建立接收對應類別

1. 建立新類別ReqSetBdy.java
2. 依照查詢的上行電文建立屬性
3. 為方便打印內容，指定toString方法

```java
package com.example.demo.request;

public class ReqSetBdy {
    public String project;
    public String subject;
    public String from;
    public String to;

    public ReqSetBdy() {
    // 需有無引數的預設建構子
    }

    @Override
    public String toString() {
    return "ReqSetBdy [project=" + project + ", subject=" + subject + ", from=" + from + ", to=" + to + "]";
    }
}
```

### 2.2 修改Controller內的設定Method

1. mailSet\(\)的引數括號內新增@RequestBody ReqSetBdy body
2. 宣告要接收Request Body，由ReqSetBdy body物件承接

```java
@RequestMapping(value="/api/mail/set", method = RequestMethod.POST,  produces = "application/json")
public @ResponseBody Response mailSet(@RequestBody ReqSetBdy body){
    Response res = new Response();
    res.code = "0000";

    //將設定的值回傳驗證
    res.msg = body.toString();
    res.time = "2017-09-01";
    res.datas = null;
    return res;
}
```

### 2.3 執行電文檢視查詢結果

* Postman工具記得指定： Content-Type: application/json
* 需有Request Body：

```js
{
    "project": 0,
    "subject": "新主旨",
    "from": "rd1@gmail.com",
    "to": "boss@gmail.com,user@gmail.com,user2@gmail.com"
}
```

執行結果如下

```js
{
    "code": "0000",
    "msg": "ReqSetBdy [project=0, subject=新主旨, from=rd1@gmail.com, to=boss@gmail.com,user@gmail.com,user2@gmail.com]",
    "time": "2017-09-01",
    "datas": null
}
```

![](/assets/json_req_02.png)

