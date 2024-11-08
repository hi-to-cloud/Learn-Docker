## Docker

Monolithic Architecture __> Virtualization
- 
Enterprise Applications
- FE & BE Together __> Monolithic Architecture (Jboss, Weblogic, Websphere)(Heavy Applications)
- Small Change in any component should go for entire lifecycle __> Take Long time
- .ear __> enterprise archive files


- Fe Separate Team __> Nginx, Apache
- BE Separate Team __> Tomcat, Jboss ___> .war __> Web Archive files

with help of API calls FE & BE talk to each other.

```
a big server can be logically divided into multiple servers...
Hypervisor __> it can host multiple guest servers

booting time __> less time
cost __> less
15 __> 1 server RHEL, 1 server windows, 1 server ubuntu, 1 Mac

RAM, HD allocate to VM's.
2GB RAM, 100GB HD -> 0.5GB RAM, 1GB HD

security __> VM are isolated from one to another

a clear isolation is there between servers, but it should be configured properly
```

MicroServices Architecture __> Containerization
-
- You install containerization in VM, Container don't block the resources..
- containers can get the resources dynamically.
- resource utilization is very low
- booting time is very less - may be in sec

Portability
-
- AMI → take one full OS, create VM, install application runtime(Java,NodeJs, python, DotNet), configuration(creation of users, folders, permissions, etc).download code, run the service

take AMI out of this, run any where

- portability __> Docker Image

Docker image == Bare minimum OS + App run time + system packages and dependencies + App code

```
AMI __> Static file
EC2 instance __> if you run AMI, it can create instance __> Running version of AMI is called instance

Docker image __> static file
Docker container __> running instance of image is called container
```


## Docker Commands
→ Remove all images
```
docker system prune -a
``` 

→ List of Docker images
```
docker images
```
```
docker image ls
```
→ Pull Image
```
docker pull <name>:<version>
```
→ Remove Image\
→ Stop Container & remove Container then only we able to remove Image
```
docker rmi image a6bd
```
→ Create Container
```
docker create <img-id> or <name>:<version>
```
→ Run Container
```
docker start <container-id>
```
→ Note
```
docker run = docker pull + docker create + docker start
```
→ Show Running Containers
```
docker container ls
```
→ Show Stopped Containers
```
docker container ls -a
```
→ Stop Container
```
docker stop <container-id>
```
→ Remove Container
```
docker rm <container-id>
```
```
docker rm -f <container-id> // -f = force
```
```
docker pull nginx

docker image ls
REPOSITORY                    TAG       IMAGE ID       CREATED        SIZE
nginx                         latest    a6bd71f48f68   2 days ago     187MB
gcr.io/k8s-minikube/kicbase   v0.0.40   c6cc01e60919   4 months ago   1.19GB

docker create a6bd
6443c5288acdaa419357237a21d05525be8c3d885268a36c4b3733a5285ab42c

docker start 6443
6443

docker container ls
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS         PORTS     NAMES
6443c5288acd   a6bd      "/docker-entrypoint.…"   29 seconds ago   Up 9 seconds   80/tcp    clever_jang
```
```
Run in Detach Mode
    - docker run -d nginx
Run with Specific Port
    - docker run -d -p <Host-Port>:<Container-Port> nginx
Run with Specific Name to container
    - docker run -d -p <Host-Port>:<Container-Port> --name nginx1-c nginx
Login to container
    - docker exec -it <container-id> bash 
    (it = interactive)(bash is terminal)
```
→ build image
```
docker build -t [repo-url]/[username]/[image-name]:[version] .
-t → tag image
. → mandatory it represents present working directory
```
→ push docker image
```
docker push [repo-url]/[username]/[image-name]:[version]
```