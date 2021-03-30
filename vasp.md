# VASP

软件官网：[www.vasp.at]

## 安装步骤

1. 安装依赖包

```
yum -y install cmake pkgconfig
yum groupinstall "Development Tools"
```
2. 运行BaseKit与HpcKit脚本

```
wget https://registrationcenter-download.intel.com/akdlm/irc_nas/17226/l_BaseKit_b_2021.1.10.2261.sh
chmod +x l_BaseKit_b_2021.1.10.2261.sh
./l_BaseKit_b_2021.1.10.2261.sh
wget https://registrationcenter-download.intel.com/akdlm/irc_nas/17229/l_HPCKit_b_2021.1.10.2477_offline.sh 
chmod +x l_HPCKit_b_2021.1.10.2477_offline.sh 
./l_HPCKit_b_2021.1.10.2477_offline.sh 
```

3. [注册](https://www.vasp.at/registration_form/)并下载vasp
 
4. 编译vasp（以6.1.0版本举例）

```
cd vasp.6.1.0
cp arch/makefile.include.linux_intel makefile.include
echo \$MKLROOT=$MKLROOT >> makefile.include
vi makefile.include
```

此处将`makefile.include`文件中的`-xHOST`替换为`-march=core-avx2`，并保存

?> 参数调整的原因为：-xHost为Intel平台的推荐参数，而EPC计算节点则接使用AMD平台的CPU，需要使用-march=core-avx2参数进行编译，不然会致使编译错误

```
make all
```
