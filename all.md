重新配置电脑
backup




修改的目录

电脑的一些目录和修改
缓存目录
C:\ProgramData\OpenBoxLab\RaiDrive\Cache

手机的一些目录和修改
.aaastore
NS 游戏目录






两台电脑 1个nas 多个移动硬盘 1手机 1 pad
1 游戏本, 吃性能的不重要的东西
2 轻薄本 保持稳定,日常用的所有软件, 裸机安装, 尽量少安装
3 nas 存放资料，长期不用的资料
4 移动硬盘 存放资料
4 移动硬盘, linux 保持干净和纯洁的linux， 或者专注做某件事情的时候的linux
5 pad 画图 看视频 电子书 和访问nas 视图等用处








# 我的需要
windows 虚拟机
键盘映射工具
i3 或 多任务窗口
chrome
代理
启动器
中文输入法


























# windows



## 软件库
bilidownloader
chrome
thorium
laragon
Mobaxterm
RaiDrive
WizeTree





chrome 书签和密码同步

GIMP
OpenShotEditor
Everything
Ear.Trumpe




## 急切需要使用的软件

.vscode-mindmap
clashverge
chrome
7z
vscode
vmware
win10 或者linux测试环境
网盘迅雷百度等等




## win10设置和配置
主页中
关闭通知
多任务中的 浏览器窗口 和 时间线
关闭贴靠窗口的下边的三个选项

关闭跨设备共享
打开剪切板历史记录


关闭索引和隐私

设备中
关闭自动播放
关闭USB设备出现问题

个性化
显示桌面计算机

默认应用改为谷歌
隐私设置








# 其他理解

## nas
是一个图书馆 储藏室 是电子仓库


重要但是 没必要备份的文件
划分到 拷贝到nas 和 从nas 拷贝过来的 

一般文件分为
所有设备都应有一个backup,用来备份当前文件夹的文件,打压缩包之后拷贝到这个文件夹


之后再电脑上有一份backupall,这一份含有手机的,之后将这个被分到u盘或者nas



# 备份需要
手机备份


电脑备份







网站备份
chrome 书签和密码
有道云笔记
simplenote



# 开发环境

## windows

python
1 添加绿色版python 到环境变量
2 下载并使用脚本安装pip
此时还是无法运行pip
修改python38._pth文件
> 因为Python解释器启动一般会自动import site，并调用site.main()。而在windows的嵌入版中，使用了python38._pth来指定包的位置。而通过这种方式加载python为避免包冲突不会自动import site。
需要打开python根目录下的python38._pth文件，修改#import site为import site。




## linux
安装包之前试试 pacman -Sy 一下





