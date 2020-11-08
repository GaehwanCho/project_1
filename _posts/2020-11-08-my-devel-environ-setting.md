---
title: "my development environment setting"
categories:
- etc
tags:
- git
- vscode
---
Here is my development environment setting script below.
This setting is based on Ubuntu 20.04.

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