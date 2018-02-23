# Fast-RTPS

FROM      ubuntu:16.04
MAINTAINER Kazuki Urabe <urabe.kazuki@tis.co.jp>

RUN apt-get update \
  && apt-get -y upgrade \
	&& apt-get install -y git cmake g++ default-jre default-jdk wget unzip libssl-dev

RUN cd ~/ && wget https://services.gradle.org/distributions/gradle-4.3.1-bin.zip \
  && mkdir /opt/gradle && unzip -d /opt/gradle gradle-4.3.1-bin.zip \
  && export PATH=$PATH:/opt/gradle/gradle-4.3.1/bin \
  && cd ~/ && git clone https://github.com/eProsima/Fast-CDR \
  && cd Fast-CDR/ && cmake . && make && make install \
  && cd ~/ && git clone https://github.com/eProsima/Fast-RTPS \
  && mkdir Fast-RTPS/build && cd Fast-RTPS/build \
  && cmake -DTHIRDPARTY=ON -DBUILD_JAVA=ON -DCOMPILE_EXAMPLES=ON -DPERFORMANCE_TESTS=ON -DSECURITY=ON .. \
  && make && make install
