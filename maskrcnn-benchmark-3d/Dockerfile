#ARG CUDA="9.0"
#ARG CUDNN="7"

#FROM nvidia/cuda:${CUDA}-cudnn${CUDNN}-devel-ubuntu16.04
ARG PYTORCH="1.4"
ARG CUDA="10.1"
ARG CUDNN="7"

FROM pytorch/pytorch:${PYTORCH}-cuda${CUDA}-cudnn${CUDNN}-devel

RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections

# install basics
RUN apt-get update -y \
 && apt-get install -y apt-utils git curl ca-certificates bzip2 cmake tree htop bmon iotop g++ \
 && apt-get install -y libglib2.0-0 libsm6 libxext6 libxrender-dev wget 

## Install Miniconda
#RUN wget -O ~/miniconda.sh 'https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh' \
# && chmod +x ~/miniconda.sh \
# && ~/miniconda.sh -b -p ~/miniconda \
# && rm ~/miniconda.sh
#ENV PATH=~/miniconda/bin:$PATH
#ENV CONDA_AUTO_UPDATE_CONDA=false
## && rm /miniconda.sh



#RUN curl -LO http://repo.continuum.io/miniconda/Miniconda-latest-Linux-x86_64.sh
#RUN bash Miniconda-latest-Linux-x86_64.sh -p /miniconda -b
#RUN rm Miniconda-latest-Linux-x86_64.sh
#ENV PATH=/miniconda/bin:${PATH}
#ENV PATH=/miniconda/envs/py36/bin:${PATH}
#RUN conda update -y conda
#RUN conda create -y --name py36 python=3.6.7  &&  conda clean -ya
#ENV CONDA_DEFAULT_ENV=py36
#RUN conda install -y ipython
#RUN  which python
RUN pip install ninja yacs cython matplotlib opencv-python

## Install PyTorch 1.0 Nightly and OpenCV
#RUN conda install pytorch==1.4.0 -y \
# && conda clean -ya



#RUN apt-get install software-properties-common -y && \
#  add-apt-repository ppa:ubuntu-toolchain-r/test -y && \
#  apt update &&  apt install g++-7 -y

#RUN update-alternatives \
#     --install /usr/bin/gcc gcc /usr/bin/gcc-7 60 \
#     --slave /usr/bin/g++ g++ /usr/bin/g++-7 \
#     --slave /usr/bin/gcc-ar gcc-ar /usr/bin/gcc-ar-7 \
#     --slave /usr/bin/gcc-nm gcc-nm /usr/bin/gcc-nm-7 \
#     --slave /usr/bin/gcc-ranlib gcc-ranlib /usr/bin/gcc-ranlib-7 \
#     && gcc --version


RUN  python --version
#RUN conda search pytorch
# Install TorchVision master
#RUN git clone https://github.com/pytorch/vision.git \
# && cd vision \
# && python setup.py install
RUN conda install torchvision -c pytorch

# install pycocotools
RUN git clone https://github.com/cocodataset/cocoapi.git \
 && cd cocoapi/PythonAPI \
 && python setup.py build_ext install

# install PyTorch Detection
RUN git clone https://github.com/facebookresearch/maskrcnn-benchmark.git \
 && cd maskrcnn-benchmark \
 && python setup.py build develop


RUN git clone https://github.com/NVIDIA/apex \
  && cd  apex \
  && pip install -v --no-cache-dir --global-option="--cpp_ext" --global-option="--cuda_ext" ./

WORKDIR /workspace/maskrcnn-benchmark