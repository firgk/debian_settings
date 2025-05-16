

### scrcpy
    
    SEO
    scrcpy 无线调试，记录设备
    无线调试不用每次都插线

有线连接

    直接插入就可以
    之后scrcpy

转无线连接

    scrcpy

    # adb启动一个ip地址
    ./adb tcpip 5555
    # 无线连接
    ./adb connect XXXXX:5555


连接一次之后，adb 就认证了设备
之后连接不上，是因为 adb tcpip 失效了
需要重新启用这个端口
即使是别的设备的 adb 命令也可以，只要启动端口就可以了

可以使用 termux app,这是一个shell终端，支持adb
adb tcpip 5555
之后电脑端直接就可以连上了
adb connect XXXX:5555


无线调试会断掉

    断开是因为 wifi 环境变化

