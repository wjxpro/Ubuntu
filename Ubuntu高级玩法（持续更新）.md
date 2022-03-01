# **Ubuntu高级玩法**
*主页：https://github.com/wjxpro*

*邮箱：804359553@qq.com*

[TOC]

### `exfat`类型磁盘支持
```bash
sudo apt install exfat-utils
```

### `man`手册
Ubuntu提供的C语言函数手册。
```shell
man ${a C function}  # 使用

sudo apt install manpages-zh  # man中文手册安装
```

### `wine`
使用`wine`可以在Ubuntu下安装Windows软件。
```shell
sudo dpkg --add-architecture i386  # 如果你使用的是64位Ubuntu，则先要开启32位安装环境？？？
sudo apt install wine-stable  # 安装wine

wine --version  # 查看wine版本

winecfg  # 配置wine

wine ${package_name}.exe  # 安装windows软件

wine uninstaller  # 卸载软件
```
#### 解决中文方框
原因：缺少字体文件。
1. 在`home`目录下，按<kbd>Ctrl</kbd>+<kbd>H</kbd>，显示隐藏的文件夹（再按一次可以取消显示）。
2. 在Windows系统下找到`C:\\Windows\Fonts\`目录，拷贝字体文件到`~/.wine/drive_c/windows/Fonts/`下。

### 快捷访问文件夹
把文件夹添加到收藏：

### 服务器远程使用
#### a. [Xshell、Xftp、Xmanager](https://www.netsarang.com/zh/)
#### b. <a href="https://pgy.oray.com/" target="-blank" title="蒲公英官网"><img src="img/icon_pgy.png" height=24><font color=#b1b1b1> 蒲公英</font></a>
详见[Ubuntu服务器远程使用.md](./Ubuntu服务器远程使用.md)
#### c. <a href="https://sunlogin.oray.com/" target="-blank" title="向日葵官网"><img src="img/icon_sun.png" height=24><font color=#b1b1b1> 向日葵</font></a>

### 使用系统盘破解实体机
1. 进入系统盘的`Try Ubuntu`
2. 打开Try Ubuntu的终端，输入下面的命令获取Root权限：
```bash
sudo passwd root
```
3. 打开实体机目录
4. 可以使用Root权限操作
