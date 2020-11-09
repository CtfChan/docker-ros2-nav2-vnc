# Docker ROS2 NAV2 VNC
This is a simple docker image that allows you to run the Navigation2 tutorials inside a Docker and visualize the results via VNC. The code is based on [Tiryoh's Github repository](https://github.com/Tiryoh/docker-ros2-desktop-vnc).


## How to Use
`cd` into a directory that you wish to mount 

```
sudo docker pull ctfchan/ros2-nav2-vnc:foxy

sudo docker run -p 6080:80 -p 5900:5900\
    -v $(pwd):/home/ubuntu/new_folder \
    --name ros2_container_inst \
    -e RESOLUTION=1920x1080 \
	ctfchan/ros2-nav2-vnc:foxy
```

## Building 
```
cd foxy
sudo docker build -t ctfchan/ros2-nav2-vnc:foxy .
sudo docker push ctfchan/ros2-nav2-vnc:foxy
```


## Sources
- https://automaticaddison.com/how-to-install-and-launch-ros2-using-docker/
- https://github.com/Tiryoh/docker-ros2-desktop-vnc


