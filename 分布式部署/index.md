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

进入：tmux
退出：Ctrl+d或者显式输入exit命令，就可以退出 Tmux 窗口
重新接入已存在的会话：tmux attach

