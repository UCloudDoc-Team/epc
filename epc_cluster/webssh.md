# WebSSH & RERUN

初次运行EPC-Cluster任务时，可能因为对数据层次没有明确的画像，导致老是出错，不想上手。what should we do？

## 预设数据拓扑
![](/images/webssh/DIR.jpg)

## 通过WebSSH熟悉目录结构/做解压文件等预处理
### 创建WebSSH镜像任务
![](/images/webssh/CATSSH.png)
### 以webssh方式运行
![](/images/webssh/DOSSH.png)
### 观察目录结构
![](/images/webssh/TREE.png)
### 上传压缩包
![](/images/webssh/UPLOAD.png)
### 在线解压
![](/images/webssh/TAR.png)


## 通过Sbatch访问处理后的数据/正式运行
### 创建OpenFOAM（或其他你希望正式运行的超算镜像）任务
![](/images/webssh/CATOF.png)
### 以sbatch方式运行（此处demo为读取之前解压的数据，正式运行例如以此为输入进行计算等）
![](/images/webssh/RUNOF.png)
### 查看结果，发现成功读取
![](/images/webssh/RET.png)
### PS:不同任务的关联数据也可以直接放在父级目录交互，epc-task目录只是方便用户结构化和区分同名数据做的预设

## 运行不满意？再次运行RERUN！
符合条件（任务运行过且未在运行中，例如已撤销/已完成）的任务可以RERUN，再次进入任务提交窗口
![](/images/webssh/RERUN.png)
![](/images/webssh/RUNOF.png)
