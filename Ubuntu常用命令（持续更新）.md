# **Ubuntu常用命令**
*主页：https://github.com/wjxpro*

*邮箱：804359553@qq.com*

[TOC]

## 说明
所有命令均在终端运行！！！
> + `#`：注释  
> + `${}`：按需自行更改  
> + `[]`：可选参数  
> + `()`：可替换为括号内命令  
> + `-`：多个参数可以共用一个`-`

## 系统
### 管理员
```shell
# 进入root环境
su [root]

# 使用管理员权限运行命令
sudo ${your_command}

# 获取文件（夹）的权限
sudo chmod [-R] ${三位8进制数} ${filename}

# 更改文件（夹）所有者
sudo chown [-R] ${new_user} ${folder}
```
> 关于chmod的使用可参见 [Linux 文件基本属性](https://www.runoob.com/linux/linux-file-attr-permission.html)

### 硬件
```shell
# 查看系统属性
cat /proc/version

# 查看cpu信息概要
lscpu

# 查看内存情况
free [-mgh]  # -m，-g：内存显示方式

# 英伟达显卡信息
nvidia-smi

# 查看系统磁盘空间
df [-ha]  # -h：可阅读模式，-a：查看所有文件系统的磁盘空间

# 用磁盘分区工具查看磁盘空间
fdisk -l
```

### 网络
```shell
# 查看网络配置
ifconfig

# 下载并安装包（yum为centos下的同类工具）
apt(apt-get) install ${aptname}
```

## 文件
### 文件操作
```shell
# 列出目录内容
ls [${path}]  # 默认列出当前工作目录
ll [${path}]  # 详细列出

# 转换当前工作目录
cd ${path}

# 在当前位置创建文件
touch ${filename}

# 在当前位置创建文件夹
mkdir ${dirname}

# 移动文件（夹），重命名文件（夹）
mv ${oldpath} ${newpath}

# 复制文件（夹）
cp [-r] ${filepath} ${dirpath}  # -r：文件夹

# 删除文件（夹）
rm [-rf] ${filename}

# 在终端查看文件内容
cat ${filename}

# 使用vi/vim工具编辑文件
vi/vim ${filename}  # 更高级的vim可能需要自行安装

# 在文件查看窗口编辑文件
gedit ${filename}

# 查看该目录下文件夹大小
du -h --max-depth=1
```

### 解压
```shell
tar [-cxtzjvfpPN] ${filename}
unzip ${filename}
```
参数：
> + -c ：建立一个压缩文件的参数指令(create 的意思)；
> + -x ：解开一个压缩文件的参数指令！
> + -t ：查看 tarfile 里面的文件！
特别注意，在参数的下达中， c/x/t 仅能存在一个！不可同时存在！因为不可能同时压缩与解压缩。
> + -z ：是否同时具有 gzip 的属性？亦即是否需要用 gzip 压缩？
> + -j ：是否同时具有 bzip2 的属性？亦即是否需要用 bzip2 压缩？
> + -v ：压缩的过程中显示文件！这个常用，但不建议用在背景执行过程！
> + -f ：使用档名，请留意，在 f 之后要立即接档名喔！不要再加参数！例如使用『 tar -zcvfP tfile sfile』就是错误的写法，要写成『 tar -zcvPf tfile sfile』才对喔！
> + -p ：使用原文件的原来属性（属性不会依据使用者而变）
> + -P ：可以使用绝对路径来压缩！
> + -N ：比后面接的日期(yyyy/mm/dd)还要新的才会被打包进新建的文件中！
> + --exclude FILE：在压缩的过程中，不要将 FILE 打包！

## 运行
```shell
# 显示进程
ps

# 显示占用nvidia设备的进程
fuser -v /dev/nvidia*

# 终止（杀死）进程
kill [-9] ${PID}
killall ${进程名}  # 会杀掉所有同名进程

# 在指定的GPU下运行命令，GPU的ID可用nvidia-smi查看
CUDA_VISIBLE_DEVICES=${GPU-ID} ${your_command}
# 如CUDA_VISIBLE_DEVICES=1 python train.py

# 使进程在后台运行，命令行输出结果保存在当前目录下的nohup.out中
nohup ${your_command} &
# 如nohup python train.py &
nohup ${your_command} > ${your_logfile} 2>&1 &
# 2>&1 解释：
# 将标准错误 2 重定向到标准输出 &1 ，标准输出 &1 再被重定向输入到 your_logfile 文件中。
# 0 – stdin (standard input，标准输入)
# 1 – stdout (standard output，标准输出)
# 2 – stderr (standard error，标准错误输出)

# 实时查看命令使用情况（默认每两秒刷新），ctrl+C停止
watch [-n ${second}] ${your_command}
# 如watch -n 1 nvidia-smi
```

## 键盘命令
> <kbd>Ctrl</kbd> + <kbd>Insert</kbd>：复制  
<kbd>Shift</kbd> + <kbd>Insert</kbd>：粘贴  
<kbd>Ctrl</kbd> + <kbd>C</kbd>：强制中断运行  
<kbd>Ctrl</kbd> + <kbd>Z</kbd>：强制暂停运行  
<kbd>Ctrl</kbd> + <kbd>D</kbd>：退出
