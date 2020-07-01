# This docker file is written for AVOD  by Ali Babolhavaeji at 6/30/2020

FROM tensorflow/tensorflow:1.3.0-devel-gpu-py3
WORKDIR /app
RUN git clone https://github.com/Zengyi-Qin/TLNet.git
ENV PYTHONPATH=/usr/bin/python3
ENV PYTHONPATH=$PYTHONPATH:'/app/TLNet' 
ENV PYTHONPATH=$PYTHONPATH:'/app/TLNet/avod'

RUN apt-get update &&  apt-get install -y \
  libprotobuf-dev \
  libprotoc-dev  \
   protobuf-compiler \
	libsm6 \ 
     libxext6 \
   libxrender-dev

WORKDIR /app/TLNet

RUN  sh avod/protos/run_protoc.sh \
      && pip install --upgrade pip \
      && pip3 install opencv-python   pillow


    