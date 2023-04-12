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

请参照链接1进行安装，使用依次下载NVIDIA驱动、CUDA、cudnn，国内即可在官网上快速下载cuda和cudnn，下载cudnn需要注册Nvidia账号。注意版本匹配问题，推荐全部下载本地安装文件，NVIDIA驱动和CUDA为`.run`文件，cudnn为`.tar`文件。

### 1. 禁用nouveau并重启
```bash
lsmod | grep nouveau
#没有lsmod就安装
apt install module-init-tools

sudo vim /etc/modprobe.d/blacklist.conf
```
在打开的文本最后加上：
```
blacklist nouveau
options nouveau modeset=0
```
然后更新并重启：
```bash
sudo update-initramfs -u
reboot
```

### 2. 安装依赖（gcc）
```bash
sudo apt install build-essential
```

### 3. 删除旧的NVIDIA驱动
```bash
sudo apt-get remove nvidia-*
sudo apt-get autoremove
```

### 4. 安装
```bash
# 安装显卡驱动
sudo bash NVIDIA-Linux-x86_64-470.182.03.run

#安装CUDA
sudo bash cuda_11.3.1_465.19.01_linux.run
# 为CUDA建立软链接
sudo ln -s /usr/local/cuda-11.3 /usr/local/cuda

#安装cudnn
# 解压cudnn，生成cuda文件夹
tar -xvf cudnn-linux-x86_64-8.8.1.3_cuda11-archive.tar
#将cuda文件夹内的文件复制到/usr/local/cuda/中
sudo cp cuda/include/* /usr/local/cuda/include/
sudo cp cuda/lib64/* /usr/local/cuda/lib64/

```

### 5. 配置环境变量
```bash
sudo vim /etc/profile
```
在文件后面增加以下内容：
```
export PATH=/usr/local/cuda-10.1/bin:$PATH
export LD_LIBRARY_PATH=/usr/lcoal/cuda-10.1/lib64:$LD_LIBRARY_PATH
```
保存并退出。

> **注意**：第一个教程中配置环境变量路径有误，不应该加引号。  
**技巧**：推荐使用软链接的方法配置环境路径，方便后续切换CUDA版本。  
**技巧**：环境变量可以不添加到`~/.bashrc`下，而是添加到`/etc/profile`下，前者是用户变量，后者是全局变量。  
**技巧**：修改完环境变量后，需要使用`source /etc/profile`激活更改，或者重新登录shell。

### 双CUDA
[ubuntu 安装多个CUDA版本并可以随时切换](https://blog.csdn.net/yinxingtianxia/article/details/80462892)

```shell
# 查看cuda版本
nvcc -V
```

## 安装第二个CUDA 10.0
```shell
sudo ./cuda_10.0.130_410.48_linux.run
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

建立软链接：
```shell
sudo rm -rf cuda
sudo ln -s /usr/local/cuda-10.0 /usr/local/cuda
```

## 卸载显卡驱动
```shell
# 两种卸载方式
# 使用本地安装包安装的驱动使用这种方式
sudo /usr/bin/nvidia-uninstall

# 使用apt安装的驱动使用这种方式
sudo apt --purge remove nvidia*
sudo apt autoremove
```

## 重装显卡驱动出错
### 报错一：
```
An NVIDIA kernel module ‘nvidia-drm‘ appears to already be loaded in your kernel...
```
进入tty界面：
<kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>F1~F12</kbd>

```shell

sudo systemctl isolate multi-user.target

# 卸载内核模块
sudo modprobe -r nvidia-drm

# 重装显卡驱动
sudo ./NVIDIA-Linux-x86_64-XXXXXXX.run

# 重装完成后，可以使用nvidia-smi查看是否正常安装

# 默认使用图形界面启动
sudo systemctl set-default graphical.target

# 重启
sudo reboot
```
### 报错二：
```
The CC version check failed
The kernel was built with gcc version XXX, but the current compiler version is cc XXX...
```
用`sudo /usr/bin/nvidia-uninstall`命令卸载显卡驱动，然后重装。