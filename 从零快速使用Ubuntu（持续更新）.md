# **从零快速使用Ubuntu**
*主页：https://github.com/wjxpro*

*邮箱：804359553@qq.com*

[TOC]

## 前言
<font color='red' size=4><b>一篇好的教程，是提升效率的关键！</b></font>

配置环境的一个重要问题就是版本对应，下载错误的版本会浪费大量时间！

## 〇、Ubuntu入门
### 简介
<a href="https://ubuntu.com/" target="-blank" title="ubuntu 官网">
<img src="img/ubuntu_logo.svg">
</a>
Ubuntu是linux的发行版。LTS意思是长期支持（Long Term Support）。这是基础库的开发者对库的使用者的一个承诺，保证某个版本的库发布之后的很长一段事件之内都得到支持。如果此版本发现一些紧急问题需要修复，那么就会在这个版本上进行更新。通常这些问题的修复都不会导致 API 变化（API 保证长期兼容），所以版本号的前两位是不变的，通常只变化第三位。

### 和Windows的区别
Ubuntu免费，Windows收费。

### 文件系统
详见[Ubuntu文件系统.md](Ubuntu文件系统.md)

## 一、安装系统
详见[Ubuntu系统安装教程.md](Ubuntu系统安装教程.md)

## 二、配置系统及环境
### 1. Root用户与多用户
详见[Ubuntu多用户.md](Ubuntu多用户.md)

### 2. Ubuntu服务器远程使用
详见[Ubuntu服务器远程使用.md](Ubuntu服务器远程使用.md)

### 3. 安装NVIDIA显卡驱动
详见[Ubuntu安装NVIDIA驱动、CUDA、cudnn.md](Ubuntu安装NVIDIA驱动、CUDA、cudnn.md)

### 4. 搭建深度学习平台
详见[Ubuntu下从零搭建深度学习平台.md](Ubuntu下从零搭建深度学习平台.md)

## 三、使用Ubuntu
### 1. 包管理
详见[Ubuntu包管理.md](Ubuntu包管理.md)

### 2. 常用命令
详见[Ubuntu常用命令.md](Ubuntu常用命令.md)

### 3. 其他配置
#### 关闭更新
详见[Ubuntu关闭更新.md](Ubuntu关闭更新.md)
#### 高级玩法
详见[Ubuntu高级玩法.md](Ubuntu高级玩法.md)

## 四、问题集中营
### 1. *无法使用make编译，出现makefile: XXXXXXX failed*
如安装CUDA在编译`deviceQuery`时，提示：
```shell
g++: No such file or directory
Makefile:288: recipe for target 'deviceQuery.o' failed
make: *** [deviceQuery.o] Error 1
```
需要安装g++：
```shell
sudo apt-get install libncurses5-dev
```

### 2. *`nvcc --version`不显示*
重装了一下cuda，然后发现nvcc命令不存在了，终端提示使用`sudo apt-get install nvidia-cuda-toolkit`来使用nvcc。  
注意，<font color='red'><b>不要</b></font>使用这种方式安装，因为系统认为你没有安装cuda，实际上你已经装了，执行这条命令会重新安装cuda。  
正确操作：
```shell
cd /usr/local/cuda-10.1/bin
```
查看cuda的`bin`目录下是否有nvcc，有的话直接将cuda路径加入系统路径就可以了。可以写入`~/bashrc`里面：
```shell
gedit ~/.bashrc
```
将下面两行加在文件最下面：
```
export PATH=$PATH:/usr/local/cuda/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda/lib64
```
最后激活变更：
```shell
source ~/.bashrc
```
即可。

### 3. *没有`ifconfig`命令*
```shell
sudo apt install net-tools
```

### 4. *几分钟自动断网*
在`/etc/ppp/options`中，注释掉`Icp-echo-failure 4`和`Icp-eco-interal 30`。这两是向服务器发送询问，所以将两个注释掉就能阻止发送询问，就不会造成断网。
```shell
sudo gedit /etc/ppp/options
```
    # Icp-echo-failure 4
    # Icp-eco-interal 30
