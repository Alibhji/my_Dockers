# AVOD- TLNet
 Based on --> [https://github.com/Zengyi-Qin/TLNet]

download weights from this links --> [https://cloud.tsinghua.edu.cn/f/6eb6b856efec42d19937/?dl=1 -O tlnet_pretrained.tar.gz]
```
$ cd  [docker file directory]
$ mkdir weights
``` 

Download weights in tools directory: --> [https://drive.google.com/file/d/1aapMXBkSn5c5hNTDdRNI74Ptxfny7PuC/view?usp=sharing]


Build docker file:
```
$ sudo docker build   -t "alibhji/tf1.3_gpu:avod" .

``` 

Download and extract it inside the Kiiti dataset path: --> [https://cloud.tsinghua.edu.cn/f/af6ca62301df4f14a6e4/?dl=1]

Run it:
``` 				
$ nvidia-docker run -ti \ 
-v /home/mjamali/proj/OFT_3_2020/data/kitti/:/root/Kitti \
-v ~/proj/G_All_b/point_rcnn/avod/weight:/app/TLNet/avod/models\
alibhji/tf1.3_gpu:avod  bash

``` 
