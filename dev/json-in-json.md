# 回應多層JSON結構

---

查詢的API中回覆了datas，其值也為一物件。

### 1. 新增類別

1. 在response的package中新增一類別：ResGetDatas.java

2. 依照查詢API的回應資訊中datas的格式實作POJO物件

```java
package com.example.demo.response;

public class ResGetDatas {
    public String proj_name;
    public String subject;
    public String from;
    public String to;

    public ResGetDatas() {
    // 需有無引數的預設建構子
    }
}
```

### 2. 修改Controller

1. 新增一ResGetDatas併實例化
2. 設定其資料
3. 指定至欲回應的datas中

```java
@RequestMapping(value="/api/mail/get", method = RequestMethod.POST, produces = "application/json")
public @ResponseBody Response mailGet(){
    ResGetDatas datas = new ResGetDatas();
    datas.proj_name = "某排程P";
    datas.subject = "排程的郵件主旨";
    datas.from = "rd@gmail.com";
    datas.to = "boss@gmail.com,user@gmail.com";

    Response res = new Response();
    res.code = "0000";
    res.msg = "OK";
    res.time = "2017-09-01";
    res.datas = datas;
    return res;
}
```

### 3. 效果

獲得與API規劃中查詢電文相同格式的回應

![](/assets/json_in_json_01.png)

