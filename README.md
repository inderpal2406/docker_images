# Docker Images
This repository contains docker images for different applications. These images are built to practice docker commands and platform management.

## How to install docker?
Before installing docker, we need to verify if our system has below two pre-requisites,
1. 64 bit processor
2. Linux kernel 3.10 or later.
If above 2 pre-requisites are not met, then docker won't be installed.

Follow below steps to install docker on Ubuntu 18.04.1 \(bionic\) x86_64 processor
1. Installing prerequisite Ubuntu packages for docker <br>
   `sudo apt-get install apt-transport-https ca-certificates curl software-properties-common`
2. Add official Docker GPG key <br>
   `curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`
3. Add docker APT repository <br>
   `sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"` <br>
   `$(lsb_release -cs)` will print distribution specific information wherein -c is for codename and -s is for short. <br>
   This will add repository to `/etc/apt/sources.list` file.
4. Update APT sources <br>
   `sudo apt-get update`
5. Install docker-ce <br>
   `sudo apt-get install docker-ce` <br>
   This installation automatically configures docker service to run on reboots and service crash. It adds following symlink, <br>
   `/etc/systemd/system/multi-user.target.wants/docker.service -> /lib/systemd/system/docker.service`
6. Verify docker installation <br>
   `sudo docker info` <br>
   This had shown us that we are using version 19.03.2 of docker-ce.
7. Add user to `docker` group to avoid typing `sudo` everytime we run `docker` command <br>
   `sudo usermod -G docker username`

## Docker installation script
An alternate way to install docker is to use a remote installation script. To use this script, weneed to `curl` it from a `get.docker.com` website. Execute below command,

`curl https://get.docker.com/ | sudo sh`

This scriptwill check our kernel version, processor and if kernel supports appropriate storage drivers. It'll then automatically install all dependencies required for docker. It'll proceed to install and start docker daemon. [The script can be found here.](./get-docker.sh) This has been stored for reference purpose, but it is recommended to curl and get the latest version of script before installaion of docker.

## Configuring docker daemon
The docker daemon "dockerd" can be configured further to customize it according to our needs. This can be referred to page number 38 in `The Docker Book` by James Turnbull.
