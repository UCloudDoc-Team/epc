# VASP

软件官网：[www.vasp.at]

你说的那种错误确实会出现，原因是用的makefile是intel arch的， 有一个参数 -xHOST ，这个参数配置在AMD CPU机器会出异常， AMD 机器上有替换参数，我们HPC 上AMD 平台支持的最好的是-march=core-avx2。  也普中把makfile.include 文件里的 -xHOST, 替换成 -march=core-avx2
