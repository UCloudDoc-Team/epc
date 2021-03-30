# VASP

软件官网：[www.vasp.at]

## 安装步骤

1. 安装依赖包与

```
yum -y install cmake pkgconfig
yum groupinstall "Development Tools"

wget https://registrationcenter-download.intel.com/akdlm/irc_nas/17226/l_BaseKit_b_2021.1.10.2261.sh
chmod +x l_BaseKit_b_2021.1.10.2261.sh
./l_BaseKit_b_2021.1.10.2261.sh

wget https://registrationcenter-download.intel.com/akdlm/irc_nas/17229/l_HPCKit_b_2021.1.10.2477_offline.sh 
chmod +x l_HPCKit_b_2021.1.10.2477_offline.sh 
./l_HPCKit_b_2021.1.10.2477_offline.sh 
```

2. 注册下载vasp
3. 编译vasp（以6.1.0版本举例）
```
cd vasp.6.1.0
cp arch/makefile.include.linux_intel makefile.include
echo \$MKLROOT=$MKLROOT >> makefile.include

```

你说的那种错误确实会出现，原因是用的makefile是intel arch的， 有一个参数 -xHOST ，这个参数配置在AMD CPU机器会出异常， AMD 机器上有替换参数，我们HPC 上AMD 平台支持的最好的是-march=core-avx2。  也普中把makfile.include 文件里的 -xHOST, 替换成 -march=core-avx2
