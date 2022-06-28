# Webssh及批处理操作指南

EPC Cluster集群任务支持webssh和批处理以及图形化界面（部分软件支持）三种操作方式，本篇主要介绍webssh和批处理的操作。


## 项目数据目录结构

![](/images/webssh/datadirectory.png)

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


## 通过批处理访问处理后的数据/正式运行
### 创建集群任务（您可以选择我们平台上已支持的软件，此处以openFOAM为例）
![](/images/webssh/CATOF.png)
### 以批处理方式运行
![](/images/webssh/RUNOF.png)
### 查看结果，发现成功读取
![](/images/webssh/RET.png)

?> 不同任务的关联数据也可以直接放在父级目录交互，epc-task目录只是方便用户结构化和区分同名数据做的默认设置。

?> 如果您对运行出任务结果不满意，或者需要再次运行，我们提供同任务重试的功能。

符合条件（任务运行过且未在运行中，例如已撤销/已完成）的任务可以RERUN，再次进入任务提交窗口。
![](/images/webssh/RERUN.png)
![](/images/webssh/RUNOF.png)
