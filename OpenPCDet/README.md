# OpenPCDet
 Based on --> [https://github.com/open-mmlab/OpenPCDet]
 Installation --> [https://github.com/open-mmlab/OpenPCDet/blob/master/docs/INSTALL.md]


Build docker file:
```
$ sudo docker build   -t " sudo nvidia-docker build  -t "alibhji/cuda9_pytorch1.1:OpenPcDet" .
``` 
Run it:
``` 				
nvidia-docker run -ti -v /home/mjamali/proj/OFT_3_2020/data/kitti/object:/app/OpenPCDet/data/kitti  "alibhji/cuda9_pytorch1.1:OpenPcDet"
cd OpenPCDet/
nano setup.py --> change 'spconv==1.0' to 'spconv'
python setup.py develop
``` 
