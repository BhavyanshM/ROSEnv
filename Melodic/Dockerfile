FROM osrf/ros:melodic-desktop-full

RUN apt-get update && apt-get -y install sudo python-rosinstall python-rosinstall-generator \
	python-wstool build-essential python-catkin-tools python-wstool python-pip \
	libzmqpp-dev libeigen3-dev libvulkan1 mesa-vulkan-drivers vulkan-utils libsdl-image1.2-dev \
	libsdl-dev mesa-utils

RUN pip install catkin_pkg

RUN adduser --disabled-password --gecos '' docker
RUN adduser docker sudo
RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

USER docker

# nvidia-container-runtime
ENV NVIDIA_VISIBLE_DEVICES \
    ${NVIDIA_VISIBLE_DEVICES:-all}
ENV NVIDIA_DRIVER_CAPABILITIES \
    ${NVIDIA_DRIVER_CAPABILITIES:+$NVIDIA_DRIVER_CAPABILITIES,}graphics
