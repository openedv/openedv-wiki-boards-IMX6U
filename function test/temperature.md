---
title: '温度传感器'
sidebar_position: 10
---

# 温度传感器

I.MX6U芯片内部内置有温度传感器，可以实时反映I.MX6U CPU的内部温度

```c#
cat /sys/class/thermal/thermal_zone0/temp
```

![3.10.1](./img/3.10.1.png)

温度值即为 51.440℃（51440/1000）。



