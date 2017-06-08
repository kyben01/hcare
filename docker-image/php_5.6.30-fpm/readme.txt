
#################################
# Docker Build Image
#################################

Installed Packages:
1.Phalcon 3.1.2
2.Composer
3.Node
4.Npm
5.Bower
6.Git
7.Robo
8.Redis



# Building Docker Image
$ sudo docker build -t {image-name}:{version} .

# run and see your new build image
$ sudo docker images


# Test if the listed packages has been successfully installed

# Container directory
$ sudo docker run --rm --name {name} -ti {image}:{version} /bin/bash

$ Test Phalcon
$ phalcon info

# Test Composer
$ compose help

# Test Node
$ node -v

# Test Npm
$ npm -v

# Test Bower
$ bower -v

# Test Bower
$ bower -v

# Test Bower
$ bower -v

# Git
$ git --version

# Robo
$ robo

# Redis
$ redis-cli
$ 127.0.0.1:6379 > ping 
# it should be return PONG

# To Exit Container Directory 
$ exit


#################################
# Dongled Image
#################################

# List Dongling Images
sudo docker images --filter "dangling=true"

# Remove ALL Dongling image
sudo docker rmi $(sudo docker images -q --filter "dangling=true")
