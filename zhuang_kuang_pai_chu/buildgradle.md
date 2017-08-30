## 選錯專案類型 {#build-gradle}

* 專案內沒看到gradle的檔案卻有pom.xml的，代表選到Maven專案...
* build.gradle內容目前至少應為：
  ```java
  dependencies {
   compile('org.springframework.boot:spring-boot-starter-web')
   testCompile('org.springframework.boot:spring-boot-starter-test')
  }
  ```

* 若少了boot-starter-web，則無法成為網站，但也不必砍掉重練，加入dependencies後執行Refresh Gradle Project即可。

  










