---
layout:     post
title:      "Linux私房菜：规则与安装"
subtitle:   ""
date:       2017-01-28
author:     "Jennica"
header-img: "img/post-bg-linux.jpg"
catalog: true
tags:
    - 技术
    - 读书
    - Linux
---


> 重温Linux。

# 前言

把[《鸟哥的Linux私房菜基础学习篇》](https://read.douban.com/ebook/12872434/)读薄系列笔记。

1. 开始学习Linux
2. 主机规划与磁盘分区
3. 系统安装
4. 登陆和在线求助

# 开始学习Linux

1. 内核：管控硬件并提供相关功能。内核程序所放置到内存当中的区块是受保护的，并且开机后一直常驻在内存当中。
2. 系统调用：操作系统除内核外，还提供一整组开发接口，软件开发需遵循系统调用参数。
3. GNU：Linux是在GNU GPL授权下的自由软件，可自由使用及修改源码，不能单纯销售。

# 主机规划与磁盘分区

1. 硬件设备：在Linux中设备都被当作一个文件来对待，基本都在/dev内。如，IDE硬盘（/dev/hd[a-d]），SCSI／SATA／USB（/dev/sd[a-p]）。
5. SCSI模块：SCSI／SATA／USB都由SCSI模块驱动，这些设备的文件名根据Linux内核检测到的顺序。
6. 磁盘第一扇区：包含446B的主引导分区MBR，和64B的分区表。
7. 分区：最小单位是柱面；最多4个主分区或扩展分区，最多有1个扩展分区；只有主分区和逻辑分区可格式化；扩展分区可记录其划分的逻辑分区，IDE最多59个逻辑分区（5～63），SATA最多11个逻辑分区（5～15）。
8. 挂载：从目录树中的目录点作为挂载点，读取磁盘分区数据；根目录／一定要挂在到某个分区。
9. 开机流程：BIOS根据设置取得硬盘并读取其MBR，MBR中放置了最基本引导加载程序boot loader（常用grub），loader加载内核文件。
10. boot loader：可提供开机选项菜单，根据菜单选项直接载入内核文件，或转交给安装在所选分区引导扇区的其他loader。

# 系统安装
1. 文件系统类型：ext2／ext3适合Linux，ext3带日志；LVM弹性调整文件系统大小；RAID软件仿真出磁盘阵列；swap用于内存交换空间，不需目录树的挂载；vfat可同时被Linux和Windows支持。
12. swap分区：不常使用的数据从物理内存中移到swap交换空间，可将物理内存释放；大小最好为物理内存的1.5到2倍。
13. 安装笔记本：让内核不要加载台式机的电源及显卡选项，`boot: linux nofb apm=off acpi=off pci=noacpi`。
14. 多重引导：先装Windows后装Linux，将引导程序grub安装在第一可开机设备的MBR上，用grub控制全部开机菜单并添加Windows启动项。

# 登陆和在线求助
1. 登录模式：纯文本（run level3），6个终端界面tty1～tty6；图形界面（run level5），除纯文本还拥有一个图形界面桌面tty7
16. 注销：离开系统并不是关机，只是当前登陆工作停止，命令为exit或^D。
17. 热键：Tab，连按两次，命令补全和文件补齐；^C终止程序；^D表示EOF或注销。
18. man page：括号中的数字，1代表一般账号命令，8代表管理员命令，5表示系统配置文件格式。
19. info page：将说明拆为有层次的多个节点，类似超链接。
20. 关机：错误关机会导致其他用户中断或文件系统损坏；sync数据同步写入磁盘，shutdown／reboot／halt等命令在关机前均调用了sync；命令之间区别不大，shutdown后自动调用halt，halt前自动调用shutdown；init命令修改run level到0可关机，到6可重启。
21. shutdown功能：自由选择关机模式，设置关机时间，自定义关机消息，可仅发信息不关机，选择是否要fsck检查文件系统。
22. 文件系统错误：不正常开关机或硬盘使用率过高都会导致数据损坏；对发生错误的分区调用fsck命令可修复硬盘，若根目录损坏可拔出硬盘接到另一台Linux机fsck。
23. 忘记root密码：进入grub编辑模式，在kernel行尾添加single，进入单用户维护模式，将以root进入tty1，passwd修改密码。
