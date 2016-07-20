---
layout:     post
title:      "Kali Linux下常用软件安装及配置"
subtitle:   ""
date:       2015-07-12
author:     "Jennica"
header-img: "img/post-bg-linux.jpg"
catalog: true
tags:
    - 技术
    - Linux
---

> 吾本贪婪，故而无妄。

# 0x00 Synaptic
[Synaptic（新立得）][1]是一个高级软件包管理器，它可以管理系统内安装的每个软件及包组件，在图形界面内完成LINUX系统软件的搜寻、安装和删除。

Synaptic安装简单，命令如下：
```
yogy@kali:~$ sudo apt-get install synaptic
```
运行Synaptic，输入关键词后，可筛选列举更新源中获取的所有相关包。

# 0x01 OpenVPN
使用[国外VPS][2]搭建OpenVPN，实现本地Kali客户端与远程Ubuntu服务端的VPN通信。
### 服务端
1. 下载并安装 [LZO][3] && [OpenSSL][4] && [OpenVPN][5]
2. 生成密钥文件
```
root@server:/# openvpn --genkey --secret /etc/openvpn/secret.key
```
密钥文件secret.key需拷贝至客户端
3. 服务端配置文件
```
root@server:/# vi /et/openvpn/server.conf
```
> 
dev tun
ifconfig 172.16.10.1 172.16.10.2
keepalive 10 60
proto tcp-server    
port 1119         
\#user nobody
\#group nogroup
persist-tun
persist-key
comp-lzo
verb 3
secret /etc/openvpn/secret.key
4. 添加开机启动
```
root@server:/# vi /etc/rc.local 
```
> 
echo "1" > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -s 172.16.10.1/32 -o venet0 -j MASQUERADE
iptables -t nat -A POSTROUTING -s 172.16.10.2/32 -o venet0 -j MASQUERADE
/usr/local/sbin/openvpn /etc/openvpn/server.conf &
exit 0

### 客户端
1. 拷贝密钥文件至/etc/openvpn/secret.key
2. 客户端配置文件
```
yogy@kali:~$ sudo vi /etc/openvpn/client.ovpn
```
> 
dev tun
remote 12.34.56.78 # remote ip address of openvpn server
ifconfig 172.16.10.2 172.16.10.1
keepalive 10 60
proto tcp-client
port 1119
persist-tun
persist-key
comp-lzo
verb 3
secret /etc/openvpn/secret.key
redirect-gateway def1
3. 运行OpenVPN建立通信
```
yogy@kali:~$ sudo openvpn /etc/openvpn/client.ovpn
```
> Sat Jul 11 12:11:55 2015 OpenVPN 2.2.1 x86_64-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [eurephia] [MH] [PF_INET6] [IPv6 payload 20110424-2 (2.2RC2)] built on Dec  1 2014
...
Sat Jul 11 12:11:57 2015 Initialization Sequence Completed

# 0x02 VirtualBox
[VirtualBox][6]小巧精悍，适合用于Kali中运行Windows7虚拟机。
1. 添加源及密钥
```
yogy@kali:~$ sudo echo "deb http://download.virtualbox.org/virtualbox/debian wheezy contrib"  >> /etc/apt/sources.list
yogy@kali:~$ wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -
```
2. 更新源并安装
```
yogy@kali:~$ sudo apt-get update
yogy@kali:~$ sudo apt-get install virtualbox-4.3 dkms
```
3. 修改虚拟系统文件大小
```
yogy@kali:~/VirtualBox VMs/win7$ vboxmanage modifyhd win7.vdi --resize 52428
```
4. 删除多余内核
```
yogy@kali:~$ dpkg --get-selections | grep linux-image
linux-image-3.18.0-kali3-amd64			install
linux-image-3.7-trunk-amd64			install
yogy@kali:~$ uname -a
Linux kali 3.18.0-kali3-amd64 #1 SMP Debian 3.18.6-1~kali2 (2015-03-02) x86_64 GNU/Linux
yogy@kali:~$ sudo apt-get remove linux-image-3.7-trunk-amd64
yogy@kali:~$ sudo apt-get autoclean
```
5. USB赋权

 * 将当前用户加入vboxusers组
```
yogy@kali:sudo /usr/sbin/usermod -G vboxusers -a yogy
```
 * 查询vboxusers组编号
```
yogy@kali:~$ cat /etc/group | grep vboxusers 
```
> vboxusers:x:137:yogy

 * 添加读写权限
```
yogy@kali:~$ sudo echo "none /proc/bus/usb usbfs devgid=137,devmode=664 0 0" >> /etc/fstab
```
6. 启动USB
下载并添加[VirtualBox扩展包][15]，启动USB 2.0控制器，分配USB设备。

# 0x03 Code::Blocks
Code::Blocks是一款轻量级开源跨平台C/C++ IDE，极力推荐。
1. [官网][7]下载源码
2. 二次解压*.tar.xz
```
yogy@kali:~/Downloads$ xz -d codeblocks-13.12-1_amd64.debian.stable.tar.xz
yogy@kali:~/Downloads$ tar -zxvf codeblocks-13.12-1_amd64.debian.stable.tar
```
3. 安装*.deb
```
yogy@kali:~/Downloads$ cd /debian-stable/amd64
yogy@kali:~/Downloads/debian-stable/amd64$ sudo dpkg -i *.deb
yogy@kali:~/Downloads/debian-stable/amd64$ sudo apt-get -f install
yogy@kali:~/Downloads/debian-stable/amd64$ sudo dpkg -i codeblocks-common_13.12-1_all.deb
```
4. 修改输出终端
Environment settings -- General settings -- Terminal to launch console programs: gnome-terminal -t $TITLE -x
5. 汉化（可选）
  * 下载[*.mo][8]
  * 移至指定目录
```
yogy@kali:~/Downloads$ mkdir -p /usr/share/codeblocks/locale/zh_CN
yogy@kali:~/Downloads$ cp codeblocks.mo /usr/share/codeblocks/locale/zh_CN
```
  * Environment settings -- View -- Internationalization: Chinese (Simplified)

# 0x04 Pycharm
给最爱的Python，配最好的IDE。
1. 修改java版本
```
yogy@kali:~$ update-alternatives --config java
```
> 
有 2 个候选项可用于替换 java (提供 /usr/bin/java)。
  选择       路径                                          优先级  状态
  \* 0            /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java   1061      自动模式
 1            /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java   1061      手动模式
 2            /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java   1051      手动模式
要维持当前值[*]请按回车键，或者键入选择的编号：2

  ```
yogy@kali:~$ update-alternatives --config javac
```
> 
有 2 个候选项可用于替换 javac (提供 /usr/bin/javac)。
  选择       路径                                       优先级  状态
\* 0            /usr/lib/jvm/java-6-openjdk-amd64/bin/javac   1061      自动模式
  1            /usr/lib/jvm/java-6-openjdk-amd64/bin/javac   1061      手动模式
  2            /usr/lib/jvm/java-7-openjdk-amd64/bin/javac   1051      手动模式
要维持当前值[*]请按回车键，或者键入选择的编号：2
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/javac to provide /usr/bin/javac (javac) in 手动模式
2. 下载并安装
```
yogy@kali:~/Downloads$ wget http://download-cf.jetbrains.com/python/pycharm-professional-4.5.2.tar.gz
yogy@kali:~/Downloads$ sudo tar -zxvf pycharm-professional-4.5.2.tar.gz
yogy@kali:~/Downloads$ sudo cp -r pycharm-4.5.2 /opt/
```
3. 获取注册码
Jetbrains旗下产品，学生可通过University email address、ISIC/ITIC membership、Official document三种方式[免费申请][9]。
4. 创建快捷方式
  * 手动创建
```
yogy@kali:/usr/share/applications$ sudo gedit jetbrains-pycharm.desktop
```
> 
[Desktop Entry]
Version=1.0
Type=Application
Name=PyCharm
Icon=/opt/pycharm-4.5.2/bin/pycharm.png
Exec="/opt/pycharm-4.5.2/bin/pycharm.sh" %f
Comment=Develop with pleasure!
Categories=Development;IDE;
Terminal=false
StartupWMClass=jetbrains-pycharm

  * 软件创建
Configure -- Creat Desktop Entry

# 0x05 ns-3
[ns-3][10]是针对互联网系统的离散事件网络仿真平台，主要用于研究。
1. 下载ns-3源码
```
yogy@kali:/home/yogy/Workspace$ wget http://www.nsnam.org/release/ns-allinone-3.23.tar.bz2
yogy@kali:/home/yogy/Workspace$ tar xjf ns-allinone-3.23.tar.bz2
```
2. 安装Doxygen
```
yogy@kali:~/Downloads$ wget http://jaist.dl.sourceforge.net/project/doxygen/rel-1.8.10/doxygen-1.8.10.linux.bin.tar.gz
yogy@kali:~/Downloads/doxygen-1.8.10$ gedit Makefile
```
> 
RM        = rm -f
VERSION   = 1.8.10
INSTALL   = /usr/local
INSTTOOL  = /usr/bin/install
DOXYDOCS  = ..
export TMAKEPATH
install: 
	$(INSTTOOL) -d $(INSTALL)/bin
	$(INSTTOOL) -d $(INSTALL)/doc/doxygen
	$(INSTTOOL) -m 755 bin/doxygen    $(INSTALL)/bin

  ```
yogy@kali:~/Downloads/doxygen-1.8.10$ ./configure
yogy@kali:~/Downloads/doxygen-1.8.10$ sudo make
yogy@kali:~/Downloads/doxygen-1.8.10$ sudo make install
```
3. 生成文档
``` 
yogy@kali:~/Workspace/ns-allinone-3.23/ns-3.23$ doxygen doc/doxygen.conf
yogy@kali:~/Workspace/ns-allinone-3.23/ns-3.23/doc$ sudo easy_install Sphinx dia
yogy@kali:~/Workspace/ns-allinone-3.23/ns-3.23/doc/tutorial$ make html
yogy@kali:~/Workspace/ns-allinone-3.23/ns-3.23/doc/manual$ make html
yogy@kali:~/Workspace/ns-allinone-3.23/ns-3.23/doc/models$ make html
```
4. 编译运行
```
yogy@kali:~/Workspace/ns-allinone-3.23/ns-3.23$ ./waf configure --enable-tests --enable-examples
yogy@kali:~/Workspace/ns-allinone-3.23/ns-3.23$ ./waf --run hello-simulator
```

# 0x06 ndnSIM
1. 安装依赖库
```
yogy@kali:~$ sudo aptitude install libboost-all-dev
yogy@kali:~$ sudo apt-get install python-dev python-pygraphviz python-kiwi python-pygoocanvas python-gnome2 python-rsvg ipython
```
2. 下载ndnSIM源码
```
yogy@kali:~/Workspace$ mkdir ndnSIM
yogy@kali:~/Workspace/ndnSIM$ git clone -b ndnSIM-v1 git://github.com/cawka/ns-3-dev-ndnSIM ns-3
yogy@kali:~/Workspace/ndnSIM$ git clone git://github.com/cawka/pybindgen.git pybindgen
yogy@kali:~/Workspace/ndnSIM$ git clone -b master-v1 git://github.com/named-data/ndnSIM.git ns-3/src/ndnSIM
```
3. 编译运行
```
yogy@kali:~/Workspace/ndnSIM/ns-3$ ./waf configure --enable-tests --enable-examples
yogy@kali:~/Workspace/ndnSIM/ns-3$ ./waf --run=ndn-simple --vis
```

# 0x07 Eclipse
Eclipse+CDT实现C/C++编程，并修改配置以调试ns-3。
1. 安装Eclipse
```
yogy@kali:~$ sudo apt-get install eclipse eclipse-cdt eclipse-cdt-pkg-config
```
2. [配置用于ns-3][11]
 * 新建ns-3项目
> 
New -- C++ Project
Project name: ns-3.23
Location: /home/yogy/Workspace/ns-allinone-3.23/ns-3.23
  * 配置Waf编译器
> 
Builder Settings:
Build command: ${workspace_loc:/ns-3.23}/waf 
Build directory: ${workspace_loc:/ns-3.23}/build
Behaviour:
Build(Incremental Build): all --> build
  * 配置调试器
> 
Run -- Debug Configurations:
C/C++ Application: build/src/ndnSIM/examples/ns3-dev-ndn-tree-cs-tracers-debug
Project: ns-3.23
Environment -- New:
Variable: LD_LIBRARY_PATH
Value: ${workspace_loc:/ns-3.23}/build

# 0x08 Tex
[Tex][12]是一套优秀的电子排版系统，常用于论文写作。

1. 安装TeXLive
  * 下载[texlive2015.iso][13]
  * 挂载镜像
```
yogy@kali:~/Downloads$ sudo mount -o loop texlive2015.iso  /mnt/
yogy@kali:~/Downloads$ cd /mnt
yogy@kali:/mnt# ./install-tl
```
 * 修改环境变量
```
yogy@kali:~$ vim ~/.bashrc
```
> 
\# TeX Live 2015export 
MANPATH=${MANPATH}:/usr/local/texlive/2015/texmf-dist/doc/manexport INFOPATH=${INFOPATH}:/usr/local/texlive/2015/texmf-dist/doc/infoexport PATH=${PATH}:/usr/local/texlive/2015/bin/x86_64-linux
2. 添加字体
```
yogy@kali:~$ sudo apt-get install ttf-wqy-microhei ttf-wqy-zenhei xfonts-wqy
yogy@kali:~$ cp /home/yogy/Downloads/fonts/* ~/.fonts/
```
3. 安装TeXstudio
```
yogy@kali:~$ sudo apt-get install exstudio
```

# 0x09 WPS
不稳定，用于临时查看 *.doc / \*.ppt / .\*xls。
1. 安装32位框架
```
yogy@kali:~$ sudo dpkg --add-architecture i386
yogy@kali:~$ dpkg --print-architecture
amd64
yogy@kali:~$ dpkg --print-foreign-architectures
i386
yogy@kali:~$ sudo apt-get update && sudo apt-get upgrade
yogy@kali:~$ sudo apt-get -f install 
yogy@kali:~$ sudo apt-get install libc6-i386 ia32-libs libnotify-bin ia32-libs-gtk
```
2. 下载并安装WPS
```
yogy@kali:~/Downloads$ wget http://wdl1.cache.wps.cn/wps/download/Linux/unstable/wps-office_8.1.0.3724~b1p2_i386.deb
yogy@kali:~/Downloads$ sudo dpkg -i wps-office_8.1.0.3724-b1p2_i386.deb
```
3. 添加缺失字体
```
yogy@kali:~/Downloads$ cp {Wingdings\ 2.ttf,Wingdings\ 3.ttf,Wingdings.ttf,webdings.ttf,MTExtra.ttf} ~/.fonts/
yogy@kali:~/Downloads$ sudo fc-cache -fv
```

# 0x0a Audacious
[Audacious][14]是一个支持多种格式轻巧快速的音乐播放器，可解决多数外文乱码问题。
1. 安装
```
yogy@kali:~$ sudo apt-get install audacious
```
2. 配置
外观 -- 界面: Winamp Classic Interface
外观 -- 界面设置 -- 使用点阵字体：取消
首选项 -- 播放列表：
自动检测下列编码: 汉语
备用字符编码: GBK
3. 播放列表为 *.m3u

# 0x0b Wine
[Wine][16]是一个能够在多种POSIX-compliant操作系统（诸如 Linux，Mac OSX 及 BSD 等）上运行 Windows 应用的兼容层。
1. 添加32位框架支持
```
yogy@kali:~$ sudo  dpkg --add-architecture i386
yogy@kali:~$ sudo  apt-get update
```
2. 安装32位Wine
```
yogy@kali:~$ sudo  apt-get install wine-bin:i386
```

# 0x0c MongoDB
[MongoDB][17]是开源文档型数据库，是非关系型数据库（NoSql）中流行的一种。
1. 添加源及密钥
```
yogy@kali:~$ echo "deb http://repo.mongodb.org/apt/debian wheezy/mongodb-org/3.0 main" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.0.list
yogy@kali:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 7F0CEB10
``` 
2. 更新源并安装
```
yogy@kali:~$ sudo apt-get update
yogy@kali:~$ sudo apt-get install -y mongodb-org
```
3. 禁止版本更新
```
yogy@kali:~$ echo "mongodb-org hold" | sudo dpkg --set-selections
yogy@kali:~$ echo "mongodb-org-server hold" | sudo dpkg --set-selections
yogy@kali:~$ echo "mongodb-org-shell hold" | sudo dpkg --set-selections
yogy@kali:~$ echo "mongodb-org-mongos hold" | sudo dpkg --set-selections
yogy@kali:~$ echo "mongodb-org-tools hold" | sudo dpkg --set-selections
```
4. 运行
 * 启动
```
yogy@kali:~$ sudo service mongod start
```
 * 验证
```
yogy@kali:~$ sudo vim /var/log/mongodb/mongod.log
```
> 2015-08-27T20:49:03.357+0800 I JOURNAL  [initandlisten] journal dir=/var/lib/mongodb/journal
...
2015-08-27T20:49:03.764+0800 I NETWORK  [initandlisten] waiting for connections on port 27017

 * 终止
```
yogy@kali:~$ sudo service mongod stop
```

# 0x0d GitHub
作为开源代码库以及版本控制系统，[Github][18]拥有140多万开发者用户。
1. 建立Git
```
yogy@kali:~$ sudo apt-get install git
yogy@kali:~$ git config --global user.name "yogykwan"
yogy@kali:~$ git config --global user.email "jingg.cxy@foxmail.com"
```
2. HTTPS认证
 * 
```
yogy@kali:~$ git config --global credential.helper cache
yogy@kali:~$ git config --global credential.helper 'cache --timeout=3600'
```
3. SSH认证
   * 确认已有ssh key ```ls -al ~/.ssh```
   2. 生成密钥 ```ssh-keygen -t rsa -b 4096 -C "jingg.cxy@foxmail.com"```
   3. 确认开启ssh ```eval "$(ssh-agent -s)"```
   4. 本地添加密钥 ```ssh-add /home/yogy/.ssh/id_rsa```
   5. 远端添加密钥，将~/.ssh/id_rsa.pub内容复制到[SSH keys][19]
   6. 测试连接 ```ssh -T git@github.com```

# 0x0e Webstorm
与Pycharm同属Jetbrains旗下，主要用于开发Javascript，Web前端开发神器。
1. 下载并安装
```
yogy@kali:~/Downloads$ wget http://download-cf.jetbrains.com/webstorm/WebStorm-10.0.4.tar.gz
yogy@kali:~/Downloads$ sudo tar -zxvf WebStorm-10.0.4.tar.gz
yogy@kali:~/Downloads$ sudo cp -r WebStorm-141.1550 /opt/
```
2. 获取注册码
Jetbrains旗下产品，学生可通过University email address、ISIC/ITIC membership、Official document三种方式[免费申请][9]。
3. 创建快捷方式
  * 手动创建
```
yogy@kali:/usr/share/applications$ sudo gedit jetbrains-webstorm.desktop
```
> 
[Desktop Entry]
Version=1.0
Type=Application
Name=WebStorm
Icon=/opt/WebStorm-141.1550/bin/webide.png
Exec="/opt/WebStorm-141.1550/bin/webstorm.sh" %f
Comment=Develop with pleasure!
Categories=Development;IDE;
Terminal=false
StartupWMClass=jetbrains-webstorm

  * 软件创建
Configure -- Creat Desktop Entry
4. 安装SASS
```
yogy@kali:/$ sudo su -c "gem install sass"
```

# 0x0f µTorrent
µTorrent是各大BT网站指定下载工具。
1. [下载][20]并解压
2. 添加配置文件
```
yogy@kali:~/utorrent-server-alpha-v3_3$ vim utserver.conf
``` 
> 
\#Internal Settings
ut_webui_port: 8080
dir_active: /home/yogy/PT/.tmp/
dir_completed: /home/yogy/PT/
preferred_interface: eth0
\#Regular Settings
\#传入链接所使用的端口
bind_port: 5158
\#最大上传速度（kb/s）
max_ul_rate: 50000
\#最大下载速度(kb/s)
max_dl_rate: 50000
\#全局最大链接数
max_total_connections: 800
\#每个Torrent的最大链接数
conns_per_torrent: 500
\#每个Torrent的上传通道数
ul_slots_per_torrent: 6
3. 运行```./utserver``` 
4. 打开[WebUI][21]，登录admin账户（无密码）
5. 添加从PT网站下载的.torrent种子文件


# 0x10 一键安装
```
yogy@kali:~$ sudo apt-get install gimp #图片
yogy@kali:~$ sudo apt-get install okular #PDF
yogy@kali:~$ sudo apt-get install smplayer #视频
```

# 0x11 结束语
常用软件记录完毕，Kali特性待另开新篇。
![Kali Linux](http://upload-images.jianshu.io/upload_images/177786-925e79600d260b6c.png)
***转载请注明出处***

[1]: http://www.nongnu.org/synaptic/
[2]: http://chicagovps.net/
[3]: http://www.oberhumer.com/opensource/lzo/download/lzo-2.09.tar.gz
[4]: http://www.openssl.org/source/openssl-1.0.2c.tar.gz
[5]: http://download.csdn.net/detail/alex198211/3207791
[6]: https://www.virtualbox.org/
[7]: http://www.codeblocks.org/downloads/26#linux64
[8]: https://translations.launchpad.net/codeblocks
[9]: https://www.jetbrains.com/shop/eform/students
[10]: https://www.nsnam.org/
[11]: https://www.nsnam.org/wiki/HOWTO_configure_Eclipse_with_ns-3
[12]: http://www.ctex.org/TeX/
[13]: http://mirrors.ustc.edu.cn/CTAN/systems/texlive/Images/texlive2015.iso
[14]: http://audacious-media-player.org/
[15]: http://www.virtualbox.org/wiki/Downloads
[16]: https://www.winehq.org/
[17]: http://docs.mongodb.org/manual/
[18]: https://github.com
[19]: https://github.com/settings/ssh
[20]: http://www.utorrent.com/intl/zh_cn/downloads/linux
[21]: http://localhost:8080/gui/web/index.html
