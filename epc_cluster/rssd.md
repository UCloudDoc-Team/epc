# EPC单机挂载UHOST高速云盘
EPC计算节点有优越的单机CPU性能，UHOST附带的RSSD云盘提供高速带宽，what if我的计算需求同时包含两者？

| 机型/性能 | 计算 | 存储 |
|---|  ---  | ----  |
| EPC单机 | MAX: AMDZen2 - 240C跨NUMA/128C单NUMA| SSD云盘（系统盘）/ RSSD+远程协议（共享存储）[百MBs级] |
| UHOST | MAX: 96C  | RSSD高速云盘直连（跟容量相关，可达TBs级） |

ANSWER：创建EPC用作计算，创建UHOST+RSSD用作存储，两者通过NFS关联，带宽损耗~<20%

| 机型/性能 | 计算 | 存储 |
|---|  ---  | ----  |
| EPC单机 | 创建EPC单机 | -<NFS CLIENT挂载>- |
| UHOST | -<开启NFS SERVER>- | 创建UHOST+RSSD-核数超过IO瓶颈即可 |

## STEP1：创建EPC计算节点
PS：先进入EPC控制台：https://console.ucloud.cn/uhost/uhost?hpc=true
![](/images/ultra/CATEPC.png)

## STEP2: 创建UHOST+RSSD（
![](/images/ultra/CATUHOST2.png)


### HINTS
| ID | HINT |
|---|  ---  |
| 1 | 请在上海2A创建，因为EPC在上海2A，为了高速互通和低延迟保持同地域） |
| 2 | 磁盘读写的瓶颈有：IO/CPU，例如我需要4TB的磁盘，为了2TBs的原生带宽，至少创建8核的机器，以保证CPU不成为磁盘瓶颈|

## STEP3：进入UHOST开启NFS服务器 - 以CentOS8.3为例
```
yum install nfs-utils
vim /etc/exports
#输入：/data 10.23.0.0/16(rw,no_root_squash)
#注：10.23.0.0属于你名下UHOST和EPC机器互通的内网IP段，根据自己的VPC IP段设置
systemctl start nfs-server.service
```

## STEP4: 进入EPC挂载NFS
```
yum install nfs-utils
mkdir -p /mnt(或自定义挂载目录)
mount -t nfs 10.23.x.x(UHOST的内网IP):/data /mnt
df -h #检查挂载结果
```

## STEP5: benchmark
测试软件：FIO

标准测试：https://docs.ucloud.cn/udisk/introduction/performance/rssd

### HINT
分别benchmark：UHOST本地的RSSD数据盘，和EPC通过NFS挂载UHOST-RSSD的挂载点

说白了区别就是：一个在UHOST执行fio，目标目录是数据盘/data，一个在EPC执行fio，目标目录是挂载点/mnt（或者你自己定义的挂载目录）

| benchmark | command |
|---|  ---  |
| UHOST-LOCAL | ```fio -direct=1 -iodepth=1 -rw=read -ioengine=libaio -bs=256k -size=3G -numjobs=8 -runtime=1000 -group_reporting -name=test -filename=/data/demofile``` |
| EPC-NFS | ```fio -direct=1 -iodepth=1 -rw=read -ioengine=libaio -bs=256k -size=3G -numjobs=8 -runtime=1000 -group_reporting -name=test -filename=/mnt/demofile```|

RESULT:
### UHOST本地~2.2GBs
![](/images/ultra/RET1.png)
### EPC挂载~1.8GBs
![](/images/ultra/RET2.png)
