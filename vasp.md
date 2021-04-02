# VASP

软件官网：\[[www.vasp.at](http://www.vasp.at)\]

## 安装步骤

1. 安装依赖包

```bash
yum -y install cmake pkgconfig
yum groupinstall "Development Tools"
```

2. 下载Intel oneAPI base toolkit并安装([Intel oneAPI](https://software.intel.com/content/www/us/en/develop/tools/oneapi.html))

```bash
wget https://registrationcenter-download.intel.com/akdlm/irc_nas/17226/l_BaseKit_b_2021.1.10.2261.sh
chmod +x l_BaseKit_b_2021.1.10.2261.sh
./l_BaseKit_b_2021.1.10.2261.sh
```

3. 下载Intel HpcKit并安装

```bash
wget https://registrationcenter-download.intel.com/akdlm/irc_nas/17229/l_HPCKit_b_2021.1.10.2477_offline.sh 
chmod +x l_HPCKit_b_2021.1.10.2477_offline.sh 
./l_HPCKit_b_2021.1.10.2477_offline.sh 
```

4. [注册](https://www.vasp.at/registration_form/)并下载vasp

5. 编译vasp（以6.1.0版本举例）

```bash
cd vasp.6.1.0
cp arch/makefile.include.linux_intel makefile.include
echo \$MKLROOT=$MKLROOT >> makefile.include
vi makefile.include
```

此处将`makefile.include`文件中的`-xHOST`替换为`-march=core-avx2`，并保存

?> 参数调整的原因为：-xHost为Intel平台的推荐参数，而EPC计算节点则为AMD平台的CPU，可以通过使用-march=core-avx2参数，编译出使用高级向量扩展指令的目标程序。如果不替换-xHost，则会导致编译错误

```bash
source /opt/intel/oneapi/setvars.sh
make all
```

