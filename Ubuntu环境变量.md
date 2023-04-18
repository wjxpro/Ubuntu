# **Ubuntu环境变量**
*主页：https://github.com/wjxpro*

*邮箱：804359553@qq.com*

[TOC]

## 环境变量配置文件
参考自[Ubuntu 系统环境变量配置文件](https://blog.csdn.net/chan70707/article/details/81636327)。
+ `/etc/profile`: 在登录时，操作系统定制用户环境时使用的第一个文件，此文件为系统的每个用户设置环境信息，当用户第一次登录时，该文件被执行。
+ `/etc/environment`: 在登录时操作系统使用的第二个文件， 系统在读取你自己的`profile`前，设置环境文件的环境变量。
+ `~/.profile`：在登录时用到的第三个文件是`.profile`文件，每个用户都可使用该文件输入专用于自己使用的shell信息，当用户登录时，该文件仅仅执行一次！默认情况下，他设置一些环境变量，执行用户的`.bashrc`文件。
+ `/etc/bashrc`: 为每一个运行`bash shell`的用户执行此文件。当`bash shell`被打开时，该文件被读取.
+ `~/.bashrc`: 该文件包含专用于你的`bash  shell`的bash信息，当登录时以及每次打开新的`shell`时，该该文件被读取。

通常，多用户通用的环境变量放到`/etc/profile`中，用户自己需要的环境变量放到`~/.bashrc`中（`~`表示用户自己的家目录）。

## 终端命令
```bash
echo ${已经存在的环境变量名}  # 显示已经存在的环境变量值

export  # 显示当前所有环境变量

source ${一些配置文件或者某些环境}
```

## 修改环境变量
### 语法小知识
+ 变量值之间用`:`分隔
+ 引用一个存在的变量时，要在变量名前加`$`

推荐学习Linux shell编程语法，参考[菜鸟教程——Shell 教程](https://www.runoob.com/linux/linux-shell.html)

### 直接赋值
直接赋值可以一次赋单个值，也可以一次赋多个值。如果重复赋值，新的会覆盖旧的。
```bash
export ${环境变量名}=${值1}:${值2}:${...}:${值n}
## 例子：
export CUDA_HOME=/usr/local/cuda
```
### 增量赋值
增量赋值就是在已有的变量的基础上增加新的值，通常会用来增加PATH这个变量
```bash
export ${环境变量名}=$(${环境变量名}):${新增值}
# 或
export ${环境变量名}=${新增值}:$(${环境变量名})
# 例子：
export PATH=$PATH:/usr/local/cuda/bin
# 语句的含义是：使用$引用原来的PATH，并在后面加上新值/usr/local/cuda/bin，最后重新赋值给PATH
```
### 修改变量
使用管道+正则表达式，进行变量值的字符串替换。
```bash
export PATH=`echo $PATH | sed 's/${原来的值}/${新的值}/g'`
# 例子：
export PATH=`echo $PATH | sed 's/\/usr\/local\/cuda\/bin/\/usr\/local\/cuda-10.1\/bin/g'`
# 语句的含义是：使用echo命令得到原PATH的字符值，将结果使用管道传给sed命令，并把原PATH中的/usr/local/cuda/bin替换为/usr/local/cuda-10.1/bin，最后将得到的新字符串赋值给PATH
# 注意：正斜杠/需要用反斜杠\转译，变成\/
```

