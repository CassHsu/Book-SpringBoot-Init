# 回傳使用JSON格式

---

### 新增承載回應的類別

1. 新增package com.example.demo.response
2. 在該package中新增一個類別Response.java
3. 依照[API回應格式](/api/README.md)增加屬性
4. 確保會有空的建構子

```java
package com.example.demo.response;

public class Response {
    public String code;
    public String msg;
    public String time;
    public String datas;

    public Response() {
    // 需有無引數的預設建構子
    }
}
```

### 修改Controller

1. 將Method回傳類型改為Response
2. 將Response實例化，並設定其內容
3. 在該方法的註解定義處加入produces = "application/json"

#### Get Code

```java
@RequestMapping(value="/api/mail/get", method = RequestMethod.POST, produces = "application/json")
public @ResponseBody Response mailGet(){
    Response res = new Response();
    res.code = "0000";
    res.msg = "OK";
    res.time = "2017-09-01";
    res.datas = "";
    return res;
}
```

#### Get 測試結果

![](/assets/json_res_01.png)

#### Set Code

```java
@RequestMapping(value="/api/mail/set", method = RequestMethod.POST,  produces = "application/json")
public @ResponseBody Response mailSet(){
    Response res = new Response();
    res.code = "0000";
    res.msg = "OK";
    res.time = "2017-09-01";
    res.datas = "";
    return res;
}
```

#### Set 測試結果

![](/assets/json_res_02.png)

### 可產生基礎JSON回應



