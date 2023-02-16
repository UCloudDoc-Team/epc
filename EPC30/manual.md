# 独占集群操作指南

以GROMACS为例，演示EPC独占集群的使用流程。

## 创建独占集群

![image](/images/EPC3.0/epc3.0_create1.png)

选择节点配置，然后点击【立即运行】。

![image](/images/EPC3.0/epc3.0_create2.png)
![image](/images/EPC3.0/epc3.0_create2_2.png)
![image](/images/EPC3.0/epc3.0_create2_3.png)

创建集群后，集群及节点状态如下:

![image](/images/EPC3.0/epc3.0_create3.png)

## 登录集群

### 方式一：客户端SSH登录

点击可以查看资源详情；

![image](/images/EPC3.0/login_01.png)

从登录节点资源详情复制外网登录IP；

![image](/images/EPC3.0/login_02.png)

用终端登录集群，如果是Windows终端，可以使用putty或xshell的工具。

查看集群(SLURM)状态:

![image](/images/EPC3.0/login_03.png)

进入算例目录(共享存储的路径)，使用作业脚本提交一个节点、32核的作业，作业脚本名称为water.slurm。

![image](/images/EPC3.0/login_04.png)

以GROMACS水分子作业脚本为例：

```
#!/bin/bash
#SBATCH --job-name gromacs_test
#SBATCH --nodes=1
#SBATCH --ntasks-per-node=32
#SBATCH --cpus-per-task=1
#SBATCH -o %j.out
#SBATCH -e %j.err
 
module purge
module load gromacs/2020.3-single
 
export OMP_NUM_THREADS=$SLURM_CPUS_PER_TASK
gmx_mpi grompp -f pme.mdp -c conf.gro -p topol.top -o water_pme.tpr
mpirun -np $SLURM_NPROCS gmx_mpi mdrun -v -ntomp 1 -nsteps 10000 -pin on -s water_pme.tpr
```
参数解释：

```
--job-name            ##作业名
--nodes=1             ##申请节点数量
--ntasks-per-node=32  ##每个节点的任务数，默认每个任务一个核
--cpus-per-task=1     ##每个任务需要的核心数
--output %j.out       ##输出结果STDOUT保存文件
--error %j.err        ##报错结果STDERR保存文件
```
### 方式二：控制台GUI登录方式
点击节点直连

![image](/images/EPC3.0/login_11.png)

输入用户认证密码:

![image](/images/EPC3.0/login_12.png)

分子可视化操作

右键选择“Open Terminal Here”，打开终端，在终端里面输入vmd，加载分子。

![image](/images/EPC3.0/login_13.png)

备注：可根据桌面大小设置屏幕分辨率。

![image](/images/EPC3.0/login_14.png)

## 集群文件上传和下载
### FTP上传下载
**适用于Windows、macOS、Linux 操作系统**

通过 FTP 上传下载，在“超算存储”点击【详情】

![image](/images/EPC3.0/upload_01.png)

按照如图提供的用户名、密码、地址和端口号信息，使用 FTP 客户端(Filezilla)登陆。

![image](/images/EPC3.0/upload_02.png)

### SCP上传下载
**适用于Windows、macOS、Linux 操作系统**

从登录节点资源详情复制外网登录IP

![image](/images/EPC3.0/upload_11.png)

复制本地目录到集群，在命令行界面输入

```
$ scp -r local_folder root@113.31.xx.xx:remote_folder
```
### WinSCP上传下载(Windows)

**适用于Windows操作系统**

打开WinSCP，输入主机名、SSH用户、密码，点击登录。

![image](/images/EPC3.0/upload_12.png)

复制本地目录到集群，把左边的目录拖移到右边即可。

![image](/images/EPC3.0/upload_13.png)









