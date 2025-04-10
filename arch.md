
# arch linux

arch 配置
部分参照arch wiki
使用archinstall
首先联网 itwcl
之后下载中国源，(需要手动输入网址）
之后修改下载好的配置文件，去除#
使用archinstall
安装xfce界面
下载

参考arch wiki 本地化
中文乱码
1推荐使用UTF-8的locale，将en_US.UTF-8和zh_CN.UTF-8的注释从配置文件/etc/locale.gen去掉，即删除行首的#
2sudo locale-gen
3sudo pacman -S noto-fonts-cjk    这个是字体应该就可以了

安装 ibus 输入法， fcitx5无法使用 不知为何

火狐浏览器
pacman -S firefox

代理
pacman -S clash-verge

设置缩放后字体发虚
直接调整大小，而不进行缩放
在字体选项中

## 处理休眠，睡眠失败，繁琐。放弃转 debian

了解到arch 不稳


