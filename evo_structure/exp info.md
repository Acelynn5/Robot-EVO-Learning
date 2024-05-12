# meta-morph 
ssh 47 

## Pre-requirements
docker volume create --name ws --opt type=none --opt device=/beegfs_hdd/data/nfs_share/users/liyuannan/nishome/Robot-EVO-Learning/ --opt o=bind

checked gpu use: 
docker info | grep "Runtimes"

## Build the Environment
cd evo_structure/docker
docker build -t 'evo-structure:latest' . 

Get the image_id.
 => => writing image sha256:51ed5a7fd30231c1f6cbf603515a4e41f7939f049b4f01c31b2112400568ec08            0.0s
 => => naming to docker.io/library/evo-structure:latest                                                 0.0s

xhost +  # 目前未设置 ：指示 X server 允许任何用户连接到 X server，而不需要进行任何认证 
docker run -it --name evo-structure --gpus all -v ws:/root/ws sha256:51ed5a7fd30231c1f6cbf603515a4e41f7939f049b4f01c31b2112400568ec08 /bin/bash

> CUDA Version 11.1.1
已经是显示进入这个镜像内的命令行了

docker start evo-structure # 目前未设置