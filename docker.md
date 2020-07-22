### starting
```
docker-machine stop
docker-machine start
docker-machine env
eval $(docker-machine env)
```

### docker cli
```
docker ps -a
docker container ls
docker pull resnullius/alpine-armv7l:latest

docker rmi resnullius/alpine-armv7l
docker container ls -a
docker image ls 

-shell to nginx:alpine:
  docker run -it nginx:alpine /bin/sh

-attach detach
  CTRL+P CTRL+Q (detach)
  docker attach <container>
  docker start -ai <container>
```
### docker mongo(https://hub.docker.com/r/tutum/mongodb)
```
docker run -d -p 27017:27017 -p 28017:28017 --name mongodb -e AUTH=no tutum/mongodb 
docker start <id>
mongo --host=192.168.99.100
```
