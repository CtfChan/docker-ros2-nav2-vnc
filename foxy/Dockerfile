FROM dorowu/ubuntu-desktop-lxde-vnc:focal AS foxy_layer
LABEL maintainer="Tiryoh<tiryoh@gmail.com>"

ENV DEBIAN_FRONTEND noninteractive
RUN echo "Set disable_coredump false" >> /etc/sudo.conf
RUN apt-get update -q && \
    apt-get upgrade -yq && \
    apt-get install -yq wget curl git tmux build-essential vim sudo lsb-release locales bash-completion tzdata gosu && \
    rm -rf /var/lib/apt/lists/*
RUN useradd --create-home --home-dir /home/ubuntu --shell /bin/bash --user-group --groups adm,sudo ubuntu && \
    echo ubuntu:ubuntu | chpasswd && \
    echo "ubuntu ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers
COPY ./ros-foxy-desktop.sh /ros-foxy-desktop.sh

RUN mkdir -p /tmp/ros_setup_scripts_ubuntu && mv /ros-foxy-desktop.sh /tmp/ros_setup_scripts_ubuntu/ && \
    gosu ubuntu /tmp/ros_setup_scripts_ubuntu/ros-foxy-desktop.sh

# FROM foxy_layer AS turtlebot3_layer

# RUN mv /turtlebot3.sh /tmp/ros_setup_scripts_ubuntu/ && \
#     gosu ubuntu /tmp/ros_setup_scripts_ubuntu/turtlebot3.sh&& \
#     rm -rf /var/lib/apt/lists/*

ENV USER ubuntu


COPY ./turtlebot3.sh /turtlebot3.sh
RUN bash /turtlebot3.sh


#unwanted
# RUN mkdir -p /tmp/ros_setup_scripts_ubuntu && mv /ros-foxy-desktop.sh /tmp/ros_setup_scripts_ubuntu/ && \
#     gosu ubuntu /tmp/ros_setup_scripts_ubuntu/ros-foxy-desktop.sh && \
#     rm -rf /var/lib/apt/lists/*