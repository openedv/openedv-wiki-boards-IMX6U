---
title: 'LED 与蜂鸣器测试'
sidebar_position: 1
---

# LED 与蜂鸣器测试

说明：用户LED一个，蜂鸣器一个。开发板启动时，DS0作为心跳灯，用于指示系统的运行.

开发板与LED和蜂鸣器对应的管脚关系如下：

| 开发板     | GPIO03 | SNVS_TAMPER1 |
| ---------- | ------ | ------------ |
| ALPHA/Mini | DS0    | BEEP         |

进入开发板系统，在串口终端执行指令控制对应的IO来控制对应的器件：

开发板上启动后DS0默认是[heartbeat]模式，执行如下指令改变当前触发模式，改成[none]模式就可以通过指令来控制LED的亮灭了。

```c#
echo none > /sys/class/leds/sys-led/trigger    // 改变LED的触发模式
echo 1 > /sys/class/leds/sys-led/brightness    // 点亮LED
echo 0 > /sys/class/leds/sys-led/brightness    // 熄灭LED
```

![3.1.1](./img/3.1.1.png)

因为底板的蜂鸣器用配置成了gpio-leds模式，同理蜂鸣器也可以用这样的指令来控制，默认BEEP的触发模式为[none]。

```c#
echo 1 > /sys/class/leds/beep/brightness     // 鸣叫
echo 0 > /sys/class/leds/beep/brightness     // 关闭
```

![3.1.2](./img/3.1.2.png)






