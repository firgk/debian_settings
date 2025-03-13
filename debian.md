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



## 软件
deb 包
clash-verge
google-chrome-stable

simplenote
vscode
	drawio integration


修复依赖
apt get install -f
   sudo apt --fix-broken install



## 添加某个目录到环境变量
.bashrc
export PATH="$PATH:~/bin"



## small

### 不要开启
save session for future logins



### 如何显示原始的内核消息
启动时按 "Home" 或 "Escape" 按键会显示内核消息




## 谷歌浏览器中文
whereis google-chrome

LANGUAGE=zh_cn google-chrome









## 代理

## 终端


export http_proxy=http://127.0.0.1:7897
export https_proxy=http://127.0.0.1:7897

unset http_proxy
unset https_proxy



### 脚本

todo




### chrome代理
使用插件 Omega

代理地址
https://github.com/FelisCatus/SwitchyOmega/wiki/GFWList








### 蓝牙耳机问题

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





## 虚拟机 vitrual box
dpkg -i 安装
出现故障 需要删掉软盘， 之后正常



分辨率和缩放有问题
安装增强工具 注意安装过程 需要在windows资源管理器中打开一个iso安装




### 时间错乱
udo  apt-get install ntpdate
sudo ntpdate ntp.aliyun.com

可选 同步到主板

hwclock --systohc





## 美化

### xfce 更换主题
放到
～/.themes
重启或者重新登录




### 美化登陆界面


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




### 修改主题
用这个图形化界面操作
sudo apt install lightdm-gtk-greeter-settings





### 开机动画

sudo apt install plymouth plymouth-themes


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








## 修改系统语言

sudo dpkg-reconfigure locales








## wifi管理

自带的bar



## fcitx5 切换皮肤



1. **克隆项目**:
   ```sh
   git clone https://github.com/tonyfettes/fcitx5-nord.git
1
2
3
4
安装主题:
mkdir -p ~/.local/share/fcitx5/themes/
cd fcitx5-nord
cp -r Nord-Dark/ Nord-Light/ ~/.local/share/fcitx5/themes/
1
2
3
启用主题: 编辑~/.config/fcitx5/conf/classicui.conf文件，设置：
Theme=Nord-Dark # 或 Theme=Nord-Light
1
最后，重启Fcitx5：
fcitx5 -r




## 查看网关
ip r






# 软件

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







 