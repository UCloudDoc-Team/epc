# GROMACS使用参考样例

## 创建任务

![](/images/gromacs/create.png)

## 上传项目数据
参考算例:
[算例](/images/gromacs/gromacs_water.tgz)


![](/images/gromacs/2.png)

![](/images/gromacs/3.png)

## 运行软件

### 命令行方式

![](/images/gromacs/4.png)

```
tar -xzvf gromacs_water.tgz
cd gromacs_water/1536
gmx_mpi grompp -f pme.mdp -c conf.gro -p topol.top -o water_pme.tpr
mpirun -np ${TOTAL_NPROC} gmx_mpi mdrun -v -ntomp 1 -nsteps 5000 -pin on -s water_pme.tpr
```

TIPS:
```
1.先使用tar命令解压缩项目数据；然后cd到需要执行的目录下
2.grompp 命令是gromacs软件中自带的命令，执行时需要前面添加 _apprun_ 切换至软件运行环境下执行，否则会找不到需要运行的软件
3.grompp -f pme.mdp -c conf.gro -p topol.top -o water_pme.tpr 命令为数据预处理命令，不需要mpirun并行
4.${TOTAL_NPROC} 是一个内建变量，可以获取到创建任务时指定的核数
5.mpirun是并行计算启动命令，当前使用的mpi软件类型是openmpi-4.1.1版本；-np表示需要多少进程同时运行；其他参数请查阅openmpi相关文档获取
```

### 脚本方式
如果觉得每次提交都需要输入一长串的命令行参数太过麻烦，可以保存为脚本文件，这样选择脚本文件执行即可
![](/images/gromacs/5.png)

![](/images/gromacs/6.png)

TIPS:
```
1.目前脚本文件类型可以支持python2、bash、sh、perl
2.任务执行路径默认在项目数据所在根目录，可以通过cd命令进行切换目录
```

## 查看任务
![](/images/gromacs/7.png)

![](/images/gromacs/8.png)

![](/images/gromacs/9.png)
