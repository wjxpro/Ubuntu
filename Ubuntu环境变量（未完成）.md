# **Ubuntu环境变量**
*主页：https://github.com/wjxpro*

*邮箱：804359553@qq.com*

[TOC]

## 环境变量配置文件
```

```

## 终端命令
```bash
echo ${已经存在的环境变量名}  # 显示已经存在的环境变量值

export  # 显示当前所有环境变量

source ${一些配置文件或者某些环境}
```

## 修改环境变量
### 语法小知识
> + 变量值之间用`:`分隔
> + 引用一个存在的变量时，要在变量名前加`$`

推荐学习Linux shell编程语法。

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

