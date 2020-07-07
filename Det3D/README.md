# Det3D
 Based on --> [https://github.com/poodarchu/Det3D]
 

Build docker file:
```
sudo nvidia-docker build  -t "alibhji/cuda9_pytorch1.3.1:Det3D" .
``` 
Run it:
``` 				
nvidia-docker run -ti -v /home/mjamali/proj/OFT_3_2020/data/kitti/object:/app/OpenPCDet/data/kitti  "alibhji/cuda9_pytorch1.3.1:Det3D"
nano setup.py # --> change 'spconv==1.0' to 'spconv'
python setup.py develop  # it
```

```
cd  apex
pip install -v --no-cache-dir --global-option="--cpp_ext" --global-option="--cuda_ext" ./
``` 
cd spconv
edit setup.py file: --> change 'spconv==1.0' to 'spconv'

``` 				
nano setup.py 
python setup.py develop
 
cd Det3D
python setup.py build develop

```

train second
```
cd tools
bash scripts/dist_train.sh 4  --cfg_file ./cfgs/kitti_models/second.yaml  --batch_size 32  --epochs 80
```

train pv-rcnn
```
cd tools
bash scripts/dist_train.sh 4  --cfg_file ./cfgs/kitti_models/second.yaml  --batch_size 32  --epochs 80
```

# training is working but evaluation has problem with the following command:
bash scripts/dist_train.sh 4 --cfg_file cfgs/kitti_models/pv_rcnn.yaml --batch_size 16 --epochs 80

python test.py --cfg_file cfgs/kitti_models/pv_rcnn.yaml --batch_size 16 --ckpt /app/PCDet/output/kitti_models/pv_rcnn/default/ckpt/checkpoint_epoch_80.pth 