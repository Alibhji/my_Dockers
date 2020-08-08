# OpenPCDet
 Based on --> [https://github.com/open-mmlab/OpenPCDet]
 
Installation --> [https://github.com/open-mmlab/OpenPCDet/blob/master/docs/INSTALL.md]


Build docker file:
```
git clone https://github.com/open-mmlab/OpenPCDet.git
sudo nvidia-docker build  -t "alibhji/cuda9_pytorch1.3.1:OpenPcDet" .
``` 
Run it to have interactive terminal:
``` 				
nvidia-docker run -ti  \
     -v /home/mjamali/proj/OFT_3_2020/data/kitti/object:/app/OpenPCDet/data/kitti \
	 -v /home/mjamali/proj/G_All_b/point_rcnn/OpenPCDet/benchmark_models:/app/OpenPCDet/benchmark_models \
     "alibhji/cuda9_pytorch1.3.1:OpenPcDet" 
``` 


Run it to have jupyter:
``` 				
nvidia-docker run -ti  \
     -v /home/mjamali/proj/OFT_3_2020/data/kitti/object:/app/OpenPCDet/data/kitti \
	 -v /home/mjamali/proj/G_All_b/point_rcnn/OpenPCDet/benchmark_models:/app/OpenPCDet/benchmark_models \
	 -v myNotebooks:/app/OpenPCDet/myNotebooks \
	 -p 8888:8888 \
     "alibhji/cuda9_pytorch1.3.1:OpenPcDet" \
	 jupyter notebook --ip=0.0.0.0 --no-browser
	 
``` 

  


	

### KITTI Dataset
* Please download the official [KITTI 3D object detection](http://www.cvlibs.net/datasets/kitti/eval_object.php?obj_benchmark=3d) dataset and organize the downloaded files as follows (the road planes could be downloaded from [[road plane]](https://drive.google.com/file/d/1d5mq0RXRnvHPVeKx6Q612z0YRO1t2wAp/view?usp=sharing), which are optional for data augmentation in the training):
* NOTE: if you already have the data infos from `pcdet v0.1`, you can choose to use the old infos and set the DATABASE_WITH_FAKELIDAR option in tools/cfgs/dataset_configs/kitti_dataset.yaml as True. The second choice is that you can create the infos and gt database again and leave the config unchanged.

```
OpenPCDet
├── data
│   ├── kitti
│   │   │── ImageSets
│   │   │── training
│   │   │   ├──calib & velodyne & label_2 & image_2 & (optional: planes)
│   │   │── testing
│   │   │   ├──calib & velodyne & image_2
├── pcdet
├── tools
```

* Generate the data infos by running the following command: 
```python 
python -m pcdet.datasets.kitti.kitti_dataset create_kitti_infos tools/cfgs/dataset_configs/kitti_dataset.yaml
```

run setup.py:
```
python setup.py develop
```

train second
```
cd tools
bash scripts/dist_train.sh 4  --cfg_file ./cfgs/kitti_models/second.yaml  --batch_size 32  --epochs 80
```

train pv-rcnn
```
cd tools
bash scripts/dist_train.sh 4  --cfg_file ./cfgs/kitti_models/pointrcnn.yaml  --batch_size 32  --epochs 80
```

# benchmark [https://github.com/open-mmlab/OpenPCDet/blob/master/README.md#model-zoo]:
python test.py --cfg_file ./cfgs/kitti_models/pointrcnn.yaml --batch_size 16 --ckpt /app/OpenPCDet/benchmark_models/pointrcnn_7870.pth 
