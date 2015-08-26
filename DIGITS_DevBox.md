# DIGITS_DevBox


## DIGITS软件要求
[Prerequisites](https://github.com/NVIDIA/DIGITS)

- NVIDIA的驱动版本必须是346或更高版本

- CUDA toolkit (>= 6.5) 

- cnDNN

- Caffe

- graphviz (网络结构可视化)

                > sudo apt-get install graphviz
                
## DIGITS v2.0.0-rc for Ubuntu 14.04

1. 下载安装包digits-2.0.0-rc.tar.gz在http://developer.nvidia.com/digits

2. 解压

                > tar xvf digits-2.0.0-rc.tar.gz

3. 进入解压目录digits-2.0，运行安装脚本

                > cd digits-2.0
                > ./install.sh
                
    在终端安装过程中，可能出现`无法下载 http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources Hash 校验和不符`的情况。如图
    
    打开Ubuntu软件中心，点击左上角`编辑--软件源`，在`其他软件`中，取消`独立`和`独立(源代码)`。如图
    
    完成后，再次运行 ./install.sh
    
4. 运行`runme.sh`启动DIGITS server

                > ./runme.sh
                
     在浏览器中打开http://localhost:5000/来查看DIGITS工具。如图
                

# Caffe 问题

- 在安装过程中，必须根据CUDA版本选择NVIDIA驱动版本，例如CUDA7.0对应的版本应该是NVIDIA346版，不要总是安装最新版本的NVIDIA驱动，例如安装了最新的355版本后，可能显示`no CUDA-capable device is detected` 

- libmkl_rt.so: cannot open shared object file: No such file or directory

        1.在/etc/ld.so.conf.d 添加MKL库路径/opt/intel/mkl/lib/intel64，sudo ldconfig（推荐使用）
        2. export LD_LIBARY_PATH=/opt/intel/mkl/lib/intel64:$LD_LIBARY_PATH，sudo ldconfig
        3. ln -s /opt/intel/mkl/lib/intel64/*.so /usr/lib，sudo ldconfig
        
- libcudart.so.7.0: cannot open shared object file

    在.bashrc中加入export PATH=$PATH:/usr/local/cuda-7.0/bin
    export LD_LIBRARY_PATH=$LD_LIBARY_PATH:/usr/local/cuda-7.0/lib64
    
- 目前（2015.08.26）
    
## NVIDIA工具

**NVIDIA官网中很多程序或工具都是需要注册后才可下载的。**

### cuDNN

[cuDNN](http://devblogs.nvidia.com/parallelforall/accelerate-machine-learning-cudnn-deep-neural-network-library/)， CUDA Deep Neural Network library，是专门针对Deep Learning框架设计的一套GPU计算加速方案，使工作者投入与设计和训练神经网络模型，而不用在底层的表现上话费时间。目前支持的DL工具包括caffe，Theano和Torch等。

cuDNN的Realease版本有cuDNN v1，cuDNN v2和cuDNN v3.

-  Download cuDNN v3 Release Candidate (August 4, 2015), for CUDA 7.0 and later.

- Download cuDNN v2 (March 17,2015), for CUDA 6.5 and later.

- Download cuDNN v1 (cuDNN 6.5 R1)

cuDNN特点：

- 

### CUDA

## RAID

1.格式化硬盘 sudo mkfs.ext4 /dev/sdX，显示
 /dev/sdX is apparently in use by the system; will not make a filesystem here!
 
                > sudo dmsetup status
                > dmsetup remove_all
                > dmsetup status
                        No devices found
                > sudo mkfs.ext4 /dev/sdX
    