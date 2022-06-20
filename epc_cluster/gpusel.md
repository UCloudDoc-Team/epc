# 促销GPU使用TIPS
## 登录界面
https://www.ucloud.cn/site/active/gpu.html
![](/images/GPUSelling.png)


## 选择机型
![](/images/GPUUniverse.png)

## 购买并选择是否自动挂载共享存储
![](/images/GpuSellOptions.png)

## 去GPU云主机控制台查看新建的机型(记得切换到正确的可用区)
https://console.ucloud.cn/uhost/uhost?hpc=false
![](/images/CreateGPUSuccess.png)
#### 选择你创建机器所属的可用区，例如：上海2C
![](/images/AZ.png)

## 去UFS控制台查看新建的共享存储（如果你有附加购买的话）
https://console.ucloud.cn/ufs/ufs
![](/images/UFS.png)

## 登录机器 （ubuntu系统用户名为ubuntu）

### CUDA驱动已预装
![](/images/NV.png)

### 可以直接使用AI框架：pytorch / tensorflow
![](/images/AI.png)

### 如果选择挂载UFS，发现共享存储已自动挂载（到/home/ubuntu）
![](/images/MOUNT.png)
