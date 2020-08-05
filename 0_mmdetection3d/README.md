# mmdetection3d
 Based on --> [https://github.com/open-mmlab/mmdetection3d/blob/master/docs/install.md]
 https://github.com/open-mmlab/mmdetection3d/blob/master/docs/benchmarks.md
 https://github.com/open-mmlab/mmdetection3d/blob/master/docs/getting_started.md


Build docker file:
```
sudo nvidia-docker build  -t "alibhji/cuda101_pytorch1.3.1:mmdetection3d" .

``` 
Run it:
``` 	
nvidia-docker run -ti -v /home/mjamali/proj/OFT_3_2020/data/kitti/object:/app/mmdetection3d/data/kitti/ -v /home/mjamali/proj/G_All_b/point_rcnn/Det3D/mmcv/:/app/mmcv "alibhji/cuda101_pytorch1.3.1:mmdetection3d"
	
chmod 777 . -R
python tools/create_data.py kitti --root-path ./data/kitti --out-dir ./data/kitti --extra-tag kitti
```




you are going have:
```
root@6bd5908ac4f8:/app/mmdetection3d# python tools/create_data.py kitti --root-path ./data/kitti --out-dir ./data/kitti --extra-tag kitti
Generate info. this may take several minutes.
[>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>] 3712/3712, 172.3 task/s, elapsed: 22s, ETA:     0s
Kitti info train file is saved to data/kitti/kitti_infos_train.pkl
[>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>] 3769/3769, 181.8 task/s, elapsed: 21s, ETA:     0s
Kitti info val file is saved to data/kitti/kitti_infos_val.pkl
Kitti info trainval file is saved to data/kitti/kitti_infos_trainval.pkl
Kitti info test file is saved to data/kitti/kitti_infos_test.pkl
create reduced point cloud for training set
[>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>] 3712/3712, 232.9 task/s, elapsed: 16s, ETA:     0s
create reduced point cloud for validatin set
[>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>] 3769/3769, 191.7 task/s, elapsed: 20s, ETA:     0s
create reduced point cloud for testing set
[>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>] 7518/7518, 191.9 task/s, elapsed: 39s, ETA:     0s
Create GT Database of KittiDataset
[>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>] 3712/3712, 100.5 task/s, elapsed: 37s, ETA:     0s
load 2207 Pedestrian database infos
load 14357 Car database infos
load 734 Cyclist database infos
load 1297 Van database infos
load 488 Truck database infos
load 224 Tram database infos
load 337 Misc database infos
load 56 Person_sitting database infos
root@6bd5908ac4f8:/app/mmdetection3d# ./tools/dist_train.sh configs/votenet/votenet_16x8_sunrgbd-3d-10class.py 8 --no-validate
bash: ./tools/dist_train.sh: Permission denied
root@6bd5908ac4f8:/app/mmdetection3d# chmod 777 . -R
root@6bd5908ac4f8:/app/mmdetection3d# ./tools/dist_train.sh configs/votenet/votenet_16x8_sunrgbd-3d-10class.py 8 --no-validate


```

by running the following code:
``` 
[SECOND] [https://github.com/open-mmlab/mmdetection3d/blob/master/docs/benchmarks.md]
./tools/dist_train.sh configs/benchmark/hv_second_secfpn_4x8_80e_pcdet_kitti-3d-3class.py 4
```


