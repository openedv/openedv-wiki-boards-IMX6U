---
title: '3.13 USB接口测试'
sidebar_position: 13
---

# 3.13 USB接口测试

ALPHA底板USB/OTG接口说明：
+ USB_HOST1~USB_HOST3为HOST模式，默认为HOST模式；
+ USB1_HOST支持 HOST模式；USB_OTG1支持切换为 HOST/DEVICE 

Mini底板只有一个USB_HOST

## 3.13.1 HOST模式读写测试

以下实验根据使用的U盘或TF卡的不同和实验环境不同，测试结果会有所差异。
将U盘 或TF卡用读卡器插到开发板 USB_HOST1~USB_HOST3/USB1_HOST其中一个接口。

插入后会打印如下信息，可以从中看到 U 盘大小和挂载名，如下图所示：

![3.13.1](./img/3.13.1.png)

使用df -h 查看U盘的挂载路径，可以看到下图U盘已经挂载在/run/media/下，挂载名为sda。

```c#
df -h
```

![3.13.2](./img/3.13.2.png)

写速度测试：
```c#
time dd if=/dev/zero of=/run/media/sda/test bs=1024k count=100 conv=fdatasync
```

![3.13.3](./img/3.13.3.png)

本次写100MiB，速度为15.9 MB/s。

读速度测试：
小提示：
因为LINUX的内核机制，一般情况下不需要特意去释放已经使用的cache。这些cache内容可以增加文件的读写速度。

执行下面指令清除缓存。
```c#
echo 3 > /proc/sys/vm/drop_caches
```
执行下面的指令读取前面用dd指令写入的test文件。
```c#
time dd if=/run/media/sda1/test of=/dev/null bs=1024k
```

![3.13.4](./img/3.13.4.png)

这里一共读出了100 MiB test文件，速度为18.1 MB/s。

## 3.13.2 DEVICE模式测试

本实验将TF卡的第一个分区“boot”分区模拟成U盘，请使用一根USB转串口线接在USB_OTG1处，并连接PC端USB接口。在串口终端执行下面指令，就可以将开发板的TF卡模拟成U盘挂载在PC上。

```c#
modprobe g_mass_storage file=/dev/mmcblk0p1 removable=1
```

![3.13.5](./img/3.13.5.png)

如下图，已经将TF卡的第一个分区成功的挂载在PC上。可以当作U盘一样使用。

![3.13.6](./img/3.13.6.png)

## 3.13.3 USB SERIAL测试

本实验将USB_OTG1当作串口使用。将另一根USB转串口线接到USB_OTG1处，然后连接PC，在串口终端下执行如下指令。(注:如果使用了上小节的DEVICE模式，需要重启开发板再做此实验)。

```c#
modprobe g_serial
```

![3.13.7](./img/3.13.7.png)

查看是否生成/dev/ttyGS0节点。
```c#
ls /dev/ttyGS0
```

![3.13.8](./img/3.13.8.png)

同时可以在PC设备管理器处，查看端口号

![3.13.9](./img/3.13.9.png)

开启守护进程。
```c#
setsid getty 115200 /dev/ttyGS0 
```

![3.13.10](./img/3.13.10.png)

然后用SecureCRT或者MobaXterm软件工具连接到该端口号。打开串口调试终端，选择正确的 COM 口，波特率为 115200，8N1，无检验位，并建立串口连接，按下回车键，可以后其他串口终端一样使用了。






