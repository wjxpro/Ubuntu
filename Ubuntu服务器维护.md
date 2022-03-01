# **Ubuntu服务器维护**
*主页：https://github.com/wjxpro*

*邮箱：804359553@qq.com*

[TOC]

## 卸载显卡驱动
```bash
sudo apt-get purge nvidia*

sudo apt autoremove
```

## 选择内核版本启动
### 图形界面操作
重启后，在进入主机logo界面时，按<kbd>Esc</kbd>进入`grub`引导界面。选择`Advanced options for Ubuntu`后，进入其子菜单，选择一更新前内核版本或者较老的硬核版本，然后等待重启即可。
### 命令行操作
```bash
sudo gedit /etc/default/grub
```
根据需要修改下面一行内容：
```bash
GRUB_DEFAULT="1> 4"
# 注：1 代表主菜单的第二项Advanced options for Ubuntu；4代表1项目下面对应的子菜单里面的第5项
```
输入以下命令适用更改：
```bash
sudo update-grub
```

## 重装显卡驱动出错
若报错信息如下：
```
An NVIDIA kernel module ‘nvidia-drm‘ appears to already be loaded in your kernel...
```
进入tty界面：
<kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>F1~F12</kbd>

```bash

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