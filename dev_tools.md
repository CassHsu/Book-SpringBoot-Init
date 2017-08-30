# Dev Tools {#dev-tools}

### 採用Gradle安裝 {#gradle}

1. buid.gradle檔中的dependencies內新增comile項目
   ```java
   dependencies {
       compile("org.springframework.boot:spring-boot-devtools")
   }
   ```
2. 專案按右鍵呼叫選單，在Gradle內選Refresh Gradle Project  
   ![](/assets/ying_mu_kuai_zhao_2016_-_07_-_28_shang_wu_12__12__26.png)

3. 安裝成功
   ```
   BUILD SUCCESSFUL

   Totaltime:1.576secs
   Download
   https://repo1.maven.org/maven2/org/springframework/boot/spring-boot-devtools/1.3.6.RELEASE/spring-boot-devtools-1.3.6.RELEASE.pom
   Download
   https://repo1.maven.org/maven2/org/springframework/boot/spring-boot-devtools/1.3.6.RELEASE/spring-boot-devtools-1.3.6.RELEASE.jar
   Download
   https://repo1.maven.org/maven2/org/springframework/boot/spring-boot-devtools/1.3.6.RELEASE/spring-boot-devtools-1.3.6.RELEASE-sources.jar
   ```



