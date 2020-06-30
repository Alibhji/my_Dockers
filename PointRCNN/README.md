# PointRCNN base on 
 Based on --> [https://github.com/sshaoshuai/PointRCNN]

Download source file next to the Docker file:
```
$ git clone --recursive https://github.com/sshaoshuai/PointRCNN.git
``` 

Download weights in tools directory: --> [https://drive.google.com/file/d/1aapMXBkSn5c5hNTDdRNI74Ptxfny7PuC/view?usp=sharing]


Build docker file:
```
$ sudo docker build  -t "alibhji/ubuntu-devel-cuda:8.0" .
``` 

Run it:
``` 
$ nvidia-docker run -ti \
                    -v /home/mjamali/proj/OFT_3_2020/data/kitti/:/app/PointRCNN/data/KITTI \  
                    -v /home/mjamali/proj/G_All_b/point_rcnn/Docker1/PointRCNN/tools:/app/PointRCNN/tools \
                    alibhji/ubuntu-devel-cuda:8.0 bash 
``` 
