---
title: 'FlexCAN测试'
sidebar_position: 12
---

# FlexCAN测试

开发板底板有一路CAN（注：核心板支持两路，底板只能用一路，另一路被复用了）。要想测试CAN，用户手上需要有测试CAN的仪器，（否则需要用两块不同的开发板的CAN或者其他CAN设备测试）比如周立功的CAN分析仪、创芯科技的CAN分析仪和广成科技的CAN分析仪等。或者可用两个CAN设备对接相互收发。关于CAN仪器及CAN上位机的使用，请参照各厂商的使用说明书，如不会使用请咨询CAN分析仪厂家的技术支持。

CAN接口如下图，下图为ALPHA底板的位置，Mini底板CAN接口位置的不一样。

![3.12.1](./img/3.12.1.png)

测试前请使用CAN分析仪或者测试CAN的设备连接好I.MX6U底板的CAN，CANH接仪器的CANH，CANL接CAN仪器的CANL。

设置 can0 的 can 设备通信波特率为 1000000，也就是最大通信波特率1MBit/s。
```c#
ip link set can0 up type can bitrate 1000000 triple-sampling on
```

![3.12.2](./img/3.12.2.png)

使用candump指令接收来自can0的数据
(1)	-ta: t代表打印时间，a代表开启ASCII输出
candump -ta can0
使用cansend指令发送数据。
cansend can0 123#01.02.03.04.05.06.07.08
解释：
(1)	can0设备
(2)	123：帧ID
(3)	01.02.03.04.05.06.07.08：帧数据

如下图，使用创芯科技的CAN分析仪上面机界面与开发板收发数据如下。

![3.12.3](./img/3.12.3.png)



