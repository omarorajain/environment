FROM osrf/ros:humble-desktop-full

ENV LIBVA_DRIVER_NAME=d3d12
ENV LD_LIBRARY_PATH=/usr/lib/wsl/lib

RUN apt-get update && apt-get install -y software-properties-common curl
RUN add-apt-repository ppa:kisak/kisak-mesa -y

RUN apt-get update && apt-get upgrade -y && apt-get install -y \
    ros-humble-ros-gz \
    ros-humble-gazebo-ros \ 
    ros-humble-rviz-imu-plugin \
    ros-humble-navigation2 \
    ros-humble-nav2-bringup \
    ros-humble-turtlebot3-gazebo \
    ros-humble-dynamixel-sdk \
    ros-humble-turtlebot3-msgs \
    ros-humble-turtlebot3 \
    python3-colcon-clean \
    wget \
    nano \
    vainfo \
    mesa-utils \
    && rm -rf /var/lib/apt/lists/*

RUN useradd -m umarv && echo "umarv:umarv123" | chpasswd && adduser umarv sudo
USER umarv
WORKDIR /home/umarv

RUN echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
RUN echo "source /usr/share/colcon_cd/function/colcon_cd.sh" >> ~/.bashrc
RUN echo "export _colcon_cd_root=/opt/ros/humble/" >> ~/.bashrc
RUN echo "source /usr/share/colcon_argcomplete/hook/colcon-argcomplete.bash" >> ~/.bashrc
RUN echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc