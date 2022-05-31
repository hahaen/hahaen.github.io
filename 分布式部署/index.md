# 分布式部署


![配置图](/img/分布式部署/配置图.png)


## 服务器配置java

[injdk.cn](https://www.injdk.cn/)  
各种JAVA JDK的镜像分发

![jdk](/img/分布式部署/1.png)

## 配置docker

## 下载代码

如 ：
```text
git clone https://github.com/hahaen/wxshop.git
```

## 启动MySQL

```text
docker run -d -v `pwd`/wxshop-data:/var/lib/mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=wxshop --name=wxshop-mysql mysql
```

需要改成自己地址

![mysql](/img/分布式部署/2.png)


创建order数据库

```text
docker exec -it wxshop-mysql mysql -uroot -proot -e 'create database if not exists `order`'
```

## redis

```text
docker run -p 6379:6379 -d redis
```

## zookeeper

```text
docker run -p 2181:2181 -d zookeeper
```

## nginx

![创建nginx目录](/img/分布式部署/3.png)


![nginx.conf配置](/img/分布式部署/4.png)

```
events{}
http {
    include    mime.types;
    upstream app {
        server 172.23.0.1:8080;
        server 172.23.0.1:8081;
    }
    
    server {
        location /api {
            proxy_pass http://app;
        }
    location / {
            root   /static;
            autoindex on;
        }
    }
}
```

注意：如果只有 html 是对的，css js 都写错写成了 text/plain 而不是 text/css

一定要在配置加上`include    mime.types;`

![误区](/img/分布式部署/6.png)

改成机器上的ip

![文件](/img/分布式部署/5.png)

启动nginx

start_nginx.sh

```text
docker run -d -p 5000:80 -v 文件目录/build:/static -v (/root/nginx-conf/nginx.conf)配置目录:/etc/nginx/nginx.conf nginx
```

## tmux

终端复用器

[tmux教程](https://www.ruanyifeng.com/blog/2019/10/tmux.html)

* 创建0：`tmux new -s 0`
* 创建1：`tmux new -s 1` 
* 查看所有tmux: tmux ls
* 重新接入已存在的会话：`tmux attach -t 0`
* 退出（下次可进入）：`Ctrl+b 再单独按d`
* 退出（杀死）：`Ctrl+d`



---

> 作者: hahaen  
> https://hahaen.github.io/%E5%88%86%E5%B8%83%E5%BC%8F%E9%83%A8%E7%BD%B2/
