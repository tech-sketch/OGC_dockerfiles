# Kurento & OpenCV3.4

FROM      ubuntu:16.04
MAINTAINER Kazuki Urabe <urabe.kazuki@tis.co.jp>

RUN apt-get update \
  && apt-get -y upgrade \
	&& apt-get install -y build-essential \
  && apt-get install -y cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev \
  && apt-get install -y python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev


RUN mkdir ~/workspace/ && cd ~/workspace/ \
  && git clone https://github.com/opencv/opencv.git \
  && git clone https://github.com/opencv/opencv_contrib.git


RUN cd ~/workspace/opencv_contrib/
  && git checkout refs/tags/3.4.0 \
  && cd ~/workspace/opencv/ \
  && git checkout refs/tags/3.4.0 \
  && mkdir build && cd build \
  && cmake -D CMAKE_BUILD_TYPE=Release -D CMAKE_INSTALL_PREFIX=/usr/local -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules/ .. \
  && make && make install
