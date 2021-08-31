# 购买云主机 #

1. 使用 UCloud 账号登录 UCloud 控制台 https://console.ucloud.cn ，如果没有 UCloud 账号，请联系销售人员或技术支持人员帮助申请和认证。

2. 全部产品—云极高性能计算EPC （备注：传输主机可以选择”云主机UHost“ ）

![buy](../../epc/images/buy.png)                                                                                                                 

3. 点击【创建主机】，购买所需的机型，仅需选择镜像、选择配置、输入管理员密码（用于远程登陆使用）

   机型：点击卡片即可

   镜像：UCloud 官方纯净版系统、或者您自己制作的系统镜像（已经部署好 HPC 软件）

   共享存储：同一地域同一项目下的所有资源共享 1000GB 配额，支持热扩容

   Linux系统使用 NFS 存储，购买后挂载到 /172.16.0.XX/NFSSharedFiles 目录，可在命令行输入df命令查看；

   ![buy6](../../epc/images/buy6.png)
   
   Windows系统挂载 SMB 存储：挂载为一个网络盘符，与本地盘使用无异；
   
   ![buy7](../../epc/images/buy7.png)
   
   网络：外网带宽默认 5Mb，可选教育网加速；
   
   增加外网带宽，参考如下链接：[https://docs.ucloud.cn/unet/eip/guide](https://docs.ucloud.cn/unet/eip/guide?id=%e8%b0%83%e6%95%b4ip%e5%b8%a6%e5%ae%bd)

![buy2](../../epc/images/buy2.png)

![](../../epc/images/buy3.png)

![](../../epc/images/buy4.png)

4. 管理设置                                                             

登录用户名：采用默认，Windows 为“Administrator”；Linux 如果选择 CentOS 镜像， 则为“root”；如果选择 Ubuntu 镜像，则为“ubuntu” 。

设置密码：请务必设置强安全性的密码，用于登录主机。

![](../../epc/images/buy5.png)

