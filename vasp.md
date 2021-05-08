# VASP

软件官网：\[[www.vasp.at](http://www.vasp.at)\]

## 安装步骤

1. 安装依赖包

```bash
yum -y install cmake pkgconfig
yum groupinstall "Development Tools"
yum install numactl-libs  numactl-devel  pandoc
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

4. 安装ucx

```bash
    git clone https://github.com/openucx/ucx.git ucx
    cd ucx
    ./autogen.sh
    mkdir build
    cd build
    ../configure --prefix=/opt/ucx
    make && make install
```

5. OpenMPI and OpenSHMEM  编译安装

```bash
	git clone https://github.com/open-mpi/ompi.git
	cd ompi
	./autogen.pl
	mkdir build
	cd build
	../configure --prefix=/opt/ompi --with-ucx=/opt/ucx
	make && make install
```

6. [注册](https://www.vasp.at/registration_form/)并下载vasp

7. 编译vasp（以6.1.0版本举例）

```bash
source /opt/intel/oneapi/setvars.sh
cd vasp.6.1.0
将本文档最下方的 makefile.include内容在此目录下保存到此目录下，保存文件名为：makefile.include

make all
```

8. 运行vasp：
```bash
   /opt/ompi/bin/mpirun -np 32 --oversubscribe --mca pml ucx --mca btl ^uct -x UCX_NET_DEVICES=mlx5_0:1 --allow-run-as-root  /{your_vasp_path}/vasp.6.1.0/bin/vasp_std
```

9. 附录（makefile.include）
```bash
# Precompiler options
CPP_OPTIONS= -DHOST=\"LinuxIFC\"\
             -DMPI -DMPI_BLOCK=8000 -Duse_collective \
             -DscaLAPACK \
             -DCACHE_SIZE=4000 \
             -Davoidalloc \
             -Dvasp6 \
             -Duse_bse_te \
             -Dtbdyn \
             -Dfock_dblbuf
CPP        = fpp -f_com=no -free -w0  $*$(FUFFIX) $*$(SUFFIX) $(CPP_OPTIONS)
FC         = mpiifort
FCL        = mpiifort -mkl=sequential
FREE       = -free -names lowercase
#FFLAGS     = -assume byterecl -w -xHOST
FFLAGS     = -assume byterecl -w -march=core-avx2
OFLAG      = -O2
OFLAG_IN   = $(OFLAG)
DEBUG      = -O0
MKLROOT    = /opt/intel/oneapi/mkl/latest
MKL_PATH   = $(MKLROOT)/lib/intel64
BLAS       =
LAPACK     =
BLACS      = -lmkl_blacs_intelmpi_lp64
SCALAPACK  = $(MKL_PATH)/libmkl_scalapack_lp64.a $(BLACS)
OBJECTS    = fftmpiw.o fftmpi_map.o fft3dlib.o fftw3d.o
INCS       =-I$(MKLROOT)/include/fftw
LLIBS      = $(SCALAPACK) $(LAPACK) $(BLAS)
OBJECTS_O1 += fftw3d.o fftmpi.o fftmpiw.o
OBJECTS_O2 += fft3dlib.o
# For what used to be vasp.5.lib
CPP_LIB    = $(CPP)
FC_LIB     = $(FC)
CC_LIB     = icc
CFLAGS_LIB = -O
FFLAGS_LIB = -O1
FREE_LIB   = $(FREE)

OBJECTS_LIB= linpack_double.o getshmem.o

# For the parser library
CXX_PARS   = icpc
LLIBS      += -lstdc++

# Normally no need to change this
SRCDIR     = ../../src
BINDIR     = ../../bin

#================================================
# GPU Stuff

CPP_GPU    = -DCUDA_GPU -DRPROMU_CPROJ_OVERLAP -DUSE_PINNED_MEMORY -DCUFFT_MIN=28 -UscaLAPACK -Ufock_dblbuf

OBJECTS_GPU= fftmpiw.o fftmpi_map.o fft3dlib.o fftw3d_gpu.o fftmpiw_gpu.o

CC         = icc
CXX        = icpc
CFLAGS     = -fPIC -DADD_ -Wall -qopenmp -DMAGMA_WITH_MKL -DMAGMA_SETAFFINITY -DGPUSHMEM=300 -DHAVE_CUBLAS

CUDA_ROOT  ?= /usr/local/cuda/
NVCC       := $(CUDA_ROOT)/bin/nvcc -ccbin=icc
CUDA_LIB   := -L$(CUDA_ROOT)/lib64 -lnvToolsExt -lcudart -lcuda -lcufft -lcublas

GENCODE_ARCH    := -gencode=arch=compute_30,code=\"sm_30,compute_30\" \
                   -gencode=arch=compute_35,code=\"sm_35,compute_35\" \
                   -gencode=arch=compute_60,code=\"sm_60,compute_60\" \
                   -gencode=arch=compute_70,code=\"sm_70,compute_70\" \
                   -gencode=arch=compute_72,code=\"sm_72,compute_72\"

MPI_INC    = $(I_MPI_ROOT)/include64/
```
