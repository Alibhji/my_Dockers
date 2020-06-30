build it:
sudo docker build  -t "alibhji/ubuntu-devel-cuda:8.0" . 

Run:
sudo nvidia-docker run -it alibhji/ubuntu-devel-cuda:8.0 bash

To mount dataset:
nvidia-docker run -it -v /home/mjamali/proj/OFT_3_2020/data/kitti/:/testenv/KITTI alibhji/ubuntu-devel-cuda:8.0 bash


