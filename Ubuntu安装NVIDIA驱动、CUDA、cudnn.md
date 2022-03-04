# **Ubuntu安装NVIDIA驱动、CUDA、cudnn**
*主页：https://github.com/wjxpro*

*邮箱：804359553@qq.com*

[TOC]

## 安装NVIDIA驱动、CUDA、cudnn
![nvidia-logo](img/nvidia_logo_horizontal.png)

+ [Ubuntu18.04下安装Nvidia驱动和CUDA10.1＋CUDNN](https://blog.csdn.net/BigData_Mining/article/details/99670642)
+ [NVIDIA CUDA Installation Guide for Linux](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#runfile-overview)
+ [cuda官网下载地址](https://developer.nvidia.com/cuda-toolkit-archive)
+ [cudnn官网下载地址](https://developer.nvidia.com/rdp/cudnn-archive)

> **注意**：第一个教程中配置环境变量路径有误，不应该加引号。  
**说明**：国内即可在官网上快速下载cuda和cudnn，下载cudnn需要注册Nvidia账号。
**技巧**：推荐使用软链接的方法配置环境路径，方便后续切换CUDA版本。  
**技巧**：环境变量可以不添加到`~/.bashrc`下，而添加到`/etc/profile`下，前者是用户变量，后者是全局变量。  
**技巧**：修改完环境变量后，需要使用`source /etc/profile`激活更改，或者重新登录shell。

### 双CUDA
[ubuntu 安装多个CUDA版本并可以随时切换](https://blog.csdn.net/yinxingtianxia/article/details/80462892)

```shell
# 查看cuda版本
nvcc --version
```

## CUDA 10.0
```shell
sudo bash cuda_10.0.130_410.48_linux.run
```

```shell
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
```