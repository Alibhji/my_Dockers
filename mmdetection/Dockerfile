ARG PYTORCH="1.3"
ARG CUDA="10.1"
ARG CUDNN="7"

FROM pytorch/pytorch:${PYTORCH}-cuda${CUDA}-cudnn${CUDNN}-devel

# Fix for compiling cpp extensions in docker builds. See the following for more information:
# - https://github.com/NVIDIA/apex/issues/486
# - https://github.com/NVIDIA/apex/pull/490
#
# The fix is to set the same environment variables from https://github.com/pytorch/pytorch/blob/master/docker/pytorch/Dockerfile
ENV TORCH_CUDA_ARCH_LIST="6.0 6.1 7.0+PTX"
ENV TORCH_NVCC_FLAGS="-Xfatbin -compress-all"
ENV CMAKE_PREFIX_PATH="$(dirname $(which conda))/../"

RUN apt-get update && apt-get install -y libglib2.0-0 libsm6 libxrender-dev libxext6 \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

# Install mmdetection
RUN conda install cython -y && conda clean --all
RUN git clone https://github.com/open-mmlab/mmdetection.git /mmdetection
WORKDIR /mmdetection
RUN pip install --no-cache-dir -e .