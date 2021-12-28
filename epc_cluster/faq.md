# 常见问题
## 文件管理
### 上传数据
![](/images/upload1.png)
![](/images/upload2.png)

### 下载数据
![](/images/get1.png)
![](/images/get2.png)
![](/images/get3.png)

## 自制镜像
软件列表没有我想要的软件或软件版本？
epc cluster提供自制镜像(singularity)能力，如需自制镜像：联系我们上传您的singularity文件，并指定此文件(xx.sif)想要显示的软件和版本，然后此文件表示的镜像将新增在上方软件和版本选择中

## 拼写命令
### 简单版
点击启动按钮后，出现命令输入框，输入框里有给出命令的模板，根据模板补全其中的问号（？？）部分，即可拼写出该软件的典型命令。
![](/images/run3-1.5.png)
例如:

```shell
#软件给出
lmp_mpi < ./??
#用户补全为
lmp_mpi < ./inano.lj
```
在用户正确上传inano.lj(如图)的前提下，任务运行成功

![](/images/run4.png)

注：命令模板只是对初次上手的提示，不是所有命令都能通过填充问号部分(？？)就能得到，熟悉的用户可以删掉提示并完全填写自己的指令，例如：如果上图中文件inano.lj位于目录fightzone内，则命令行可以是：

```shell
## 进入输入文件所在目录
cd fightzone
## 对应lammps软件，指定输入文件可以用<，也可以用-i
lmp_mpi -i ./inano.lj
```

> 还是有疑问？[完整的指令拼写](#howtorun_detail)
> 成功的任务（可从"项目数据"下载输出文件）：
> ![](/images/run5.png)


### 详细版
无需关注与命令无关的srun/slurm/singularity指令，仅（如果需要用mpirun运行时）填写mpirun和运行任务本身的指令即可。以Gromacs软件为例：

#### 在裸机上运行的命令输入

```shell
#!/bin/bash
#SBATCH --partition=compute
#SBATCH -N 2
#SBATCH --job-name=gromacs_demo
#SBATCH --output=jobs/gmx-%j.out
#SBATCH --error=jobs/gmx-%j.err
#SBATCH --ntasks-per-node=32

export OMPI_ALLOW_RUN_AS_ROOT=1
export OMPI_ALLOW_RUN_AS_ROOT_CONFIRM=1

cd gromacs_water/1536
#预处理
singularity exec -H `pwd` /gv_images_production/public/gromacs/2021.4/gromacs.sif gmx_mpi grompp -f pme.mdp -c conf.gro -p topol.top -o water_pme.tpr
#正式模拟
srun mpirun -np 64 singularity exec -H `pwd` /gv_images_production/public/gromacs/2021.4/gromacs.sif gmx_mpi mdrun -v -ntomp 1 -nsteps 5000 -pin on -s water_pme.tpr
```

#### 对应在epc cluster平台输入命令

```shell
cd gromacs_water/1536
gmx_mpi grompp -f pme.mdp -c conf.gro -p topol.top -o water_pme.tpr
mpirun -np 64 gmx_mpi mdrun -v -ntomp 1 -nsteps 5000 -pin on -s water_pme.tpr
```
环境变量`${TOTAL_NPROC}`可代替当前任务的配置核数，例如:如果当前任务配置是64核心，则`${TOTAL_NPROC}`=64。因此上述命令可改为：
```shell
cd gromacs_water/1536
gmx_mpi grompp -f pme.mdp -c conf.gro -p topol.top -o water_pme.tpr
mpirun -np ${TOTAL_NPROC} gmx_mpi mdrun -v -ntomp 1 -nsteps 5000 -pin on -s water_pme.tpr
```

#### 总结

| 指令序号| srun | openmpi | singularity | 用户指令 |
|---|  ---  | ----  | --- | --- |
| | 省略|用户可选 | 省略|用户填写 |
|指令1| \ | \ |singularity exec -H `pwd` {镜像目录}/gromacs.sif | gmx_mpi grompp -f pme.mdp -c conf.gro -p topol.top -o water_pme.tpr|
|指令2| srun |mpirun -np 64 或 mpirun -np ${TOTAL_NPROC} |singularity exec -H `pwd` {镜像目录}/gromacs.sif| gmx_mpi mdrun -v -ntomp 1 -nsteps 5000 -pin on -s water_pme.tpr |
