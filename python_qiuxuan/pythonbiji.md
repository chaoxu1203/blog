shutil

import shutil

### 将文件内容拷贝到另一个文件中
shutil.copyfileobj(open('old.txt', 'r'), open('new.txt', 'w'))

### 拷贝文件
shutil.copyfile('old.txt', 'old1.txt')

### 仅拷贝权限。内容、组、用户均不变
shutil.copymode('old.txt', 'old1.txt')

### 复制权限、最后访问时间、最后修改时间
shutil.copystat('old.txt', 'old1.txt')

### 复制一个文件到一个文件或一个目录
shutil.copy('old.txt', 'old2.txt')

### 在copy上的基础上再复制文件最后访问时间与修改时间也复制过来了
shutil.copy2('old.txt', 'old2.txt')

### 把olddir拷贝一份newdir，如果第3个参数是True，则复制目录时将保持文件夹下的符号连接，如果第3个参数是False，则将在复制的目录下生成物理副本来替代符号连接
shutil.copytree('C:/Users/xiaoxinsoso/Desktop/aaa', 'C:/Users/xiaoxinsoso/Desktop/bbb')

### 移动目录或文件
shutil.move('C:/Users/xiaoxinsoso/Desktop/aaa', 'C:/Users/xiaoxinsoso/Desktop/bbb') # 把aaa目录移动到bbb目录下

### 删除一个目录
shutil.rmtree('C:/Users/xiaoxinsoso/Desktop/bbb') # 删除bbb目录

### 进程：

  pool = Pool(processNums)
    for seq in workList:
        pool.apply_async(func=func, args=(seq, *args))
    pool.close()
    pool.join()

main中os.environ["CUDA_VISIBLE_DEVICES"] = gpu_id

### 图片中加边框

cv2.copyMakeBorder(src,top, bottom, left, right ,borderType,value)

### 空字典中添加元素

dict_class_image = {}
if class_file not in dict_class_image.keys():
            dict_class_image[class_file] = []
        dict_class_image[class_file].append(1.0-float(image_score))

### 参数添加：

parser = argparse.ArgumentParser(description="compare epoches",

​                                     formatter_class=argparse.ArgumentDefaultsHelpFormatter)

​    

​    parser.add_argument('--version', type=str, help='verison name')

​    # parser.add_argument('--mode', type=str, help='mode')

​    args = parser.parse_args()

​    version_root = os.path.join('/ssd/510176/ped_filter/ped_train', args.version)

​    args.model_path = os.path.join(version_root, 'antifp_mask_sc2')

### easydict

conf = edict()

conf.work_path = Path('work_space")

conf.work_path.mkdir() if not conf.work_path.is_dir() else None 

conf.model_path = conf.work_path/'4gpu" 



### 列表排序

sorted(sim_list,key = lambda x:x[1],reverse=True) 

### 输出文件名及分数值

os.path.basename(path) + "\tped: {:.4f}  rideall: {:.4f}  other: {:.4f}".format(*score) 