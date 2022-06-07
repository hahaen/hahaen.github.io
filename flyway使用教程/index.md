# Flyway使用教程


[官网](https://flywaydb.org/documentation/)

<br>

[引入Maven plugin](https://flywaydb.org/documentation/usage/maven/)

```
   <plugin>
      <groupId>org.flywaydb</groupId>
      <artifactId>flyway-maven-plugin</artifactId>
      <version>6.2.4</version>
      <configuration>
      <user>root</user>
      <password>root</password>
      <url>jdbc:mysql://localhost:3306/xxx</url>
      </configuration>
   </plugin>

```
<br>

[创建目录](https://flywaydb.org/documentation/concepts/migrations#versioned-migrations)

* 在`resources`下创建目录`db`
* 在目录`db`创建目录`migration`
* 在目录`migration`下创建文件`V1__Create_User.sql`
* 在文件`V1__Create_User.sql`下写相应sql

如图

![创建目录图](/img/Flyway使用教程/创建目录图.png)

```
mvn flyway:clean
```

```
mvn flyway:migrate
```






---

> 作者: hahaen  
> https://hahaen.github.io/flyway%E4%BD%BF%E7%94%A8%E6%95%99%E7%A8%8B/
