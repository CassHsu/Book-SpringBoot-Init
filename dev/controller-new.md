# Controller

---

### 新增一個Controller ![](/assets/Controller_01_new.png)新Class

初始狀態如下

```java
package com.example.demo;

public class MailController {

}
```

### 使用註解定義為Controller

在Class上加入@Controller，並依照提示import packages

```java
package com.example.demo;

import org.springframework.stereotype.Controller;

@Controller
public class MailController {

}
```

### 新增要成為接口的Method

```java
@Controller
public class MailController {
    public String mailGet(){
      return "Post Mail Get OK";
    }
	
    public String mailSet(){
      return "Post Mail Set OK";
    }
}
```

### 使用註解定義Method接收Request

使用@RequestMapping設定路由

```java
@Controller
public class MailController {
    @RequestMapping(value="/api/mail/get", method = RequestMethod.POST)
    public String mailGet(){
      return "Post Mail Get OK";
    }
	
    @RequestMapping(value="/api/mail/set", method = RequestMethod.POST)
    public String mailSet(){
      return "Post Mail Set OK";
    }
}
```

### 使用註解定義回傳值為ResponseBody

```java
@Controller
public class MailController {
    @RequestMapping(value="/api/mail/get", method = RequestMethod.POST)
    public @ResponseBody String mailGet(){
      return "Post Mail Get OK";
    }
	
    @RequestMapping(value="/api/mail/set", method = RequestMethod.POST)
    public @ResponseBody String mailSet(){
      return "Post Mail Set OK";
    }
}
```

### 使用Postman檢視

啟動Spring Boot App，順利啟動後Console資訊：

```
Tomcat started on port(s): 8080 (http)
```

故以 localhost:8080 接上@RequestMapping\(value="該路由路徑"

#### Get

在回應的Body中回覆"Post Mail Get OK"

![](/assets/controller_02_post_get.png)

#### Set

在回應的Body中回覆"Post Mail Set OK"

![](/assets/controller_02_post_set.png)

### 建立基礎路由與接收成功



