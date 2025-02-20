---
title: '3.25 RGB转HDMI模块测试'
sidebar_position: 25
---

# 3.25 RGB转HDMI模块测试

&emsp;&emsp;准备正点原子RGB-HDMI V1.3模块，模块需要另外购买，比较便宜，如下图，LCD接口在背面。搭配一段5cm左右的fpc软排线。

&emsp;&emsp;请不要使用长于5cm的fpc软排线，防止因为fpc软排线太长，信号受到干扰。RGB转HDMI需要使用RGB转HDMI的驱动，HDMI线连接显示器端支持热插拨。

&emsp;&emsp;所以在上电前需要连接好模块与支持HDMI的显示器。RGB转HDMI模块最大支持1366*768 60Hz输出。

&emsp;&emsp;因为IMX6U只支持1366*768 60Hz的LCD输出。分辨率再高时钟就会波形失真，不能高于这个分辨率。考虑到有些显示器不支持1366*768 60Hz的HDMI输入，所以我们出厂就配置了1280*720 60Hz，标准的720p的HDMI输出。

<center>
![3.25.1](./img/3.25.1.png)<br />
3.25 1 正点原子RGB转HDMI模块
</center>

&emsp;&emsp;和正点原子所有RGB屏一样，RGB转HDMI模块可以被出厂的系统识别，无需更换设备树。

&emsp;&emsp;先将显示器上电，用HMDI连接线连接模块与显示器。用5cm的fpc软排线接到模块上，接到开发板RGBLCD接口处。

&emsp;&emsp;开发板上电启动，HDMI就可以显示出图像了。（**注意事项:HDMI接口处一定要插到底**）.




