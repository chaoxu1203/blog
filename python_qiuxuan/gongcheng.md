### 添加依赖库

export LD_LIBRARY_PATH=/opt/gtk/lib:$LD_LIBRARY_PATH

### 将文件路径输出到txt中

find /home/zxw/face_recog/result/affine1_img/ -name "*.jpg" >list.txt

### 查看文件数量

find ./ -name "*.jpg" |wc -l

### 压缩及解压

unrar l 1.rar

zip -r filename.zip filesdir
unzip -o 20200827_marked_xiafa8_4_12shipin.zip
unrar x all.rar .
unzip -O CP936 20201023_marked\(wxq_284393\).zip

os.system("./xx.bin xxx.val.txt 1 ")


### 文件数目过多时mv:    

find train2014/ -name "*.jpg" | xargs -i mv {} coco_train2014/
用户名@g5500-p100-19:/ssd/ssd2/zxw_face_classification_2_checked_face_rec/0925_video_hat/01face_new$
cp -r ./online_data_test/online_data_hy_supercolor_low_0915_X2241-FLI_2020-09-15-18-46-30_001/face*/*/* ./online_data_test_tj/online_data_hy_supercolor_low_0915_X2241-FLI_2020-09-15-18-46-30_001/face/
tar -zxvf xxx.tar.gz
ls -lR face |grep .bin.|wc -l
scp:
scp -r /tmp/online_data/ 用户名@IP:/home/zxw/0_c_face_recog/
ssh不用输入密码：ssh-copy-id 用户名@IP
sudo scp -r 用户名@IP:/data/11/frontend_data/ /home/ssd/ssd0/dataset/jfr/train/pytorch_data/jfr_ybo/

### 挂载：

##### windows ->  linux 挂载指令

sudo mount -t cifs -o username=smbwx961750 //10.154.33.11/production_data/原始数据/产品共享HY /home/zxw/gzimages1

##### linux -> linux 挂载指令

改一下41服务器挂载权限  vim /etc/exports  后面加一行/home/xj/ssd124/yolov3/face_pic/caffe_yolo_3outblobs_8974 IP(rw,sync,no_root_squash,no_subtree_check)
sudo service nfs-kernel-server restart
在119服务器下：
sudo mount -t nfs -o fsc IP:/home/xj/ssd124/zcl/wfl_face_data /home/zxw/gzimages2

ldd "/home/cj/face_sdk/VCM_Face/publish/lib/libhw_ips.so"  #动态库依赖

### git

git clone -b personal/c00444240/det_sync_d ssh://git@isource-sh.huawei.com:2222/IPC/VCM_Face.git
git clone git@code-sh.rnd.huawei.com:Face_Ped_Snapshot/ped-antifp.git

git pull
git checkout aux_dataset

ln -s /home/cj/face_sdk/gpusp_face/tools/ ./tools(软连接)
git diff
git log
git pull 
git reset --hard HEAD
git checkout master
git branch

### docker后台运行

cmd='python /home/zxw/face_recog/02_script/embeddings_test_tp.py --images_list /home/zxw/face_recog/result/tpimages/20191017_jfr_list.txt'
echo $cmd
nohup $cmd > log1.log 2>&1 &
tailf log1.log

### 进程查看及杀进程

ps -ef|grep python
kill -9 15729 杀进程
du -d 0 -h /ssd/ssd0/fyd/antifp_test/
杀含某个字段的进程：ps -ef|grep video2img_utils_zsy_2_2.py|grep -v grep|cut -c 9-15|xargs kill -9
杀所有进程ps -ef | grep ^username | cut -c 10-15 | xargs kill -9
ps aux | grep -ie 'python' | awk '{print $2}' | xargs kill -9

### docker:

##### 创建

nvidia-docker run --name qx -v /home/zxw/0_c_face_recog/:/0_c_face_recog -it mrc_sdk_test_docker_cuda8.0_cudnn6.0_ubuntu14.04:mrc_sdk_test_docker --ipc=host bash
nvidia-docker run --name qx4 --ipc host -v /ssd/ssd0/:/ssd0 -v /home/qx/:/qx1/ -it pytorch/mxnet/caffe:cuda-9.0-cudnn7-devel-ubuntu16.04 bash
docker run -it -v /home/xj/ssd124/:/ssd124 -v /ssd/ssd1:/ssd/ssd1 pytorch/mxnet/caffe:cuda-9.0-cudnn7-devel-ubuntu16.04 /bin/bash

##### 转移

docker save -o qx5.tar pytorch/mxnet/caffe:cuda-9.0-cudnn7-devel-ubuntu16.04
tar -zcvf qx5.tar.gz qx5.tar
docker load --input qx5.tar
sudo nvidia-docker image load --input qx5.tar
docker images
nvidia-docker run --name qx4 --ipc host -v /ssd/ssd0/zq_train/:/ssd/ssd0/zq_train -it pytorch/mxnet/caffe:cuda-9.0-cudnn7-devel-ubuntu16.04 bash
打包docker:nvidia-docker save -o qx4.tar pytorch/mxnet/caffe:cuda-9.0-cudnn7-devel-ubuntu16.04
sudo nvidia-docker image load --input qx5.tar
CUDA_VISIBLE_DEVICES=2,3,4,5,6,7 python -m torch.distributed.launch --nproc_per_node=6 train.py -lr 0.8 -w 6



### 克隆外网代码报错：Failed to connect to github.com port 443: Timed out

```
git config --global https.proxy    https://域账号:密码@proxycn2.huawei.com:8080
git config --global http.proxy    http://域账号:密码@proxycn2.huawei.com:8080
git config --global http.sslVerify false
```

#### 查看tcp链接情况

netstat -n | awk '/^tcp/ {++S[$NF]} END {for(a in S) print a, S[a]}' 

lsof |wc -l

lsof | grep node |wc -l