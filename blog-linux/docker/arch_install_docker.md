## arch安装docker
### 安装
```
sudo pacman -S docker
```
### 开启docker服务
```
sudo systemctl enable --now docker
```
###以当前用户运行docker命令
```
sudo groupadd docker

sudo gpasswd -a ${USER} docker

newgrp ${USER}
```
### docker命令
拉取镜像：  
```
docker pull image_name
```
创建容器：  
以ubuntu镜像，容器名称为linux举例  
``` 
docker run -i -t --name linux ubuntu bash
```
运行容器：
```
docker start -i linux
```
---
[返回到上一页](https://storm-1614.github.io/blog-linux/)
[返回到主页](https://storm-1614.github.io/)
