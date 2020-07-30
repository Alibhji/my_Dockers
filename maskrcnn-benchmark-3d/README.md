# Maskrcnn-Benchmark-3d
 Based on --> [https://github.com/abbyxxn/maskrcnn-benchmark-3d]
 
[docker file is tested.]
Build docker file:
```
sudo nvidia-docker build  -t "alibhji/cuda9_pytorchnightly:maskrcnn3d" .
.
``` 
Run it:
``` 				
nvidia-docker run -ti -v /home/mjamali/proj/OFT_3_2020/data/kitti/object:/workspace/maskrcnn-benchmark/datasets/kitti  "alibhji/cuda9_pytorchnightly:maskrcnn3d"
```
