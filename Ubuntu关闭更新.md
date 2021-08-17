# **Ubuntu关闭更新**
*主页：https://github.com/wjxpro*

*邮箱：804359553@qq.com*

[TOC]

## 小说明
普通用户可以不关闭，但如果是开发者，最好关掉保持环境稳定。

永远不要更新gcc版本！！！需要使用其它版本时，不要删除原版，另外安装后更改下默认。记得之后改回来。

## 方法
### 关闭系统更新
修改配置文件：
```bash
sudo gedit /etc/apt/apt.conf.d/10periodic
```
０是关闭，1是开启，将所有值改为0。

### 关闭内核更新
```bash
sudo apt-mark hold linux-image-generic linux-headers-generic 
```