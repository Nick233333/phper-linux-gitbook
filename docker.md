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