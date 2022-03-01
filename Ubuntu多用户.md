# **Ubuntu多用户**
*主页：https://github.com/wjxpro*

*邮箱：804359553@qq.com*

[TOC]

## 一、root用户
在Ubuntu中，root用户默认不开启账户登录选项，默认密码也是随机的，所以需要我们自己设置root用户的密码。
### 1. 设置root账户的密码
执行`sudo passwd`命令后，首先输入当前账户密码，确认无误后，系统会提示`Enter new UNIX password: `，这是root密码，自行设置。注意在Ubuntu的命令行中，输入的密码是不可见的，只需要输入之后回车即可。
```shell
viewer@viewer-System-Product-Name:~$ sudo passwd root  # 或者sudo passwd
[sudo] viewer passwd: 
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
```
### 2. 进入root命令行
```shell
viewer@viewer-System-Product-Name:~$ su
Password: 
root@viewer-System-Product-Name:/home/viewer#  
```
### 3. 退出root命令行
按 <kbd>Ctrl</kbd>+<kbd>D</kbd> 可以退出`root`。

## 二、普通用户
### 1. 添加多用户
```shell
sudo adduser ${new_username}

sudo deluser [--remove-home] ${username}
```
### 2. 分配sudo权限

```shell
sudo gedit /etc/sudoers
```
在`# Members of the admin group may gain root privileges`这句下面添加：

> ${new_username} ALL=(ALL) ALL
