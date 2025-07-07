
FROM ghcr.io/tiryoh/ros2-desktop-vnc:humble

ENV ROS_DISTRO=humble

RUN \
    source /opt/ros/$ROS_DISTRO/setup.bash && \
    sudo apt-get update && \
    sudo apt-get install python3-rosdep -y && \
    mkdir ros2_ws && cd ros2_ws && \
    git clone -b $ROS_DISTRO https://github.com/micro-ROS/micro_ros_setup.git src/micro_ros_setup && \
    rosdep update --rosdistro $ROS_DISTRO && \
    rosdep install --from-paths src --ignore-src -y --rosdistro $ROS_DISTRO && \
    colcon build && \
    source install/local_setup.bash && \
    ros2 run micro_ros_setup create_agent_ws.sh && \
    ros2 run micro_ros_setup build_agent.sh && \
    sudo apt-get clean && \
    sudo rm -rf /var/lib/apt/lists/* 