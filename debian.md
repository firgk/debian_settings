# debian_settings

      windows 转 debian，遇到的问题 和 从0到1 的配置


# todo



语音输入工具

鼠标指针黏文件

添加 右键运行sh文件 快捷键

有概率蓝牙鼠标 被重置 灵敏度







# 基础

## install

      English version

      default partition

      xfce 


## xfce and system setting

      换源
      change /etc/apt/sourcelist : sudo vim /etc/apt/sources.list
      sudo apt update
      sudo apt install vim

      安装中文输入法 sudo apt install ibus-pinyin
      彻底关闭输入法， 或者重启系统
      在ibus-setup 中 添加中文输入法， 并且切换输入法切换



### 设置中设置

      优化缩放 appearnace 》 fonts 》 120
      黑色主题 appearnce 》 style adwaita-dark

      terminal preference > show unsafe past dialog 关闭
      terminal preference > appearnce 换个加粗的字体

      window manager tweaks > workspace > use the muouse wheel on .... 关闭

      workspace > number of workspaces > 7

      pannel > 删除panel2
      pannel 》 items 》 clock 》Time only 》 front
      pannel 》 items 》 clock 》 front 》 14 bold
      pannel 》 items 》 power manager 》 percetage

      mouse
      touchpad 》 reverse scroll direction
      touchpad 》 touchapd > tap touchpad to click

      window manager > button layout
      window manager > title left



### 快捷键

      window manager > keyboard 
      keyboard > xfce-appfinder



## 基础软件


      修复依赖
      apt get install -f
         sudo apt --fix-broken install


      删除软件
      
         删除配置
         sudo apt purge XXXX
         
         不删除配置
         apt remove XXXX
	



      deb 包
      clash-verge
      google-chrome-stable

         使用插件 Omega

         代理地址
         https://github.com/FelisCatus/SwitchyOmega/wiki/GFWList


      simplenote
      vscode
         drawio integration
         mysql 连接工具 https://database-client.com/#/home







## 添加某个目录到环境变量

      .bashrc
      export PATH="$PATH:~/bin"


## 环境变量

	/etc/profile
	.bashrc
	
## small

      不要开启 save session for future logins


# 系统优化





## 开始菜单管理


	使用 LXMenuEditor
	LXMenuEditor 对 debian 支持有问题，启动脚本有问题
	本质是 jar 包，直接使用 java -jar 启动
	
	没有修改权限，使用 sudo 即可






## 切换系统语言

	sudo dpkg-reconfigure locales
	第一步，第二步都选择中文即可
		如果第一步选过，只是选择第二步就可以


## 窗口栏 同种类型但是会聚合显示

	窗口设置中可以修改


## 剪切版候选

使用 `fcitx 5` 自带的
右键状态栏舒服法,点击设置
在 `addons` 栏下　的　`Module`  `Clipboard`
定义一个快捷键就可以了


## 丢失记忆的大小

最大化之后关闭软件，之后再次打开会丢失记忆的大小

	其实是支持的，但是qq 微信 不支持
	系统软件支持


## 鼠标轮询率

	仍然存在 蓝牙鼠标休眠的问题

	在系统的蓝牙设备管理器当中查看当前蓝牙鼠标的地址，地址字段类似于 D3:77:66:C8:FE:53。然后在超级用户的状态下修改 /var/lib/bluetooth/<mac-of-your-adapter>/<mac-of-your-mouse>/info，添加以下字段：
	
	一般情况，系统上只有一个蓝牙适配器，<mac-of-your-adapter> 是可以直接使用 Tab 键来补全的，你只需要根据之前查看到的蓝牙鼠标地址替换掉 <mac-of-your-mouse> 就可以了。
	
	[ConnectionParameters]
	MinInterval=6
	MaxInterval=9
	Latency=44
	Timeout=216
	通常 Linux 下的蓝牙设备是不会自动连接的，可以通过在 /etc/bluetooth/main.conf 的 [Policy] 下添加 AutoEnable=true 将蓝牙设备设置为开机自动连接。
	
	关于轮询率和轮询间隔
	设备的轮询率（单位 Hz）取决于轮询间隔，轮询间隔以毫秒为单位进行测量，等于滞后时间。
	
	默认的轮询间隔一般为 10ms，但是 USB 控制器一般会向下取最近的 2 的整数次幂，所以 10ms 的轮询时间实际上是 8ms 的轮询时间。
	
	下面是几个常用轮询率与轮询间隔的对应表（速率 = 1000/轮询间隔）：
	
	轮询率（Hz）	1000	500	250	125
	轮询间隔（ms）	1	2	4	8
	如果是进行一些精度较高的活动时，可以把轮询间隔尽可能地调得小一些，不过这么做同时也会加重 CPU 的负担。
	
	
	### 如何显示原始的内核消息
	启动时按 "Home" 或 "Escape" 按键会显示内核消息
	






## 终端代理

一次性

      export http_proxy=http://127.0.0.1:7897
      export https_proxy=http://127.0.0.1:7897

      unset http_proxy
      unset https_proxy


使用脚本

	cla
      export http_proxy=http://127.0.0.1:7897
      export https_proxy=http://127.0.0.1:7897
	uncla
      unset http_proxy
      unset https_proxy

启动代理
	source cla
	
关闭代理
	source uncla









## 蓝牙耳机问题

      https://www.cnblogs.com/rookieagle/p/18098106
      pipewire替代pulseaudio


      检测你的声音服务器 不是 pipewire 就要安装
      pactl info

      下载 bluez-firmware 和 firmware-iwlwifi
      bluez-firmware package for dongles based on the Broadcom BCM203x and Raspberry Pi chipset
      firmware-iwlwifi for Intel wireless cards
      安装蓝牙
      使用蓝牙耳机连接debian 12，首先要安装blueman，也要安装libspa-0.2-bluetooth，否则会报错 连接失败： br-connection-profile-unavailable

      启用pipewire替换pulseaudio
      sudo apt remove pulseaudio # 卸载 pulseaudio
      sudo apt install pipewire
      sudo apt install wireplumber
      sudo apt install pipewire-pulse
      systemctl --user --now enable wireplumber.service #直接使用user执行，不要使用root权限执行！



## 时间错乱

      sudo  apt-get install ntpdate
      sudo ntpdate ntp.aliyun.com

      可选 同步到主板

      hwclock --systohc


## 修改系统语言

      sudo dpkg-reconfigure locales





## wifi管理

自带的bar




### 查看网关

ip r



## 禁用 alt + 滚轮 放大桌面

要在 xfce4 的 gui 中禁用此设置，请执行以下操作：

1. 在出现的“Application Finder”窗口中，键入：xfwm4-tweaks-settings ( 或者在设置中找到   windows manager tweak) 
2. 单击“合成器”选项卡
3. 取消选中“使用鼠标滚轮缩放桌面”
4. 点击“关闭”


## 如何在XFCE中双击运行.sh文件

今晚遇到了同样的问题，经过一番挖掘终于解决了！（手机上可能格式有些怪异）

1. 确保你有适当的`#!/bin/bash`。
2. 右键单击文件->权限->选中"允许作为程序运行"。
3. 1 ) 进入xfce4-settings-edito。 2）右侧菜单中点击Thunar。 3）点击“新建”，将类型设置为布尔值true，属性设置为`/smisc-exec-shell-scripts-by-default`。 **无论哪种方式，请确保您没有打开文件管理器/Thunar窗口**





## 解决 Linux 系统卡死问题 (桌面环境卡死)

### 首选

在使用 Linux 系统时，有时会遇到系统卡死的情况。以下是一些常见的解决方法。
1. 使用 `Ctrl + Alt + F1-F6`  (随便选一个: 例如 `Ctrl + Alt + F2`) 切换到文字界面
2. top 查看并且杀死进程

	kill -9  PID
	pkill thunar


### 重启系统

使用 Magic SysRq 键重启系统
长按电源键 重启系统






## 迁移系统



```

dd if=/dev/nvme0n1p1 of=/dev/sda1 bs=4M status=progress
if 输入设备
of 输出设备
bs 块大小
status 显示状态


使用Ctrl+C终止命令
当dd命令正在执行时，可以按下键盘上的Ctrl+C组合键来终止命令的执行。这将立即停止dd命令的运行并退出。


可以按下键盘上的Ctrl+Z组合键来暂停dd命令的执行。这将把dd命令放入后台，并暂停它的运行。然后可以使用命令”jobs”来查看暂停的任务，或使用命令”fg”将其从后台恢复到前台运行。




umount /dev/sdb1　　　　　　　　　// 记得在操作之前先卸载所有挂载
e2fsck -f /dev/sdb1    // 如果有提示 按 y 就可以
resize2fs /dev/sdb1
// resize2fs用来调整文件系统的大小, 之前操作的是分区的大小






休眠出现问题,调整一下 swapon swapoff 就可以了:
	对旧硬盘 swapoff ,之后对新的盘启用 swapon

```




## 排查开机启动项(todesk为例) systemctl级

	查找
	sudo systemctl --all | grep wps
	禁用
	systemctl stop todeskd.service
	移除
	sudo systemctl list-units --type=service | grep todesk




## 杀死后台进程的脚本


```
#!/bin/bash
# 查找wps进程的PID
wps_pid=$(ps -aux | grep wps | grep -v grep | awk '{print $2}')

# 如果找到wps的PID，则终止进程
if [ -n "$wps_pid" ]; then
    kill -9 $wps_pid
    echo "已终止 WPS 进程，PID 为 $wps_pid"
else
    echo "未找到 WPS 进程"
fi

```







# 美化


### xfce 更换主题

	放到
	～/.themes
	重启或者重新登录




## 美化登陆界面


### 图形化操作

用这个图形化界面操作

      sudo apt install lightdm-gtk-greeter-settings



LightDM 是一个独立于不同桌面环境的登录管理器，想对于 GDM，它比较轻便，并且可以方便的自定义主题，LightDM 由 Canonical 的 Robert Ancell 和这些贡献者共同开发，并在 Contributor License Agreement 许可证下发布，但其版权是归 Canonical 所有。

不依赖 Gnome
使用 webkit 来绘制主题
支持 Gtk 和 Qt
可以灵活自定义（GTK basic 主题，Ubuntu Precise unity 主题）

LightDM 从 Debian Wheezy 开始提供，使用 Jessie 和 Sid 仓库的版本也足够稳定。

要安装 LightDM，以超级用户 root 运行以下命令：

aptitude install lightdm

配置
LightDM 的配置文件是 /etc/lightdm/lightdm.conf，若要修改默认配置，最好先备份原始文件。

要更改当前默认登录管理器，以超级用户运行：

dpkg-reconfigure lightdm
如果不熟悉 LightDM，建议保留 GDM， slim 或者其他登录管理器作为备用。


启用自动登录
在 LightDM 配置文件里查找以下行，取消其注释，并根据自己喜好进行配置。


[SeatDefaults]
#autologin-user=
#autologin-user-timeout=0

更改登录管理器背景
Debian 的 LightDM GTK 登录背景是在 /etc/lightdm/lightdm-gtk-greeter.conf 里配置，里面配置的默认登录背景图片指向 /usr/share/images/desktop-base/desktop-background，这是一个由 update-alternatives 管理的链接。

因此，若要更改背景，可以从 /usr/share/images/desktop-base/ 找一些你喜欢的图片，然后使用 update-alternatives 来更改 desktop-background 组。


update-alternatives --config desktop-background

参见
lightdm - Debian 软件包

DisplayManager

github, github issue tracker 上的 LightDM

CategoryBootProcess

zh_CN/LightDM (最后修改时间 2019-12-22 08:09:38)

Debian privacy policy, Wiki team, bugs and config.Powered by MoinMoin and Python, with hosting provided by Metropolitan Area Network Darmstadt.







## 开机动画

debian 安装 plymouth 美化开机动画


      debian默认的开机动画，即在grub菜单之后，就是密密麻麻的文本流，显示的是内核消息。有时还能看到一些无伤大雅的报错或者警告信息，说实话我都不知道到底为什么？
      下载，请注意wiki里kde桌面的提醒
      sudo apt install plymouth plymouth-themes

      修改grub配置，建议修改前保存一下旧有配置
      sudo vim /etc/default/grub



      应用修改
      sudo update-grub2

      查看一下默认主题
      sudo plymouth-set-default-theme -l



      设置主题
      sudo plymouth-set-default-theme -R softwaves

      看看效果
      softwaves


      homeworld


      tribar 有点像centos7的启动动画…… 爱了爱了


      不试验了，花里胡哨，没啥用……
      么么哒……






## fcitx5 切换皮肤



**克隆项目**:

      git clone https://github.com/tonyfettes/fcitx5-nord.git

安装主题:

      mkdir -p ~/.local/share/fcitx5/themes/
      cd fcitx5-nord
      cp -r Nord-Dark/ Nord-Light/ ~/.local/share/fcitx5/themes/

启用主题:

      编辑~/.config/fcitx5/conf/classicui.conf文件，设置：
      Theme=Nord-Dark # 或 Theme=Nord-Light
      最后，重启Fcitx5：
      fcitx5 -r




# 软件


## 文本识别工具 

UmiOcr 


## 谷歌浏览器中文

      whereis google-chrome
      LANGUAGE=zh_cn google-chrome

或者 将系统语言设置为中文，浏览器界面也会变成中文


## 虚拟机 vitrual box

	dpkg -i 安装
	出现故障 需要删掉软盘， 之后正常
	
	
	分辨率和缩放有问题
	安装增强工具 注意安装过程 需要在windows资源管理器中打开一个iso安装
	
	
	连接usb设备
	1. 安装拓展工具
	在官网下载包
	转到 “文件(File)” > “工具(Tools)” > “扩展包管理器(Extension Pack Manager)”
	点击 “安装(Install)” 按钮
	2. 要在 VirtualBox 中使用 USB 驱动器，你的当前用户需要位于 vboxusers 组中
	`sudo usermod -aG vboxusers $USER`
	3. 关机之后设备usb设备中添加设备







## 录制

屏幕

      sudo apt install simplescreenrecorder



## 加密压缩和不加密压缩 zip unzip


      zip -r blog.zip blog/ 
      zip -r --password mypasscode blog.zip blog/




## 软件安装位置

/usr 系统级的目录，可以理解为 C:/Windows/ ， /usr/lib 可理解为 C:/Windows/System32 。

/usr/local 用户级的程序目录，可以理解为 C:/Progrem Files/ 。用户自己编译的软件默认会安装到这个目录下。

/opt 用户级的程序目录，可以理解为 D:/Software ， opt 有可选的意思，这里可以用于放置第三方大型软件（或游戏），当你不需要时，直接 rm -rf 掉即可。

在硬盘容量不够时，也可将 /opt 单独挂载到其他磁盘上使用。

源码放哪里？
/usr/src 系统级的源码目录。

/usr/local/src 用户级的源码目录。



## 资源监视器Bashtop



      sudo apt update
      sudo apt install git
      git clone https://github.com/aristocratos/bashtop.git
      cd bashtop/
      cd DEB
      sudo ./build

对于卸载，请使用以下命令：

      sudo ./build --remove






## 解压乱码
 安装

sudo apt-get install unar
1
2.列出压缩包内容

lsar test.zip
1
3.解压压缩包

unar test.zip
1
4.unar常用选项解释

-o

解释：指定解压结果保存的位置
unar test.zip -o /home/dir/

-e

解释：指定编码
unar -e GBK test.zip

-p

解释：指定解压密码
unar -p 123456 test.zip

3.解决linux解压压缩包中文文件名乱码问题

lsar test.zip

###若发现乱码，可指定压缩包文件名使用的编码格式##
lsar -e GB18030 test.zip

###若能正常列出文件名，可解压###
unar -e GB18030 test.zip





## 自定义添加软件到 application finder

位置

	/usr/share/applications/
 




## 调节cpu能耗 cpufreq

	sudo cpufreq-set -g performance
	sudo cpufreq-set -g powersave





## xfce自带的webdav

	dav://user@106.12.212.6:5244/dav/



## 快捷键映射工具

	ahk (autohotkey) for linux (github)
	
![](doc/ahk教程.pdf)

我的键位：

	!z::  
	Send !{Left}
	return
	
	!e::
	Send {Enter}
	return
	
	!r::
	Send {BackSpace}
	return
	
	!CapsLock::
	Send {Esc}
	return
	
	!1::
	Send {Left}
	return
	
	!2::
	Send {Right}
	return


## 硬盘管理 gui 软件

`sudo apt install gparted`





# 开发软件


## java

debian 系统下安装jdk1.8
第一步：下载安装包
下载Linux环境下的jdk8，请去（Java Downloads | Oracle）中下载jdk的安装文件；
由于我的Linux是64位的，因此我下载jdk-8u311-linux-x64.tar.gz


2
vi .bashrc
在文件末尾添加

	export JAVA_HOME=/etc/java/jdk1.8.0_311/
	export JRE_HOME=/etc/java/jdk1.8.0_311/jre
	export CLASSPATH=.:$CLASSPATH:$JAVA_HOME/lib:$JRE_HOME/lib
	export PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin


> 使用idea的内置的maven



## docker 

安装
看官方文档


配置加速

	sudo mkdir -p /etc/docker
	sudo vim /etc/docker/daemon.json


	{
	    "registry-mirrors": [
		"https://docker.1ms.run",
		"https://docker.xuanyuan.me"
	    ]
	}

	sudo systemctl daemon-reload
	sudo systemctl restart docker




## mysql docker 5.7


      docker run -d \
         --name mysql \
         -p 3306:3306 \
         -e TZ=Asia/Shanghai \
         -e MYSQL_ROOT_PASSWORD=123456 \
         mysql:5.7




> 连接工具
>  vscode 插件
> https://database-client.com/#/home




## python

`pip3 install `全局安装包有问题
使用创建虚拟环境 可以解决

	1
	在当前目录下创建名为 tempenv 的虚拟环境。
	python3 -m venv ./tempenv
	
	2
	切换路径 
	cd tempenv
	
	3
	激活虚拟环境
	source bin/activate
	
	4
	pip install flask
	
	5
	退出虚拟环境
	deactivate


## redis

参考官网安装，操作

	关闭
	sudo service redis-server stop
	1
	开启服务
	sudo servcie redis-server start
	1
	重启
	redis-server
	
	redis-cli

## sqlite图形化管理界面DB Browser for SQLite

	sudo apt-get install sqlitebrowser

支持导出`json`格式






