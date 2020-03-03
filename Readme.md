# ROS2 Docker 

This rep provides docker images and docker-compose files for quickly setting up ROS2, Gazebo and other Robot related softwares on docker.
- Edit the required Dockerfiles to prebuild required softwares into the images
- Compiled project binaries are stored in Docker Volumes and survive container restarts
- Customize virtual network interfaces for testing and real world deployments

## Installation instructions
1. Install Docker CE and docker-compose
2. Add your user to docker group [Link](https://docs.docker.com/install/linux/linux-postinstall/). 
3. Edit /etc/docker/daemon.json to contain the following 
   ` {
    "dns": [<dns-1>, <dns-2>],
    "insecure-registries": [<insecure local docker hub ip>]
    }
    `
4. Restart docker 
   ` sudo service docker restart ` 
5.  install xorg-server-utils for GUI applications. This varies between different OSs
    Map the docker user to the local XORG group
    `xhost local:docker`
6. Pull image 
   ` docker pull <local-hub-ip>:<port>/<ros2> `
   or build image locally by cd'ing to this repo folder 
   `docker-compose build`
7. Start the container 
   `docker-compose up -d`
8. Exec to the container as user ros  
   `docker exec -it -u ros ros2_ws_ros2_1 /bin/bash`
   `cd /opt/ros2_ws`
