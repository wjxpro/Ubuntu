# **Ubuntu高级玩法**
*主页：https://github.com/wjxpro*

*邮箱：804359553@qq.com*

[TOC]

## 在服务器中编辑代码
1. 通过`vi/vim`命令，具体在教程文档中已说明。
2. 在xftp中选中需要编辑的代码文件，右键选择打开或者用记事本编辑即可。
3. vs code连接远程之后可以即时修改并保存。

## XShell断开连接后，仍然保持服务器运行
```shell
# 使用nohup命令，使命令在服务器后台运行
# nohup命令会在当前目录下保存命令行运行结果的nohup.out文件
# 用CUDA_VISIBLE_DEVICES指定GPU时，此命令需加在nohup前
nohup ${YOUR COMMAND} &

# 查看命令执行情况
cat nohup.out

# 使用kill命令结束nohup进程后，需要清理显存
# 使用以下命令可显示占用nvidia设备的进程pid，再对这些进程使用kill命令
fuser -v /dev/nvidia*
```

## 指定GPU运行代码
```shell
# 在需要运行的代码前加：
CUDA_VISIBLE_DEVICES=0  # 或1，2，...
```

## `man`手册
Ubuntu提供的C语言函数手册。
```shell
man ${a C function}  # 使用

sudo apt install manpages-zh  # man中文手册安装
```

## `wine`
使用`wine`可以在Ubuntu下安装Windows软件。
```shell
sudo dpkg --add-architecture i386  # 如果你使用的是64位Ubuntu，则先要开启32位安装环境？？？
sudo apt install wine-stable  # 安装wine

wine --version  # 查看wine版本

winecfg  # 配置wine

wine ${package_name}.exe  # 安装windows软件

wine uninstaller  # 卸载软件
```

### 解决中文方框
原因：缺少字体文件。
1. 在`home`目录下，按<kbd>Ctrl</kbd>+<kbd>H</kbd>，显示隐藏的文件夹（再按一次可以取消显示）。
2. 在Windows系统下找到`C:\\Windows\Fonts\`目录，拷贝字体文件到`~/.wine/drive_c/windows/Fonts/`下。

## `exfat`类型磁盘支持
```bash
sudo apt install exfat-utils
```

## 快捷访问文件夹
把文件夹添加到收藏。
