FROM osrf/ros:noetic-desktop-full 

RUN apt update && apt install -y \
    nano \
    git \
    python3-pip \
    python3-rosdep \
    python3-rosinstall \
    python3-rosinstall-generator \
    python3-wstool \
    build-essential \
    ros-noetic-rqt* \
    ros-noetic-turtlebot3* \
    ros-noetic-gmapping \
    ros-noetic-move-base* \
    ros-noetic-dwa-local-planner \
    ros-noetic-realsense2-camera \
    ros-noetic-teleop-twist-keyboard \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /root/catkin_ws

COPY ./ros_packages /root/catkin_ws/src

RUN /bin/bash -c "source /opt/ros/noetic/setup.bash && catkin_make"

RUN echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc && \
    echo "source /root/catkin_ws/devel/setup.bash" >> ~/.bashrc

CMD [ "/bin/bash" ]