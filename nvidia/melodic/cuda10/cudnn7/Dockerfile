FROM turlucode/ros-melodic:cuda10

MAINTAINER Athanasios Tasoglou <athanasios@tasoglou.net>
LABEL Description="ROS-Melodic-Desktop with CUDA 10 and cuDNN 7 support (Ubuntu 18.04)" Vendor="TurluCode" Version="1.0"

# Install packages without prompting the user to answer any questions
ENV DEBIAN_FRONTEND noninteractive 

## CUDNN Runtime-packages
ENV CUDNN_VERSION 7.6.0.64
LABEL com.turlucode.ros.cudnn="${CUDNN_VERSION}"

RUN apt-get -o Acquire::http::proxy="socks5h://127.0.0.1:1089/" update && \
    apt-get -o Acquire::http::proxy="socks5h://127.0.0.1:1089/" install -y --no-install-recommends \
            libcudnn7=$CUDNN_VERSION-1+cuda10.1 && \
    apt-mark hold libcudnn7 && \
    rm -rf /var/lib/apt/lists/*

## CUDNN Devel-packages
RUN apt-get -o Acquire::http::proxy="socks5h://127.0.0.1:1089/" update && \
    apt-get -o Acquire::http::proxy="socks5h://127.0.0.1:1089/" install -y --no-install-recommends \
            libcudnn7=$CUDNN_VERSION-1+cuda10.1 \
            libcudnn7-dev=$CUDNN_VERSION-1+cuda10.1 && \
    apt-mark hold libcudnn7 && \
    rm -rf /var/lib/apt/lists/*

EXPOSE 1089

# Launch terminator
CMD ["terminator"]
