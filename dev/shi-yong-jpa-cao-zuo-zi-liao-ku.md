# 使用JPA操作資料庫

---

### 1. build.gradle

打開build.gradle 檢查dependencies是否有以下

* 對JPA的支持，包含spring-data-jpa、spring-orm、Hibernate
* 安裝mysql-connector-java

```
dependencies {
    compile('org.springframework.boot:spring-boot-starter-data-jpa')
    compile group: 'mysql', name: 'mysql-connector-java', version: '5.1.38'
}
```

加入後，記得Refresh Gradle Project，才會下載相依套件。

### 2. application.properties

打開src/main/resources/application.properties，輸入以下配置資料庫訊息

### 2.1 資料庫連線

```
spring.datasource.url=jdbc:mysql://localhost:3306/learn
spring.datasource.username=admin
spring.datasource.password=123456789
spring.datasource.driver-class-name=com.mysql.jdbc.Driver

spring.jpa.properties.hibernate.hbm2ddl.auto=update
```

### 2.2 連線行為設定

spring.jpa.properties.hibernate.hbm2ddl.auto的值

* create：  
  每次載入hibernate時都會刪除上一次的生成的表，然後根據你的model類再重新來生成新表，哪怕兩次沒有任何改變也要這樣執行，這就是導致資料庫表資料丟失的一個重要原因。

* create-drop ：  
  每次載入hibernate時根據model類生成表，但是sessionFactory一關閉,表就自動刪除。

* update：  
  最常用的屬性，第一次載入hibernate時根據model類會自動建立起表的結構（前提是先建立好資料庫），以後載入hibernate時根據 model類自動更新表結構，即使表結構改變了但表中的行仍然存在不會刪除以前的行。要注意的是當部署到伺服器後，表結構是不會被馬上建立起來的，是要等 應用第一次運行起來後才會。

* validate ：  
  每次載入hibernate時，驗證創建資料庫表結構，只會和資料庫中的表進行比較，不會創建新表，但是會插入新值。

### 3. 定義資料表對應類別

* 新增package com.example.demo.db
* 新增類別 MailEntity.java
* 加入註解@Entity
* 依照Table Schema建立屬性

```java
package com.example.demo.db;

import javax.persistence.Entity;

@Entity
public class MailEntity {
    public long pno;
    public String projName;
    public String subject;
    public String sender;
    public String receivers;

    public MailEntity() {}
}
```

### 4. 指定與資料表關聯

* @Id  
  主鍵

* @GeneratedValue  
  自動遞增

* @Column\(nullable = false\)  
  自動以Java型態對應欄位，並指定不可為null

```java
package com.example.demo.db;

import javax.persistence.Column;
import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.Id;

@Entity
public class MailEntity {
    @Id
    @GeneratedValue
    public long pno;

    @Column(nullable = false)
    public String projName;

    @Column(nullable = false)
    public String subject;

    @Column(nullable = false)
    public String sender;

    @Column(nullable = false)
    public String receivers;

    public MailEntity() {}
}
```

### 5. **新增數據訪問接口Repository**

#### 5.1 建立MailRepository介面

注意，是interface

```java
package com.example.demo.db;

public interface MailRepository {

}
```

#### 5.2 繼承JpaRepository

```java
package com.example.demo.db;

import org.springframework.data.jpa.repository.JpaRepository;

public interface MailRepository extends JpaRepository<MailEntity, Long> {

}
```

### 5.3 在Controller內使用

Controller內進行資料庫存取

#### 5.3.1 調整Response內datas格式

因為要顯示多筆的Entity故型態需調整為List&lt;MailEntity&gt;

```java
package com.example.demo.response;

import java.util.List;

import com.example.demo.db.MailEntity;

public class Response {
    public String code;
    public String msg;
    public String time;
    public List<MailEntity> datas;

    public Response() {
    // 需有無引數的預設建構子
    }
}
```

#### 5.3.2 引用Repository

Controller內新增：

```java
@Autowired
private MailRepository mailRepository;
```

#### 5.3.3 使用Repository

findAll\(\) 查詢全部資料

```java
//查詢全部
List<MailEntity> datas = mailRepository.findAll();
		
//...中略...
res.datas = datas;
return res;
```

#### 5.3.4 執行Server

使用查詢API回應如下：

```
{
    "code": "0000",
    "msg": "project in request body : all",
    "time": "2017-09-01",
    "datas": []
}
```

datas已經變成中括號，即array的表示法

#### 5.3.5 資料表

進資料庫檢視，確認資料表新增成功

```
+-----------+--------------+------+-----+---------+----------------+
| Field     | Type         | Null | Key | Default | Extra          |
+-----------+--------------+------+-----+---------+----------------+
| pno       | bigint(20)   | NO   | PRI | NULL    | auto_increment |
| proj_name | varchar(255) | NO   |     | NULL    |                |
| receivers | varchar(255) | NO   |     | NULL    |                |
| sender    | varchar(255) | NO   |     | NULL    |                |
| subject   | varchar(255) | NO   |     | NULL    |                |
+-----------+--------------+------+-----+---------+----------------+
```



