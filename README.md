# debian_settings

      debian配置，遇到的问题和记录


# 注意

      部分命令需要 sudo 权限,但是没有额外提醒



# todo

      语音输入工具

      鼠标指针黏文件

      添加 右键运行sh文件 快捷键

      有概率蓝牙鼠标 被重置 灵敏度

      系统级 深色遮罩处理

      linux 点击链接的时候 默认新窗口打开

            setting->default Appcalitions -> Others -> 
            搜索 html
            设置为 新的桌面文件 打开
            ！ 未尝试


            新的桌面文件如下：

            [Desktop Entry]
            Version=1.0
            Type=Application
            Name=chrome-new-window
            Comment=
            Exec=google-chrome  --new-window  %u
            Icon=09F1_360ChromeX.0
            Path=
            Terminal=false
            StartupNotify=false



## 已经完成

      图片 pdf 深色遮罩 
            atril document viewer 支持 pdf 颜色反转


      切换工作区，chrome 看视频的时候会有bug,直接切换到桌面了，无法对焦
            打开一个新的 chrome 页面（独立窗口），之后在他两个之前切换（使用 alt + tab ），就正常了。




# 基础




## install

      debian12

      English version

      default partition

      xfce 


## xfce and system setting

      换源
      change /etc/apt/sourcelist : sudo vim /etc/apt/sources.list
      sudo apt update
      sudo apt install vim


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




      ibus-pinyin
      安装中文输入法 sudo apt install ibus-pinyin
      彻底关闭输入法， 或者重启系统
      在ibus-setup 中 添加中文输入法， 并且切换输入法切换


      fictx5






### 解压和压缩

      tar -cvf yourfile.tar your_directory/

      tar -xvf yourfile.tar




## 添加某个目录到环境变量

      .bashrc
      export PATH="$PATH:~/bin"


## 环境变量

	/etc/profile
	.bashrc
	


# 系统优化





## 系统级监控和任务

查看电量
cat /sys/class/power_supply/BAT1/status

指定规则
vim /etc/udev/rules.d/myrules

写入规则
SUBSYSTEM=="power_supply", ATTR{status}=="Discharging", ATTR{capacity}=="[0-9]",  RUN+="/usr/bin/systemctl hibernate"




## 关闭 todesk 后台占用
systemctl stop todeskd.service


## 禁用 LightDM
sudo systemctl stop lightdm.service




## 如何在XFCE中显示桌面上的全名


在我的主目录中，我必须创建一个名为.gtkrc-2.0的文件，因为没有一个现有的文件。在这个新文件中，我输入并保存了以下内容：

	style "xfdesktop-icon-view" {
	    XfdesktopIconView::ellipsize-icon-labels = 0
	}
	widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"


随着向GTK 3的转换，GTK所需的CSS语法略有改变。我发现在~/.config/GTK-3.0/gtk.css上放置以下行可以解决这个问题：

	* {
	    -XfdesktopIconView-ellipsize-icon-labels: 0;
	}




### .desktop 文件



自定义图标
terminal=true 以窗口打开






## 双系统引导




### 让 Linux 的引导加载器（如 GRUB）引导 Windows

你想让 Linux 的引导加载器（如 GRUB）引导 Windows，这是很常见的 双系统设置需求。下面是完整的操作步骤，假设你已经安装了 Windows 和 Linux 双系统：

✅ 一、确认 GRUB 是否已经安装
如果你是先装的 Windows 后装的 Linux，一般 Linux 会自动安装 GRUB 并接管引导。
✅ 二、更新 GRUB 配置，添加 Windows 引导项
在 Linux 系统下执行：
sudo update-grub
这条命令会自动扫描所有已安装的系统（包括 Windows），并在 GRUB 菜单中添加它。
输出中你应该看到类似：
Found Windows Boot Manager on /dev/sda1
如果找到了，它就会被添加进 /boot/grub/grub.cfg 中，下次重启就可以看到 Windows 启动项了。
✅ 三、重启测试
重启电脑时，你应该看到 GRUB 的启动菜单中有一项是：
Windows Boot Manager (on /dev/sdX)
选择这项即可启动 Windows。



## 亮度调节


### xrandr
使用 xrandr | grep -v disconnected | grep connected命令查看连接的显示设备
调节亮度xrandr --output *** --brightness 0.5




### ddcutil（部分linux自带）

```
探测支持控制的显示器
ddcutil detect

设置屏幕亮度:
ddcutil setvcp 10 50
10 表示 设置亮度代码(code)， 50 表示需要调节的亮度(0-100)。

查看当前显示器亮度:
ddcutil getvcp 10

还支持设置一些其它参数， 具体支持的code可以用如下命令查看:
ddcutil vcpinfo
```


### 未查找到显示器
连接显示器后用 ddcutil detect 命令没有查找的显示器，可能是应为显示器的i2c驱动没有自动加载，可以用如下方式手动加载驱动:

      sudo modprobe i2c-dev



## 视频硬件加速

为 chrome 添加启动参数

VaAPI on Linux with Vulkan

	google-chrome-stable --use-gl=angle --use-angle=vulkan --enable-features=AcceleratedVideoEncoder,VaapiOnNvidiaGPUs,VaapiIgnoreDriverChecks,Vulkan,DefaultANGLEVulkan,VulkanFromANGLE --ignore-gpu-blocklist --disable-gpu-driver-bug-workaround






## 安全的卸载硬盘

      sudo fdisk -l
      gio mount -t /dev/sda




### udisksctl

      使用该命令需要先卸载挂载点，然后停止设备。使用 unmount 子命令卸载挂载点，使用 power-off 子命令可以设备：

      udisksctl unmount -b /dev/sdb1
      udisksctl unmount -b /dev/sdb2
      udisksctl unmount -b /dev/sdb3
      udisksctl power-off -b /dev/sdb






### apt install 工具添加网络代理

Create a new configuration file named proxy.conf.

	sudo touch /etc/apt/apt.conf.d/proxy.conf

Open the proxy.conf file in a text editor.

	sudo vim /etc/apt/apt.conf.d/proxy.conf

and then add the following lines.

	Acquire {
	  HTTP::proxy "http://127.0.0.1:8080";
	  HTTPS::proxy "http://127.0.0.1:8080";
	}








## 开始菜单管理


	使用 LXMenuEditor
	LXMenuEditor 对 debian 支持有问题，启动脚本有问题
	本质是 jar 包，直接使用 java -jar 启动
	
	没有修改权限，使用 sudo 即可



## 切换系统语言

	sudo dpkg-reconfigure locales
	第一步，第二步都选择中文即可
		如果第一步选过，只是选择第二步就可以


### 暂时切换语言

加参数

      export LANG=zh_CN.UTF-8
      export LANG=en_US.utf8


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






## 解决 Linux 系统卡死问题 (桌面环境卡死)

### 首选

在使用 Linux 系统时，有时会遇到系统卡死的情况。以下是一些常见的解决方法。
1. 使用 `Ctrl + Alt + F1-F6`  (随便选一个: 例如 `Ctrl + Alt + F2`) 切换到文字界面
2. top 查看并且杀死进程

	kill -9  PID
	pkill thunar


重启 桌面环境

	sudo systemctl restart lightdm.service


## thunar 使用 gvfs 因为挂载网络资源超时 卡死 

	systemctl --user restart gvfs-daemon.service




## 迁移系统

危险操作

从 nvme0n1p1  复制到 sda1 （移动硬盘）

```

查看
fdisk -l





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





休眠出现问题

调整一下 swapon swapoff 就可以了:

	对旧硬盘 swapoff ,之后对新的盘启用 swapon

或者

	修改两个UUID
	cat /etc/initramfs-tools/conf.d/resume
	vim /etc/default/grub
		GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ..."
	
	更新他俩个
	sudo update-initramfs -u
	sudo update-grub

```




## 排查开机启动项(todesk为例) systemctl级

	查找
	sudo systemctl --all | grep wps
	禁用
	systemctl stop todeskd.service
	移除
	sudo systemctl list-units --type=service | grep todesk





## 充电阈值控制 电源

	 Huawei MateBook 14 AMD (2020)
	 我的是荣耀 magicbook 2021 intel i5  14-inch

直接google 型号 + arch wiki 可以搜到

2025-05-04

	华为 WMI 驱动程序 `v3.3` 用于公开电池保护阈值，已合并到内核 `5.5`[[2]](https://github.com/aymanbagabas/Huawei-WMI)。 存在一个问题[[3]](https://github.com/nekr0z/matebook-applet/issues/22)，硬件报告的充电阈值不正确，阻止了电池保护功能的工作。 驱动程序的维护者表示，这应该在用户空间中修复[[4]](https://github.com/aymanbagabas/Huawei-WMI/issues/36#issuecomment-657127421)。
	
	一个临时的解决方法是将一些合理的数值写入文件
	
	# echo '40 70' > /sys/devices/platform/huawei-wmi/charge_control_thresholds
	
      or
      

	# vim /sys/devices/platform/huawei-wmi/charge_control_thresholds
      输入 40 70


	这将启用电池保护（在本例中，设备将在 70% 时停止充电）。 为了让 [matebook-applet](https://aur.archlinux.org/packages/matebook-applet/)AUR 在没有超级用户权限的情况下运行，请将您自己添加到 `huawei-wmi` [用户组](https://wiki.archlinux.org.cn/title/User_group "User group")，因为阈值对于非 root 用户仍然是只读的。
	


## 电源选项





### tlp

    sudo apt install tlp tlp-rdw
    
    systemctl status tlp
    tlp-stat -s  # 查看当前电源模式和配置状态
    tlp-stat -p  # 查看 CPU 相关配置

    vim /etc/tlp.conf


```
一、启用 TLP
默认已启用，无需修改：
ini
TLP_ENABLE=1  # 1=启用，0=禁用

电源模式切换
无需手动干预，TLP 会自动根据「插电 / 电池」切换模式：
ini
# TLP_DEFAULT_MODE=AC  # 仅用于无法检测电源的设备
# TLP_PERSISTENT_DEFAULT=0  # 0=自动切换，1=强制使用默认模式

二、CPU 能效优化（核心配置）
1. 频率调节策略
推荐保持默认（自动适配硬件），如需手动调整：

ini
# Intel 处理器（intel_pstate 驱动）推荐：
CPU_SCALING_GOVERNOR_ON_AC=performance    # 插电时高性能
CPU_SCALING_GOVERNOR_ON_BAT=powersave     # 电池时节能

# AMD 或旧 Intel 处理器（acpi-cpufreq 驱动）推荐：
# CPU_SCALING_GOVERNOR_ON_AC=schedutil
# CPU_SCALING_GOVERNOR_ON_BAT=schedutil

2. 性能限制（延长续航）
ini
# 电池模式下限制 CPU 最大性能（0-100%）
CPU_MAX_PERF_ON_BAT=70  # 例如限制到 70% 性能

# 禁用电池模式下的 Turbo Boost（超频）
CPU_BOOST_ON_BAT=0
3. 核心休眠（轻负载节能）
ini
SCHED_POWERSAVE_ON_BAT=1  # 1=轻负载时关闭部分核心

三、电池保护（延长电池寿命）
1. 充电阈值（仅限支持的设备，如联想 ThinkPad）
ini
# 充电到 80% 停止，低于 75% 开始充电（减少满电损耗）
START_CHARGE_THRESH_BAT0=75
STOP_CHARGE_THRESH_BAT0=80
2. 其他设备通用建议
ini
RESTORE_THRESHOLDS_ON_BAT=1  # 拔电时恢复默认充电阈值

四、硬盘与存储设备节能
硬盘休眠与功耗
ini
# 机械硬盘高级电源管理（128=中等节能，254=最大节能）
DISK_APM_LEVEL_ON_BAT="128"

# 固态/机械硬盘自动休眠超时（单位：秒）
AHCI_RUNTIME_PM_TIMEOUT=30  # 30秒无操作后休眠
```




###  cpufreq

      勿使用，使用下方 cpupower

      sudo cpufreq-set -g performance
      sudo cpufreq-set -g powersave

      效果不明显


### cpupower

简介：Linux 内核自带的 CPU 频率调节工具，可设置 CPU 性能模式（如节能、平衡、高性能）。


  cpupower frequency-info

  sudo cpupower frequency-set -g powersave
  sudo cpupower frequency-set -g performance
  sudo cpupower frequency-set -g ondemand






#### cpupower 限制 cpu 频率


      封装了cpureq
      效果明显



      限制 cpu 频率会导致 cpu 占用过高，进一步卡顿和升温
      合理的范围是必要的

      cpupower -c all frequency-set -f 2.4GHz
      设置CPU最小频率

      sudo  cpupower -c all frequency-set -d 1.4GHz
      设置CPU最大频率

      sudo  cpupower -c all frequency-set -u 1.6GHz






# 错误修复


      不要开启 save session for future logins



## 剪切板无法正确处理图片

xfce4-screenshooter 无法将图片直接复制到剪切板
也可以在 arch wiki 上检索到
大致的意思是 clipboard 问题，或者是 启动了多个 clipboard 进程
导致即使桌面状态栏退出了 clipboard 仍然不可用
解决方法是 在 setting -> session and startup 中关闭 clipboard 的开机启动，不使用它，或者开机后手动启动






Xfce4 screenshooter cannot copy pictures directly to the clipboard (copy to the clipboard)
It can also be retrieved on the arch wiki
The general meaning is the clipboard problem, or multiple clipboard processes have been started
As a result, even if the desktop status bar exits the clipboard, it is still unavailable
The solution is to turn off the startup of clipboard in setting ->session and startup, do not use it, or start it manually after startup







## 解压乱码

      unar 会自动检测编码
      sudo apt-get install unar

      使用:
      unar test.zip

      参数:
      -o
      解释：指定解压结果保存的位置
      unar test.zip -o /home/dir/

      -e
      解释：指定编码
      unar -e GBK test.zip

      -p
      解释：指定解压密码
      unar -p 123456 test.zip


再次乱码, 可以尝试


      lsar test.zip
      若发现乱码，可指定压缩包文件名使用的编码格式,并尝试几种
      lsar -e GB18030 test.zip

      若能正常列出文件名，可解压
      unar -e GB18030 test.zip








# 美化





## 登录界面的主题

是由root控制的

      sudo apt install materia-gtk-theme murrine-themes 




## 字体



### 默认的 
Monospace Font
Monospace Bold
10

注意，Monospace字体和Default字体可以不同，终端中要设置和系统字体相同
Monospace Bold


### 好看的

Andale Mono Bold
Default Font
Nimbus Sans Bold
10


Default Font
Sans Regular 10
Default Monospace Font
Monospace Regular 10



## 主题

      sudo apt install materia-gtk-theme papirus-icon-theme




### xfce 更换主题

	放到
	～/.themes
	重启或者重新登录




## 美化登陆界面


> 图形化 

用这个图形化界面操作 LightDM

      sudo apt install lightdm-gtk-greeter-settings

      apt install lightdm



> 手动 配置 LightDM


      LightDM 的配置文件是 /etc/lightdm/lightdm.conf，若要修改默认配置，最好先备份原始文件。
      dpkg-reconfigure lightdm

      启用自动登录
      在 LightDM 配置文件里查找以下行，取消其注释，并根据自己喜好进行配置。
      [SeatDefaults]
      #autologin-user=
      #autologin-user-timeout=0


      更改登录管理器背景
      Debian 的 LightDM GTK 登录背景是在 /etc/lightdm/lightdm-gtk-greeter.conf 里配置，里面配置的默认登录背景图片指向 /usr/share/images/desktop-base/desktop-background，这是一个由 update-alternatives 管理的链接。
      因此，若要更改背景，可以从 /usr/share/images/desktop-base/ 找一些你喜欢的图片，然后使用 update-alternatives 来更改 desktop-background 组。
      update-alternatives --config desktop-background






## 开机动画

debian 安装 plymouth 美化开机动画

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






## fcitx5 切换皮肤

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










## zsh

1. 安装
安装 zsh

2. 切换
chsh -s $(which zsh)
chsh -s /bin/bash
chsh -s /usr/bin/zsh

快捷键

1. 默认快捷键
→ (右方向键): 接受整个建议
Ctrl+F: 接受整个建议

2. 自定义快捷键
在 ~/.zshrc 文件中添加以下配置：

双击 Tab 接受建议

	bindkey '\t\t' autosuggest-accept

单击 Tab 逐词接受建议

	bindkey '^I' forward-word





## 堆叠式窗口管理器

      openbox
      .xsession

      exec openbox-session





## 支持 手动布局的资源管理器

nemo 用户可在图标视图下，通过菜单栏选择 “查看”>“排列项”>“手动”，或者右键单击空白处选择 “排列项”>“手动” 来实现。







## 计算器

      sudo apt install kalgebra




## 远程桌面


### 被控

      apt install xrdp


### rdp

xfreerdp3 /u:"username" /p:"password" /v:127.0.0.1 /cert:tofu /w:1920 /h:1025 /sound  


## wine

安装 wine 10.x


最佳兼容性

wincfg 其换成win7



使用wine时，中文字体会显示成方框□
网上下载 simsun.ttc

安装字体

1. 单独复制字体到wine容器 （推荐）
如果说是最后要把wine容器当成软件发行出去，那就需要把找来的字体文件粘贴到容器的drive_c\windows\Fonts目录。


2. 安装到Linux
deepin可以双击安装，网上有说复制到/usr/share/fonts的，没试过，不知道可不可以。一次安装完，以后本机用其他wine容器的时候也不需要再次操作，就可以正常显示。


改字体渲染引擎 （没试过）
到上面一步，wine的中文字体已经可以正常显示了，但是其中的字体渲染引擎却不尽人意，可以改一下函数库的riched20（管字体的，网上可以查）
先运行你的winecfg，像这样：

	env WINEPRIFIX=你的wine容器根目录 wine运行程序 winecfg

按我的就是（wineprefix的那个引号有空格就加，我这里是以防万一）：

	env WINEPREFIX="/home/deepin/wine/DocBox" deepin-wine6-stable winecfg

然后找到函数库，添加riched20(点击第二步的下拉框时选择riched20)

完成后就是原装先于内建，也可以按编辑改成原装，之后应用确定就行，在当前wine容器就生效了







## 本地 andorid 模拟器 (性能差，吃cpu）

```yml
https://github.com/budtmo/docker-android

docker run -d \
-p 6080:6080 \
-e EMULATOR_DEVICE="Samsung Galaxy S10" \
-e WEB_VNC=true \
--device /dev/kvm \
--name android-container \
-v data:/home/firgk/andorid \
budtmo/docker-android:emulator_11.0
```


## 文本识别工具

UmiOcr

https://github.com/pot-app/pot-desktop


## 谷歌浏览器中文


      找到谷歌浏览器启动项
      whereis google-chrome
            我的在 /usr/bin/google-chrome

      修改 /usr/bin/google-chrome 第一行添加 export LANGUAGE=zh_cn google-chrome


或者 将系统语言设置为中文，浏览器界面也会变成中文


## 虚拟机
### vitrual box

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


### kvm


一、检查虚拟化支持：lscpu | grep Virtualization

二、安装必要组件：

      sudo apt install virt-manager qemu-system qemu-utils libvirt-daemon-system

1. virt-manager： 图形界面
2. qemu-system：虚拟器，配合kvm，完成虚拟器功能
3. qemu-utils：处理器仿真器，比如模拟arm处理器
4. libvirt-daemon-system：提供API，使GUI能够和各类进程、服务通信

三、检查KVM：lsmod | grep -i kvm，也就是成功安装没有

四、启动：
virt-manager
应用图标启动

      qemu-kvm – 一个提供硬件仿真的开源仿真器和虚拟化包
      virt-manager – 一款通过 libvirt 守护进程，基于 QT 的图形界面的虚拟机管理工具
      libvirt-daemon-system – 为运行 libvirt 进程提供必要配置文件的工具
      virtinst – 一套为置备和修改虚拟机提供的命令行工具
      libvirt-clients – 一组客户端的库和API，用于从命令行管理和控制虚拟机和管理程序
      bridge-utils – 一套用于创建和管理桥接设备的工具


出中看到的，libvirt的默认网络处于非活动状态，因此通过运行以下命令使其处于活动状态，并在系统重新启动时自动重新启动：

      sudo virsh net-start default
      sudo virsh net-autostart default

启用虚拟化守护进程（libvirtd）：

      sudo systemctl status libvirtd
      sudo systemctl enable --now libvirtd
      sudo systemctl start libvirtd 



如果是在普通用户下操作的，将当前登录用户加入 kvm 和 libvirt 用户组，以便能够创建和管理虚拟机。

      sudo usermod -aG kvm $USER
      sudo usermod -aG libvirt $USER



sudo apt install qemu-kvm libvirt-clients libvirt-daemon-system bridge-utils virtinst libvirt-daemon



#### KVM启动虚拟机时报错Requested operation is not valid: network ‘default‘ is not active

      sudo virsh net-start default
      sudo virsh net-autostart default







## 录制

屏幕
      sudo apt install simplescreenrecorder



## 加密压缩和不加密压缩 zip unzip


      zip -r blog.zip blog/ 
      zip -r --password mypasscode blog.zip blog/




## 软件安装位置

      /usr 系统级的目录，可以理解为 C:/Windows/ ， /usr/lib 可理解为 C:/Windows/System32
      /usr/local 用户级的程序目录，可以理解为 C:/Progrem Files/ 。用户自己编译的软件默认会安装到这个目录下
      /opt 用户级的程序目录，可以理解为 D:/Software ， opt 有可选的意思，这里可以用于放置第三方大型软件

      源码放哪里
      /usr/src 系统级的源码目录
      /usr/local/src 用户级的源码目录


## 资源监视器 Bashtop

      sudo apt update
      sudo apt install git
      git clone https://github.com/aristocratos/bashtop.git
      cd bashtop/
      cd DEB
      sudo ./build

对于卸载，请使用以下命令：

      sudo ./build --remove



## 显示gpu

      使用 Intel-gpu-tools

      intel_gpu_top 即可查看




## 自定义添加软件到 application finder


位置

      home/XXXXX/.local/share/applications/ 



## xfce自带的webdav

	dav://user@106.12.111.6:5244/dav/


如果卡死

      重启 thuanr
      kill -HUP $(pgrep -i thunar)
      thunar --daemon &


      重启 thunar 的挂载模块
      systemctl --user restart gvfs-daemon.service






## 硬盘管理 gui 软件

`sudo apt install gparted`


## unzip解压 高级 部分解压

	
	1. 解压整个.zip文件：
	“`shell
	unzip file.zip
	“`
	
	2. 查看.zip文件中的文件列表：
	“`shell
	unzip -l file.zip
	“`
	这将列出.zip文件中的所有文件，并显示文件的详细信息，如文件名、压缩比、压缩时间等。
	
	3. 解压指定文件到当前目录：
	“`shell
	unzip file.zip file1
	“`
	这将只解压名为file1的文件到当前目录。
	
	4. 解压指定目录下的所有文件：
	“`shell
	unzip file.zip folder/*
	“`
	这将解压名为folder目录下的所有文件到当前目录。
	
	5. 解压.zip文件时排除指定文件或目录：
	“`shell
	unzip -x file.zip exclude1 exclude2
	“`
	这将解压.zip文件时排除名为exclude1和exclude2的文件或目录。
	
	6. 解压指定文件到指定目录：
	“`shell
	unzip file.zip -d target_folder file1
	“`
	这将只解压名为file1的文件到target_folder目录。
	
	以上是在Linux中解压.zip文件部分文件的命令示例。根据实际情况选择合适的命令来满足你的需求。


## winapps： 将 windows 虚拟机软件和 linux 融合



启动某个软件：

      /home/firgk/.local/bin/winapps manual C:\Windows\system32\cmd.exe
      /home/firgk/.local/bin/winapps manual C:\Program Files (x86)\Tencent\QQMusic\QQMusic.exe
      

一些个性化配置

      .local/bin/winapp







## 快捷键

      window manager > keyboard 
      keyboard > xfce-appfinder


### 快捷键映射工具


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

方式1：

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


方式2：

      sudo mkdir -p /etc/systemd/system/docker.service.d
      sudo touch /etc/systemd/system/docker.service.d/proxy.conf


      [Service]
      Environment="HTTP_PROXY=http://proxy.example.com:8080/"
      Environment="HTTPS_PROXY=http://proxy.example.com:8080/"
      Environment="NO_PROXY=localhost,127.0.0.1,.example.com"

      我的
      [Service]
      Environment="HTTP_PROXY=http://127.0.0.1:7897/"
      Environment="HTTPS_PROXY=http://127.0.0.1:7897/"





### docker 需要root

✅ 解决方案（无需重启）
1️⃣ 确保当前用户属于 docker 组
运行以下命令，检查用户是否属于 docker 组：

groups
如果 docker 不在输出中，手动添加当前用户到 docker 组：

sudo usermod -aG docker $USER
然后，手动刷新用户组（避免重新登录）：

newgrp docker
再次运行：

groups
如果 docker 现在出现在列表中，尝试：

docker ps



### 指定配置文件启动 docker

docker compose --file ~/.config/winapps/compose.yaml start
docker compose --file ~/.config/winapps/compose.yaml kill






## 一些 docker 镜像

      mysql docker 5.7
      docker run -d \
         --name mysql \
         -p 3306:3306 \
         -e TZ=Asia/Shanghai \
         -e MYSQL_ROOT_PASSWORD=123456 \
         mysql:5.7



### Docker Compose 更新容器的几种方法


1. 方法一：使用`docker-compose up -d`命令更新容器
对于一个已经在运行的Docker Compose应用程序，如果需要更新其中的某个容器，有以下几种方法：

方法一：使用docker-compose up -d命令更新容器
如果已经修改了docker-compose.yml文件，并且希望更新其中的某个容器，可以直接使用docker-compose up -d命令。
该命令会更新docker-compose.yml中修改过的服务，并根据修改的设置进行重新配置。例如：

	docker-compose up -d service-name

其中 service-name是需要更新的服务名


	docker compose --file ~/.config/winapps/compose.yaml  up -d


2. 方法二：使用docker-compose stop和docker-compose rm命令重新启动容器
如果需要完全重启一个容器，并清除其中的所有数据，可以使用以下两个命令：

docker-compose stop service-name
docker-compose rm -f service-name
docker-compose up -d service-name

这会停止并删除名为 service-name 的容器，并根据docker-compose.yml重新启动它。这种方法比较适用于需要对容器进行某些比较复杂的更改，或者在更新过程中出现了一些问题。








## mysql docker 5.7

      docker run -d \
         --name mysql \
         -p 3306:3306 \
         -e TZ=Asia/Shanghai \
         -e MYSQL_ROOT_PASSWORD=123456 \
         mysql:5.7




连接工具

      vscode 插件
      https://database-client.com/#/home




## python

`pip3 install `全局安装包有问题

使用创建虚拟环境 可以解决

	python3 -m venv ./tempenv
	cd tempenv
	source bin/activate
	pip install flask
	deactivate


## redis

参考官网安装，操作

	关闭
	sudo service redis-server stop
	开启服务
	sudo servcie redis-server start
	重启
	redis-server
      测试
	redis-cli
      set hello world
      get hello




## sqlite图形化管理界面DB Browser for SQLite

	sudo apt-get install sqlitebrowser

支持导出`json`格式





# 其他




# 一些测试和实验

虚拟机下 单核较卡顿
双核流畅 win10



