# **Ubuntu安装NVIDIA驱动、CUDA、cudnn**
*主页：https://github.com/wjxpro*

*邮箱：804359553@qq.com*

[TOC]

## 安装NVIDIA驱动、CUDA、cudnn
![nvidia-logo](img/nvidia_logo_horizontal.png)

+ [Ubuntu18.04下安装Nvidia驱动和CUDA10.1＋CUDNN](https://blog.csdn.net/BigData_Mining/article/details/99670642)
+ [NVIDIA CUDA Installation Guide for Linux](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#runfile-overview)
+ [CUDA Toolkit 11.0 Update 1 Downloads](https://developer.nvidia.com/cuda-downloads?target_os=Linux)

> **注意**：第一个教程中配置环境变量路径有误，不应该加引号。  
**技巧**：推荐使用软链接的方法配置环境路径，方便后续切换CUDA版本。  
**技巧**：环境变量可以不添加到`~/.bashrc`下，而添加到`/etc/profile`下，前者是用户变量，后者是全局变量。  
**技巧**：修改完环境变量后，需要使用`source /etc/profile`激活更改。

### 双CUDA
[ubuntu 安装多个CUDA版本并可以随时切换](https://blog.csdn.net/yinxingtianxia/article/details/80462892)

## 显卡
```shell
# 查看cuda版本
nvcc --version
```


```shell
(base) viewer@viewer-System-Product-Name:~/Downloads$ sudo bash cuda_10.0.130_410.48_linux.run Logging to /tmp/cuda_install_21621.log
Using more to view the EULA.
End User License Agreement
--------------------------


Preface
-------

The Software License Agreement in Chapter 1 and the Supplement
in Chapter 2 contain license terms and conditions that govern
the use of NVIDIA software. By accepting this agreement, you
agree to comply with all the terms and conditions applicable
to the product(s) included herein.


NVIDIA Driver


Description

This package contains the operating system driver and
fundamental system software components for NVIDIA GPUs.


NVIDIA CUDA Toolkit


Description

The NVIDIA CUDA Toolkit provides command-line and graphical
tools for building, debugging and optimizing the performance
of applications accelerated by NVIDIA GPUs, runtime and math
libraries, and documentation including programming guides,
user manuals, and API references.


Default Install Location of CUDA Toolkit

Windows platform:

%ProgramFiles%\NVIDIA GPU Computing Toolkit\CUDA\v#.#

Linux platform:

Do you accept the previously read EULA?
accept/decline/quit: accept

Install NVIDIA Accelerated Graphics Driver for Linux-x86_64 410.48?
(y)es/(n)o/(q)uit: n

Install the CUDA 10.0 Toolkit?
(y)es/(n)o/(q)uit: y

Enter Toolkit Location
 [ default is /usr/local/cuda-10.0 ]: 

Do you want to install a symbolic link at /usr/local/cuda?
(y)es/(n)o/(q)uit: y

Install the CUDA 10.0 Samples?
(y)es/(n)o/(q)uit: y

Enter CUDA Samples Location
 [ default is /home/viewer ]: 

Installing the CUDA Toolkit in /usr/local/cuda-10.0 ...
Installing the CUDA Samples in /home/viewer ...
Copying samples to /home/viewer/NVIDIA_CUDA-10.0_Samples now...
Finished copying samples.

===========
= Summary =
===========

Driver:   Not Selected
Toolkit:  Installed in /usr/local/cuda-10.0
Samples:  Installed in /home/viewer

Please make sure that
 -   PATH includes /usr/local/cuda-10.0/bin
 -   LD_LIBRARY_PATH includes /usr/local/cuda-10.0/lib64, or, add /usr/local/cuda-10.0/lib64 to /etc/ld.so.conf and run ldconfig as root

To uninstall the CUDA Toolkit, run the uninstall script in /usr/local/cuda-10.0/bin

Please see CUDA_Installation_Guide_Linux.pdf in /usr/local/cuda-10.0/doc/pdf for detailed information on setting up CUDA.

***WARNING: Incomplete installation! This installation did not install the CUDA Driver. A driver of version at least 384.00 is required for CUDA 10.0 functionality to work.
To install the driver using this installer, run the following command, replacing <CudaInstaller> with the name of this run file:
    sudo <CudaInstaller>.run -silent -driver

Logfile is /tmp/cuda_install_21621.log
```

```shell
(base) viewer@viewer-System-Product-Name:~/Downloads$ sudo bash cuda_10.1.105_418.39_linux.run ===========
= Summary =
===========

Driver:   Not Selected
Toolkit:  Installed in /usr/local/cuda-10.1/
Samples:  Installed in /home/viewer/

Please make sure that
 -   PATH includes /usr/local/cuda-10.1/bin
 -   LD_LIBRARY_PATH includes /usr/local/cuda-10.1/lib64, or, add /usr/local/cuda-10.1/lib64 to /etc/ld.so.conf and run ldconfig as root

To uninstall the CUDA Toolkit, run cuda-uninstaller in /usr/local/cuda-10.1/bin

Please see CUDA_Installation_Guide_Linux.pdf in /usr/local/cuda-10.1/doc/pdf for detailed information on setting up CUDA.
***WARNING: Incomplete installation! This installation did not install the CUDA Driver. A driver of version at least 418.00 is required for CUDA 10.1 functionality to work.
To install the driver using this installer, run the following command, replacing <CudaInstaller> with the name of this run file:
    sudo <CudaInstaller>.run --silent --driver

Logfile is /var/log/cuda-installer.log

```