#FROM   nvidia/cuda:10.2-cudnn7-devel-ubuntu16.04
FROM   nvidia/cuda:10.1-cudnn7-devel-ubuntu16.04
#FROM  nvidia/cuda:9.2-cudnn7-devel-ubuntu16.04

RUN apt-get update &&  apt-get install -y \
    curl \
    wget \
    ca-certificates \
    vim \
    sudo \
    git \
    bzip2 \
    libx11-6 \
 && rm -rf /var/lib/apt/lists/*

# Create a working directory.
RUN mkdir /app
WORKDIR /app

## Create a non-root user and switch to it.
#RUN adduser --disabled-password --gecos '' --shell /bin/bash user \
# && chown -R user:user /app
#RUN echo "user ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/90-user
#USER user

## All users can use /home/user as their home directory.
#ENV HOME=/home/user
##RUN chmod 777 /home/user

# Install Miniconda.
#RUN curl -so ~/miniconda.sh https://repo.continuum.io/miniconda/Miniconda3-4.5.12-Linux-x86_64.sh \
RUN wget -O ./miniconda.sh 'https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh' \
 && chmod +x ./miniconda.sh \
 && ./miniconda.sh -b -p ./miniconda \
 && rm ./miniconda.sh
ENV PATH=/app/miniconda/bin:$PATH
ENV CONDA_AUTO_UPDATE_CONDA=false


# Create a Python 3.6 environment.
RUN /app/miniconda/bin/conda install conda-build \
 && /app/miniconda/bin/conda create -y --name py36 python=3.6\
 && /app/miniconda/bin/conda clean -ya
ENV CONDA_DEFAULT_ENV=py36
ENV CONDA_PREFIX=/app/miniconda/envs/$CONDA_DEFAULT_ENV
ENV PATH=$CONDA_PREFIX/bin:$PATH

# CUDA 9.0-specific steps.
RUN conda install -y -c pytorch \
    cudatoolkit  \
    pytorch=1.3.1 \
    torchvision \
 && conda clean -ya



# Install TorchNet, a high-level framework for PyTorch.
#RUN pip install torchnet==0.0.4
 
# Install Requests, a Python library for making HTTP requests.
RUN conda install -y requests=2.19.1 \
 && conda clean -ya

## Install Graphviz.
#RUN conda install -y graphviz=2.38.0 \
# && conda clean -ya
#RUN pip install graphviz==0.8.4

## Install OpenCV3 Python bindings.
#RUN sudo apt-get update && sudo apt-get install -y --no-install-recommends \
#    libgtk2.0-0 \
#    libcanberra-gtk-module \
# && sudo rm -rf /var/lib/apt/lists/*
#RUN conda install -y -c menpo opencv3=3.1.0 \
# && conda clean -ya

## Install PyTorch Geometric.
#RUN CPATH=/usr/local/cuda/include:$CPATH \
# && LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH \
# && DYLD_LIBRARY_PATH=/usr/local/cuda/lib:$DYLD_LIBRARY_PATH

#RUN pip install --verbose --no-cache-dir torch-scatter \
# && pip install --verbose --no-cache-dir torch-sparse \
# && pip install --verbose --no-cache-dir torch-cluster \
# && pip install --verbose --no-cache-dir torch-spline-conv \
# && pip install torch-geometric

# Set the default command to python3.
#RUN git clone https://github.com/open-mmlab/OpenPCDet.git
#RUN cd OpenPCDet && pip install -r requirements.txt 

RUN git clone https://github.com/traveller59/spconv.git --recursive
RUN sudo apt-get update && sudo apt-get install -y --no-install-recommends libboost-all-dev  cmake nano

RUN wget https://github.com/Kitware/CMake/releases/download/v3.15.2/cmake-3.15.2.tar.gz
RUN tar -zxvf cmake-3.15.2.tar.gz && cd cmake-3.15.2 && ./bootstrap && make && sudo make install
RUN cmake --version
RUN cd spconv && python setup.py bdist_wheel
RUN cd /app/spconv/dist && pip install *.whl

RUN pip install setuptools==39.1.0
RUN git clone https://github.com/poodarchu/nuscenes.git \
&& cd nuscenes\
&& pip install -r  requirements.txt
# \ && cd nuscenes && python setup.py install

RUN pip install -U setuptools
RUN git clone https://github.com/poodarchu/Det3D.git \
&& cd Det3D\
&& pip install -r  requirements.txt

RUN git clone https://github.com/NVIDIA/apex 
#	cd apex  && \
#	pip install -v --no-cache-dir ./

RUN pip install pyaml  && \
	sudo apt update && sudo apt install -y libsm6 libxext6 libxrender-dev  && \
	sudo apt-get install  -y libboost-all-dev \
	libglib2.0-0  && \
	pip install nuscenes-devkit



#RUN cd Det3D && python setup.py build develop


#RUN echo "export PATH=/usr/local/cuda-9.0/bin${PATH:+:${PATH}}" >> /home/user/.bashrc 
#ENV CUDA_LIB_PATH=/usr/local/cuda-9.0/lib
#WORKDIR /app/OpenPCDet

#CMD echo $CUDA_LIB_PATH
#CMD nvidia-smi

#CMD cd /app/OpenPCDet && python setup.py develop
