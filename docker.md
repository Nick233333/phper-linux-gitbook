#### Docker 常用命令

```
docker pull redis #拉取镜像，默认 latest 版本
```
```
docker pull mysql:8.0 #拉取指定版本镜像
```

```
docker images #查看镜像
```

```
docker image ls #查看镜像
```

```
docker image ls -f dangling=true #查看虚悬镜像
```

``` 
docker image prune #删除虚悬镜像
```

```
docker image rm acfec9788376 #根据 docker id 删除镜像
```

```
docker image rm mysql:8.0.13 #根据 docker 镜像 tag 删除
```

```
docker rmi nginx:1.15-alpine #删除 nginx 镜像
```

```
docker ps -aq #查看所有容器 id
```

```
docker stop $(docker ps -aq) #暂停所有容器
```

```
docker rm -f my-redis #强制删除运行中的容器
```

```
docker container prune #删除所有停止运行的容器
```

```
docker rm $(docker ps -aq) #删除所有停止运行的容器
```

```
 docker run -p 16379:6379 --name redis -v /redis-data:/data -d redis redis-server --requirepass "123456" #运行 redis 并且设置密码和数据持久化
```

```
docker run --name my-mysql -p 13306:3306 -v /mysql-data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=mysql -d mysql:5.7 #运行 mysql 并且设置密码和数据持久化
```

```
docker run --name my-nginx -d -p 8080:80 -v /test/nginx/www/a:/usr/share/nginx/html -v /test/nginx/log:/var/log/nginx -v /test/nginx/www/conf/nginx.conf:/etc/nginx/conf/nginx.conf nginx:1.18-alpine #运行 nginx 并且设置日志和配置文件和挂载目录
```
