---
title: "ML을 위한 Pytorch/TensorFlow Docker 환경 꾸미기"
categories: MachineLearning
tags:
  - ML
  - pytorch
  - docker
  - tensorflow
toc: true
sidebar_main: true
---

환경 : Ubuntu 20.04

# 1. Docker 설치
```bash
$ curl -fsSL https://get.docker.com > docker.sh
$ sudo sh docker.sh
$ sudo usermod -aG docker $USER # USER 그룹에 docker에 대한 권한을 append한다.
```   
`sudo docker run hello-world` 로 작동 확인   
ref.)   
[1) 모두를 위한 딥러닝 시즌2](https://www.edwith.org/boostcourse-dl-pytorch)



# 2. Docker image download
## 파이토치 이미지를 다운받기
[pytorch dockerhub (click)](https://hub.docker.com/r/pytorch/pytorch/tags?page=1&ordering=last_updated )
```
원하는 테그를 정하여 pull한다.
$ docker pull pytorch/pytorch
$ docker pull pytorch/pytorch:1.6.0-cuda10.1-cudnn7-devel
$ docker images
```
[참고사이트(click)](https://89douner.tistory.com/96?category=878197)

## pytorch image로 container 올리기
```bash
$ sudo docker run -itd --name pytorch -v /home/chogaehwan/docker_share/pytorch/:/root/share ---gpus all -p 8888:8888 pytorch/pytorch
# --gpus all GPU리소스에 접근가능하게
# --restart=always 옵션을 주면 local이 restart될때 docker이미지도 올라가있음
```
-v : `<local_folder>:<container_folder>` 로 폴더를 공유한다.   
-p : `<local port>:<container port>`에 연결한다

## jupyter 접속하기
```bash
$ conda install jupyter
# share폴더에 접속이후
$ jupyter notebook --ip=0.0.0.0 --port=8888 --allow-root
```

# 3. Docker image save
```
$ docker ps -a
$ docker stop pytorch
$ docker commit pytorch <id>/<repo name>:<tag>
```
[참고사이트(click)](https://89douner.tistory.com/96?category=878197)
# 4. Docker hub upload
```
$ docker login
$ docker push <id>/<repo name>:<tag>
```
[참고사이트1 (click)](https://89douner.tistory.com/96?category=878197)   
[참고사이트2 (click)](https://www.sauru.so/blog/build-usable-docker-image-part2/) 
