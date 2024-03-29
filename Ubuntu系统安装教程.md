# **Ubuntu系统安装教程**
*主页：https://github.com/wjxpro*

*邮箱：804359553@qq.com*

[TOC]

## 〇、准备工作
参考：[UltraISO（软碟通）制作U盘启动盘完整教程](https://zhuanlan.zhihu.com/p/326406632)

下载Ubuntu系统镜像（.iso文件），并使用`UltraISO`软件制作U盘启动盘：
- 插入U盘，此U盘在稍后会被<font color='red' size=4><b>格式化</b></font>，注意备份数据；
- 在UltraISO中的本地目录，选择下载好的镜像文件，然后双击；
- 选择菜单栏`启动`->`写入硬盘映像...`；
- 在打开的界面中，硬盘驱动器选择刚插入的U盘，点击`写入`，确认格式化。等待进度条走完，便完成了U盘启动盘的制作。

如果要安装双系统，推荐在`Windows`下先给需要安装新系统的磁盘中分出一个空闲分区，便于后续安装。以在`Win10`上操作为例：
- 在任务栏`Windows图标`上，`右键`->`磁盘管理`；
- 选择需要安装新系统的**固态**硬盘，在当前分区表内选择空闲空间较多的分区，`右键`->`压缩卷`；
- `输入压缩空间量`，推荐**大于64G**，`压缩`；
- 压缩完成，生成新的空闲卷。不需要对空闲卷进行任何操作。

## 一、开始安装
参考：[Ubuntu18.04/20.04完整新手安装教程](https://www.jianshu.com/p/54d9a3a695cc)

1. 按<kbd>F2</kbd>或者其他键（还可能是F10、F12、Delete键等，与主板对应）进入BIOS，选择U盘启动盘启动。如果在启动菜单里没有U盘启动盘，则重启再次选择
2. 点击`Install Ubuntu 18.04 LTS`
3. `Welcone`：欢迎界面，选择语言English（或中文）
4. `Keyboard layout`：键盘布局，默认即可
5. `wireless`：无线设置，选择我现在不想连接wifi无线网络（wlan口可以直接拔掉网线）
6. `Updates and other software`：更新和其他软件，选择正常安装，服务器因为不需要其他工具，为了节省空间也可以选择`Minimal installation`最小安装
7. `Installation type`：安装类型，手动分区选择`Something else`：
    - `New Partition Table`：新建分区表，可以格式化之前的磁盘分区表，然后从零分区，也就是格式化磁盘重装电脑，**安装双系统不要点！！！** 会把Windows系统的分区表删掉。
    - 选择需要安装系统的磁盘，选中`free space`空闲空间，然后点击<kbd>+</kbd>，或者直接双击空闲空间，按照如下方式依次分区：
        <table>
            <tr>
                <th colspan="2">分区类型</th>
                <th>分配空间大小</th>
                <th>分区类型</th>
                <th>格式</th>
                <th>挂载点</th>
            </tr>
            <tr>
                <td colspan="2">EFI分区？</td>
                <td>300MB</td>
                <td>主分区</td>
            </tr>
            <tr>
                <td colspan="2">交换分区</td>
                <td>内存大小</td>
                <td>主分区？</td>
            </tr>
            <tr>
                <td>个人</td>
                <td>根目录</td>
                <td>剩余所有空间</td>
                <td>逻辑分区</td>
                <td>EXT4</td>
                <td>'/'</td>
            </tr>
            <tr>
                <td rowspan="2">服务器</td>
                <td>根目录</td>
                <td>128G</td>
                <td>主分区？</td>
                <td>EXT4</td>
                <td>'/'</td>
            </tr>
            <tr>
                <td>home</td>
                <td>剩余所有空间</td>
                <td>逻辑分区</td>
                <td>EXT4</td>
                <td>'/home'</td>
            </tr>
        </table>

        > **注**：服务器通常为多用户使用，推荐将`根目录`与`home`分开。如果某个用户不小心修改了系统文件导致系统损坏，则重做系统时不格式化`home`所在分区并重新挂载，然后使用的时候`home`修改文件的所有者，就可以保留用户文件。

        > **注**：如果先在安装系统时
    - `Device for boot loader installation`：安装启动引导器的设备，选择刚刚分好的EFI分区
    - `Install Now`：现在安装，继续
8. `Where are you?`：选择地区，shanghai，东八区
9. `Who are you?`：填写用户信息

等待安装，完成后重启即可。
