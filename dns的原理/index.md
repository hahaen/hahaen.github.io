# DNS的原理

## DNS

* DNS 的全称是 Domain Name System 或者 Domain Name Service，
它主要的作用就是将人们所熟悉的网址 (域名) “翻译”成电脑可以理解的 IP 地址， 这个过程叫做 DNS 域名解析。 
* 打个比方，我们登百度的地址的时候，都是敲www.baidu.com，进行登陆，难道你会去敲IP地址登百度？明显，域名容易记忆。

而且，一个域名往往对应多个DNS地址

## 浏览器中输入URL到返回页面的全过程？

1. 根据域名，进行DNS域名解析；
2. 拿到解析的IP地址，建立TCP连接；
3. 向IP地址，发送HTTP请求；
4. 服务器处理请求；
5. 返回响应结果；
6. 关闭TCP连接；
7. 浏览器解析HTML；
8. 浏览器布局渲染；






---

> 作者: hahaen  
> https://hahaen.github.io/dns%E7%9A%84%E5%8E%9F%E7%90%86/
