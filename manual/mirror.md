# 镜像的使用 #

在首次配置好 EPC 之后（例如 OpenFOAM 软件安装完成并确认可运行），在 run case 之前，强烈建议制作系统镜像，随后可以直接用制作的镜像创建 EPC 主机。

##### 务必将所有关键软件（如 OpenFOAM）安装到系统盘，不建议在数据盘（例如 Windows 的 D 盘、Linux 的/data） 安装任何关键软件，否则将无法打包在镜像之中。 

## 打包系统镜像 ## 

1. 全部产品—云极高性能计算 EPC

2. 选择集群，点击【详情】，选择要制作镜像的计算节点
3. 更多操作—制作镜像

![](../../epc/images/mirror.png)

## 使用系统镜像启动新主机 ## 

1. 全部产品—云极高性能计算 EPC-独占集群

2. 点击【创建】 ，选择节点组，选择要使用的自制镜像（例如刚刚制作的 OpenFOAM），选择配置后，即可使用镜像购买新EPC节点。

![mirror1](../../epc/images/mirror1.png)



