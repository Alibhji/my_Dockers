# frustum-convnet
 Based on --> [https://github.com/zhixinwang/frustum-convnet]

Download source file next to the Docker file:
```
$ sudo docker build   -t "alibhji/torch1.0_cuda9_cudnn7:frustum"
``` 


Run it:
``` 
$ nvidia-docker run -ti \
                    -v /home/mjamali/proj/OFT_3_2020/data/kitti/:/app/PointRCNN/data/KITTI \  
                    alibhji/torch1.0_cuda9_cudnn7:frustum bash 
``` 


you need to run docker and in directoy and run:
``` 
$ cd ops
$ bash clean.sh
$ bash make.sh
``` 