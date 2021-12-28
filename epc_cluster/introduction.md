# 操作指南
## Step1.算例数据
以Lammps软件为例:
```
# 3d Lennard-Jones melt

variable        x index 20
variable        y index 20
variable        z index 10

variable        xx equal 20*$x
variable        yy equal 20*$y
variable        zz equal 20*$z

units           lj
atom_style      atomic

lattice         fcc 0.8442
region          box block 0 ${xx} 0 ${yy} 0 ${zz}
create_box      1 box
create_atoms    1 box
mass            1 1.0

velocity        all create 1.44 87287 loop geom

pair_style      lj/cut 2.5
pair_coeff      1 1 1.0 1.0 2.5

neighbor        0.3 bin
neigh_modify    delay 0 every 20 check no

fix             1 all nve

thermo          2
timestep        0.01

run             10
```

## Step2.创建任务
![](/images/cat1.png)
![](/images/cat2.png)

## Step3.上传项目数据

![](/images/upload1.png)
![](/images/upload2.png)

## Step4.启动任务
![](/images/run1.png)
![](/images/run2-1.5.png)

## Step5.监控任务与下载结果
![](/images/get1.png)
![](/images/get2.png)
![](/images/get3.png)
