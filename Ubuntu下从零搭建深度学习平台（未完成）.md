# **Ubuntu下从零搭建深度学习平台**
*主页：https://github.com/wjxpro*

*邮箱：804359553@qq.com*

[TOC]

## 〇、深度学习与GPU

## 一、NVIDIA驱动、CUDA和CUDNN
详见[Ubuntu安装NVIDIA驱动、CUDA、cudnn.md](Ubuntu安装NVIDIA驱动、CUDA、cudnn.md)

## 二、Anaconda
详见[Ubuntu下配置Anaconda.md](Ubuntu配置Anaconda.md)

## 三、开源框架
### TensorFlow
<a href="https://tensorflow.google.cn/" target="-blank" title="TensorFlow 官网">
<img src="img/tf_logo_horizontal.png">
</a>

[安装 TensorFlow](https://www.tensorflow.org/install)

> <font color=red><b>注意</b></font>：tensorflow版本和python的版本要对应，例如安装的是tensorflow的1.13.1版本，则python版本需要小于等于3.7。

### PyTorch
<a href="https://pytorch.org/" target="-blank" title="PyTorch 官网">
<img src="img/pytorch.png">
</a>

在官网中查询安装命令。
+ [Previous PyTorch Versions](https://pytorch.org/get-started/previous-versions/)
+ [PyTorch安装命令查询.md（未完成）](PyTorch安装命令查询.md)

> <font color=red><b>注意</b></font>：如果已经配置过国内镜像源，则`conda`命令后不要加`-c pytorch`。

### caffe

### keras

### paddle paddle