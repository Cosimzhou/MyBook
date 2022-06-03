Docker笔记
==========

docker image ls
docker container ls
docker

docker run <image name/id> [--name <instance name>]
docker run <image> /bin/bash -c <command>
#docker run -it microsoft/dotnet:latest /bin/bash
docker run -it -v <local path>:/<docker path> <image>:<version> /bin/bash #与docker共享文件
docker exec -ti <container id> /bin/bash #进入已退出的docker
docker ps -a #查看运行中的docker
docker stop <instance name>
docker container stop <container id>
docker commit <container id> <image name:user/image> #保存image

docker tag <image name> <username>/<repository>:<tag name>

docker login --username=xxxx --password-stdin <docker-registry-url>
docker push <username>/<repository>:<tag name>
docker run -p 4000:80 <username>/<repository>:<tag name>

e.g.:
```
docker build -t friendlyhello .                   # Create image using this directory's Dockerfile
docker run -p 4000:80 friendlyhello               # Run "friendlyname" mapping port 4000 to 80
docker run -d -p 4000:80 friendlyhello            # Same thing, but in detached mode
docker container ls                               # List all running containers
docker container ls -a                            # List all containers, even those not running
docker container stop <hash>                      # Gracefully stop the specified container
docker container kill <hash>                      # Force shutdown of the specified container
docker container rm <hash>                        # Remove specified container from this machine
docker container rm $(docker container ls -a -q)  # Remove all containers
docker image ls -a                                # List all images on this machine
docker image rm <image id>                        # Remove specified image from this machine
docker image rm $(docker image ls -a -q)          # Remove all images from this machine
docker login                                      # Log in this CLI session using your Docker credentials
docker tag <image> username/repository:tag        # Tag <image> for upload to registry
docker push username/repository:tag               # Upload tagged image to registry
docker run username/repository:tag                # Run image from a registry
docker commit 135a0d19f757 jenkins:1.0
docker save -o my_jenkins.tar jenkins:1.0
docker load --input my_jenkins.tar
```


```
docker stack ls                                    # List stacks or apps
docker stack deploy -c <composefile> <appname>     # Run the specified Compose file
docker service ls                                  # List running services associated with an app
docker service ps <service>                        # List tasks associated with an app
docker inspect <task or container>                 # Inspect task or container
docker container ls -q                             # List container IDs
docker stack rm <appname>                          # Tear down an application
docker swarm leave --force                         # Take down a single node swarm from the manager

docker --version
docker info
docker-compose --version
docker-machine —version
```

查看镜像、容器的信息
docker export <container-id> > <a-tarball>
docker save <image-id> > <a-tarball>
docker inspect <image-id>
docker history —no-trunc <image-id>


命令目录


容器生命周期管理
run
start/stop/restart
kill
rm
pause/unpause
create
exec


容器操作
ps
inspect
top
attach
events
logs
wait
export
port


容器rootfs命令
commit
cp
diff


镜像仓库
login
pull
push
search


本地镜像管理
images
rmi
tag
build
history
save
import
info|version
info
version


-----------
# Dockerfile

docker build -t name .

## **ADD**

ADD命令有两个参数，源和目标。它的基本作用是从源系统的文件系统上复制文件到目标容器的文件系统。如果源是一个URL，那该URL的内容将被下载并复制到容器中。如果是压缩文件，也可以自动解压。
# Usage: ADD [source directory or URL] [destination directory]
ADD /my_app_folder /my_app_folder

## **CMD**
和RUN命令相似，CMD可以用于执行特定的命令。和RUN不同的是，这些命令不是在镜像构建的过程中执行的，而是在用镜像构建容器后被调用。
# Usage 1: CMD application "argument", "argument", ..
CMD "echo" "Hello docker!"

## **ENTRYPOINT**
配置容器启动后执行的命令，并且不可被 docker run 提供的参数覆盖。
每个 Dockerfile 中只能有一个 ENTRYPOINT，当指定多个时，只有最后一个起效。
ENTRYPOINT 帮助你配置一个容器使之可执行化，如果你结合CMD命令和ENTRYPOINT命令，你可以从CMD命令中移除“application”而仅仅保留参数，参数将传递给ENTRYPOINT命令。
```
# Usage: ENTRYPOINT application "argument", "argument", ..
# Remember: arguments are optional. They can be provided by CMD
# or during the creation of a container.
ENTRYPOINT echo
# Usage example with CMD:
# Arguments set with CMD can be overridden during *run*
CMD "Hello docker!"
ENTRYPOINT echo
```

## **ENV**
ENV命令用于设置环境变量。这些变量以”key=value”的形式存在，并可以在容器内被脚本或者程序调用。这个机制给在容器中运行应用带来了极大的便利。
```
# Usage: ENV key value
ENV SERVER_WORKS 4
```

## **EXPOSE**
EXPOSE用来指定端口，使容器内的应用可以通过端口和外界交互。
```
# Usage: EXPOSE [port]
EXPOSE 8080
```

## **FROM**
FROM命令可能是最重要的Dockerfile命令。改命令定义了使用哪个基础镜像启动构建流程。基础镜像可以为任意镜 像。如果基础镜像没有被发现，Docker将试图从Docker image index来查找该镜像。FROM命令必须是Dockerfile的首个命令。
```
# Usage: FROM [image name]
FROM ubuntu
```

## **MAINTAINER**
我建议这个命令放在Dockerfile的起始部分，虽然理论上它可以放置于Dockerfile的任意位置。这个命令用于声明作者，并应该放在FROM的后面。
```
# Usage: MAINTAINER [name]
MAINTAINER authors_name
```

## **RUN**
RUN命令是Dockerfile执行命令的核心部分。它接受命令作为参数并用于创建镜像。不像CMD命令，RUN命令用于创建镜像（在之前commit的层之上形成新的层）。
```
# Usage: RUN [command]
RUN aptitude install -y riak
```

## **USER**
USER命令用于设置运行容器的UID。
```
# Usage: USER [UID]
USER 751
```

## **VOLUME**
VOLUME命令用于让你的容器访问宿主机上的目录。
```
# Usage: VOLUME ["/dir_1", "/dir_2" ..]
VOLUME ["/my_files"]
```

## **WORKDIR**
WORKDIR命令用于设置CMD指明的命令的运行目录。
```
# Usage: WORKDIR /path
WORKDIR ~/
```



Example:
```
# Use an official Python runtime as a parent image
FROM python:2.7-slim

# Set maintainer info, which is deprecated
MAINTAINER cosim cosimzhou@hotmail.com

# Set the working directory to /app
WORKDIR /app

# Copy the current directory contents into the container at /app
ADD . /app

# Install any needed packages specified in requirements.txt
RUN pip install --trusted-host pypi.python.org -r requirements.txt

# Make port 80 available to the world outside this container
EXPOSE 80

# Define environment variable
ENV NAME World

# Run app.py when the container launches
CMD ["python", "app.py"]
```
