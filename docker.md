### Commands

```
docker version

docker info

docker images

docker rmi <image id or image name>

docker build -t <image name>:<version> .

-t: tag

docker tag <image name> <account>/<image name>:<version>

docker push <account>/<image name>:<version>

docker pull <account>/<image name>

docker ps -a

docker run -td --name=<container name> <image name>

-d: detached
-t: Allocate a pseudo-tty
-p: hostPort:containerPort

docker start <container id or container name>

docker stop <container id or container name>

docker rm <container id or container name>

docker stack ls

docker service ls

docker network ls

docker network create <network name>

docker network connect <network name> <container id or container name>

docker inspect <container id or container name>
```