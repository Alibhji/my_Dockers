# Det3D
 Based on --> [https://github.com/poodarchu/Det3D]
 

Build docker file:
```
sudo nvidia-docker build  -t "alibhji/cuda9_pytorch1.3.1:Det3D" .
``` 
Run it:
``` 				
nvidia-docker run -ti -v /home/mjamali/proj/OFT_3_2020/data/kitti/object:/data/Datasets/KITTI/Kitti/object  "alibhji/cuda10_pytorch1.3.1:Det3d"
```
based on [https://github.com/NVIDIA/apex]
```
cd  apex
pip install -v --no-cache-dir --global-option="--cpp_ext" --global-option="--cuda_ext" ./

``` 

``` 
cd Det3D
python setup.py build develop
```
it takes around 5 minutes.

by running the following code:
```
python tools/create_data.py kitti_data_prep --root_path=data/kitti/
pip install -v --no-cache-dir ./

```

you are going have:
```
Generate info. this may take several minutes.
100%|###################################################################################################################################################################| 3712/3712 [01:15<00:00, 48.94it/s]
Kitti info train file is saved to data/kitti/kitti_infos_train.pkl
100%|###################################################################################################################################################################| 3769/3769 [01:15<00:00, 49.61it/s]
Kitti info val file is saved to data/kitti/kitti_infos_val.pkl
Kitti info trainval file is saved to data/kitti/kitti_infos_trainval.pkl
100%|###################################################################################################################################################################| 7518/7518 [02:33<00:00, 48.92it/s]
Kitti info test file is saved to data/kitti/kitti_infos_test.pkl
100%|##################################################################################################################################################################| 3712/3712 [00:14<00:00, 255.15it/s]
100%|##################################################################################################################################################################| 3769/3769 [00:18<00:00, 205.20it/s]
100%|##################################################################################################################################################################| 7518/7518 [01:08<00:00, 109.23it/s]
100%|##################################################################################################################################################################| 3712/3712 [00:11<00:00, 328.82it/s]
dataset length:  3712
load 2207 Pedestrian database infos
load 14357 Car database infos
load 734 Cyclist database infos
load 1297 Van database infos
load 488 Truck database infos
load 224 Tram database infos
load 337 Misc database infos
load 56 Person_sitting database infos
```


train an example:
```
bash ./tools/scripts/train.sh ./examples/second/configs/kitti_all_vfev3_spmiddlefhd_rpn1_mghead_syncbn.py 
```
