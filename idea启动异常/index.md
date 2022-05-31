# Idea启动异常

## 双击bin目录下的idea.bat

* 报错
```
 ERROR - llij.ide.plugins.PluginManager - java.net.BindException: Address already in use: bind
```

[参考](https://youtrack.jetbrains.com/issue/IDEA-238995?_ga=2.104461126.793169770.1653832196-580605303.1650608936&_gl=1*eky96f*_ga*NTgwNjA1MzAzLjE2NTA2MDg5MzY.*_ga_9J976DJZ68*MTY1MzgzMjE5Ni4zLjAuMTY1MzgzMjE5Ni4w)

运行两个命令成功解决。

```
net stop winnat

net start winnat
```




---

> 作者: hahaen  
> https://hahaen.github.io/idea%E5%90%AF%E5%8A%A8%E5%BC%82%E5%B8%B8/
