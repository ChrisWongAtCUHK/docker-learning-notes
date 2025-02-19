# Docker學習筆記

## [[小抄] Docker 基本命令](https://yingclin.github.io/2018/docker-basic.html)
docker 程序是否存在，功能是否正常
```
docker info
```
查看系統中的容器列表
```
docker ps -a
```
指定容器名稱
```

```
啟動已終止容器
```
docker start <CONTAINER_NAME_OR_ID>
```

## [Meet the example application](https://docs.docker.com/guides/golang/build-images/#meet-the-example-application)
```
git clone https://github.com/docker/docker-gs-ping
```
Build Docker image
```
docker build --tag docker-gs-ping .
```

```
docker images
```
Create a new `docker-gs-ping:v1.0` tag for the `docker-gs-ping:latest`
```
docker image tag docker-gs-ping:latest docker-gs-ping:v1.0
```
Remove the tag
```
docker rmi docker-gs-ping:v1.0
```
Start the container and expose port `8080` to port `8080` on the host, with name `my-docker-ps-ping`
```
docker run --publish 8080:8080 --name my-docker-ps-ping docker-gs-ping
```
進入已啟動的容器
```
docker exec -i -t my-docker-ps-ping /bin/bash
```