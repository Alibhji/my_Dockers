# MMdetection
 Based on --> [https://github.com/open-mmlab/mmdetection]

Download source file next to the Docker file:
```
$ sudo docker build   -t "alibhji/torch1.3_cuda10_cudnn7:mmdetection"
``` 


Run it:
``` 
$ nvidia-docker run -ti \
                    -v /home/mjamali/proj/OFT_3_2020/data/kitti/:/app/PointRCNN/data/KITTI \  
                    alibhji/torch1.3_cuda10_cudnn7:mmdetection bash 
``` 
