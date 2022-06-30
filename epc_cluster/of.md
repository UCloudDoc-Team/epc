# OpenFOAM DEMO

## 创建任务
![](/images/of/0.png)

## 上传项目数据
参考算例：
[算例](https://static.ucloud.cn/docs/epc/images/of/motorBike.tar.gz)

![](/images/of/1.png)

![](/images/of/2.png)

## 运行软件

## 命令行方式
![](/images/of/3.png)

```
tar -xzvf motorBike.tar.gz
cd motorBike
surfaceFeatures
blockMesh
decomposePar -copyZero
mpirun -np 6 snappyHexMesh -overwrite -parallel
mpirun -np 6 potentialFoam -parallel
mpirun -np 6 simpleFoam -parallel
```

### TIPS:

1.先使用tar命令解压缩项目数据；然后cd到需要执行的目录下

2../Allrun-parallel 是一个脚本文件，里面需要用到openfoam中的 blockMesh 等命令，运行前需要添加 _apprun_

3../Allrun-parallel 为预处理命令，不需要mpirun执行

4.${TOTAL_NPROC} 是一个内建变量，可以获取到创建任务时指定的核数

5.mpirun是并行计算启动命令，当前使用的mpi软件类型是openmpi-4.1.1版本；-np表示需要多少进程同时运行；其他参数请查阅openmpi相关文档获取

6.解压目录里面cavityMappingTest/system/decomposeParDict 文件里有个参数（numberOfSubdomains）和运行核数有关，需要在运行前修改，具体使用参考openfoam相关文档

#### cavityMappingTest/system/decomposeParDict
```
/*--------------------------------*- C++ -*----------------------------------*\

| =========                 |                                                 |

| \\      /  F ield         | OpenFOAM: The Open Source CFD Toolbox           |

|  \\    /   O peration     | Version:  v2106                                 |

|   \\  /    A nd           | Website:  www.openfoam.com                      |

|    \\/     M anipulation  |                                                 |

\*---------------------------------------------------------------------------*/

FoamFile

{

    version     2.0;

    format      ascii;

    class       dictionary;

    object      decomposeParDict;

}

// * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * //



numberOfSubdomains  16;



method          scotch;





// ************************************************************************* //

```

## 脚本方式

如果觉得每次提交都需要输入一长串的命令行参数太过麻烦，可以保存为脚本文件，这样选择脚本文件执行即可
![](/images/of/4.png)

![](/images/of/5.png)

### TIPS

1.目前脚本文件类型可以支持python2、bash、sh、perl

2.任务执行路径默认在项目数据所在根目录，可以通过cd命令进行切换目录

## 查看任务

![](/images/of/6.png)

![](/images/of/7.png)

![](/images/of/8.png)
