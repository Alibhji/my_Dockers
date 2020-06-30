build it:
``` sudo docker build  -t "alibhji/ubuntu16-miniconda-cuda:9.0" . ```

Run:
``` sudo nvidia-docker run -it alibhji/ubuntu16-miniconda-cuda:9.0 bash``` 

To mount a directory

``` nvidia-docker run -it -v /home/mjamali/proj/OFT_3_2020/data/kitti/:/testenv/KITTI ubuntu16-miniconda-cuda:9.0 bash``` 

