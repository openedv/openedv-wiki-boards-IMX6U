---
title: '3.9 查看系统信息'
sidebar_position: 9
---

# 3.9 查看系统信息

&emsp;&emsp;显示操作系统的内核版本号。

```c#
uname -a
```

<center>
![3.9.1](./img/3.9.1.png)<br />
图3.9 1显示内核版本号
</center>

&emsp;&emsp;查看系统主机名。

```c#
cat /etc/hostname
```

<center>
![3.9.2](./img/3.9.2.png)<br />
图3.9 2 查看系统主机名
</center>

&emsp;&emsp;查看系统登录开机信息，（备注：非自动登录时会打印开机信息）。

```c#
cat /etc/issue
```

<center>
![3.9.3](./img/3.9.3.png)<br />
图3.9 3 查看系统登录欢迎信息
</center>

&emsp;&emsp;查看CPU相关信息。

```c#
cat /proc/cpuinfo
```

<center>
![3.9.4](./img/3.9.4.png)<br />
图3.9 4 查看CPU相关信息
</center>

&emsp;&emsp;查看内存相关信息。

```c#
cat /proc/meminfo
```

<center>
![3.9.5](./img/3.9.5.png)<br />
图3.9 5 查看内存相关信息
</center>


