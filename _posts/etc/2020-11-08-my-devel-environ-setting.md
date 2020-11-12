---
title: "my development environment setting"
categories:
  - etc
tags:
  - git
  - vscode
toc: true
toc_sticky: true
---

Here is my development environment setting script below.

# ubuntu 20.04

```bash
#!/bin/bash

sudo apt update -y
sudo apt dist-upgrade -y
sudo apt upgrade -y
sudo apt install essential-build -y
#git
sudo apt install git -y
#vscode
sudo apt-get install curl -y
sudo sh -c 'curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > /etc/apt/trusted.gpg.d/microsoft.gpg'
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'
sudo apt update -y
sudo apt install code -y
#ros2 foxy
sudo apt update -y&& sudo apt install locales -y
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8
sudo apt update -y&& sudo apt install curl gnupg2 lsb-release -y
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
sudo sh -c 'echo "deb [arch=$(dpkg --print-architecture)] http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" > /etc/apt/sources.list.d/ros2-latest.list'
sudo apt update -y
sudo apt install ros-foxy-desktop -y
sudo apt install python3-colcon-common-extensions -y

#chrome
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
sudo sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
sudo apt-get update -y
sudo apt-get install google-chrome-stable -y
sudo rm -rf /etc/apt/sources.list.d/google.list
#install ruby and jekyll
sudo apt install vim -y
sudo apt-get install ruby-full build-essential zlib1g-dev -y
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
gem install jekyll bundler #error -> terminal refresh
```

<br>
# ubuntu 18.04

```bash
#!/bin/bash
sudo add-apt-repository ppa:graphics-drivers/ppa -y #nvidia 드라이버 repo
sudo add-apt-repository ppa:git-core/ppa -y #git repo
sudo apt-get update -y
sudo apt-get upgrade -y
sudo apt-get dist-upgrade -y
sudo apt install gnome-tweaks -y
sudo apt install gparted -y
sudo apt-get install build-essential -y  #make, gcc, g++등을 설치
#nvidia driver 추천 : $ubuntu-drivers devices
sudo ubuntu-drivers autoinstall -y #recommnad하는 드라이버 설치
sudo apt-get install dkms nvidia-modprobe -y #DKMS(Dynamic Kernel Module Support)
sudo apt-get install git-core -y
git config --global user.email "gaehwan.cho@lge.com"
git config --global user.name "gaehwan.cho"
sudo apt-get install curl -y
```

<br>
# util

```bash
#!/bin/bash
#chrome 설치
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
sudo sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
sudo apt-get update -y
sudo apt-get install google-chrome-stable -y
sudo rm -rf /etc/apt/sources.list.d/google.list

#docker install
sudo apt-get install \ apt-transport-https \ ca-certificates \ curl \ gnupg-agent \ software-properties-common -y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
sudo apt-get update -y
sudo apt-get install docker-ce docker-ce-cli containerd.io -y
sudo usermod -aG docker $USER #현재 사용자에게 docker sudo 권한 주기

#vscode
sudo apt-get install curl -y
sudo sh -c 'curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > /etc/apt/trusted.gpg.d/microsoft.gpg'
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'
sudo apt-get update -y
sudo apt-get install code -y
```

<br>
# ros2 install

```bash
#!/bin/bash
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8
sudo apt update -y && sudo apt install curl gnupg2 lsb-release -y
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
sudo sh -c 'echo "deb [arch=$(dpkg --print-architecture)] http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" > /etc/apt/sources.list.d/ros2-latest.list'
sudo apt update && sudo apt install -y \
  build-essential \
  cmake \
  git \
  python3-colcon-common-extensions \
  python3-pip \
  python-rosdep \
  python3-vcstool \
  wget
# install some pip packages needed for testing
python3 -m pip install -U \
  argcomplete \
  flake8 \
  flake8-blind-except \
  flake8-builtins \
  flake8-class-newline \
  flake8-comprehensions \
  flake8-deprecated \
  flake8-docstrings \
  flake8-import-order \
  flake8-quotes \
  pytest-repeat \
  pytest-rerunfailures \
  pytest \
  pytest-cov \
  pytest-runner \
  setuptools
# install Fast-RTPS dependencies
sudo apt install --no-install-recommends -y \
  libasio-dev \
  libtinyxml2-dev
# install Cyclone DDS dependencies
sudo apt install --no-install-recommends -y \
  libcunit1-dev
sudo apt update -y
sudo apt install ros-dashing-desktop -y
sudo apt install ros-dashing-turtlesim -y
git clone https://github.com/ros/ros_tutorials.git -b dashing-devel
sudo apt-get install ros-dashing-ros2bag* -y
sudo apt-get install ros-dashing-rosbag2-storage-default-plugins -y
echo "#source /opt/ros/dashing/setup.bash" >> ~/.bashrc
#colon 설치
sudo apt-get update
sudo apt-get install python3-pip python3-apt -y
pip3 install -U setuptools
pip3 install -U colcon-common-extensions colcon-ros-bundle
pip3 install -U colcon-ros-bundle
sudo apt-get install python-rosdep -y
sudo rosdep init
rosdep update -y
```

<br>
# dnn

```bash
#!/bin/bash
#tensorflow&keras 설치
sudo pip3 install tensorflow
sudo pip3 install tensorflow-gpu
sudo pip3 install keras
#pip install for python2
sudo apt install python-pip -y
#CUDA install
sudo apt install sudo gnupg -y
sudo apt-key adv --fetch-keys "http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/7fa2af80.pub"
sudo sh -c 'echo "deb http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64 /" > /etc/apt/sources.list.d/nvidia-cuda.list'
sudo sh -c 'echo "deb http://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1804/x86_64 /" > /etc/apt/sources.list.d/nvidia-machine-learning.list'
sudo apt update
sudo apt-get install cuda-10-2 -y
sudo apt-get install libcudnn7-dev -y #cuDNN install
pip install scikit-image
pip install future
sudo pip install -U scikit-learn #scikit-learn install
sudo pip install torch torchvision #pytorch install
```
