---
title: '3.2 按键测试'
sidebar_position: 2
---

# 3.2 按键测试

&emsp;&emsp;底板上按键对应的管脚关系如下：

<div class="center-table-div">
<table class="center-table">
  <tr>
    <th>开发板</th>
    <th>GPIO18</th>
  </tr>
  <tr>
    <td>ALPHA/Mini</td>
    <td>KEY0</td>
  </tr>
</table>
</div>

&emsp;&emsp;进入开发板系统，在串口终端执行如下指令查看按键所对应的输入事件。

```c#
lsinput
```

<center>
![3.2.1](./img/3.2.1.png)<br />
图3.2 1 查看按键的输入事件
</center>

&emsp;&emsp;可以从上图看出按键事件号为 event2，触摸屏占用了event1，所以当触摸屏没有插上时按键事件号为不一定为 event2！执行下面的指令，进行按键测试，按下底板上的KEY0，打印出按键输入事件的信息如下，按“Ctrl + c”终止指令。

&emsp;&emsp;指令提示：hexdump 或者od -x指令都是以十六进制的形式打印出输入事件信息。由于文件系统没提供hexpdump指令，所以只测试od指令。


```c#
od -x /dev/input/event2
```

<center>
![3.2.2](./img/3.2.2.png)<br />
图3.2 2 打印按键输入事件的信息
</center>





