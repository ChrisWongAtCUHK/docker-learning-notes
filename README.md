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
Run in detached mode, Docker can run your container in detached mode in the background.
```
docker run -d -p 8080:8080 docker-gs-ping
```

## [Use containers for Go development](https://docs.docker.com/guides/golang/develop/)

## [Use Colima to Run Docker Containers on macOS](https://smallsharpsoftwaretools.com/tutorials/use-colima-to-run-docker-containers-on-macos/)

## [站在 Docker 的肩膀上，部署任何語言的 Web 應用到 Heroku](https://medium.com/starbugs/deploy-any-web-application-to-heroku-with-docker-b64b9b0eb93)
接著在 Heroku 上新增一個 app（自己想名字）跟目前的專案連結起來
```
heroku create <YOUR_APP_NAME>
heroku git:remote --app <YOUR_APP_NAME>
```
根據目前的 Dockerfile 建出一個叫做 `api-server` 的 image
```
docker build -t api-server .
```
把這個 image 推到 Heroku 的伺服器，由 Heroku 負責把這個 image 跑起來
```
heroku container:login
heroku stack:set container
heroku container:push web
heroku container:release web
```
