---
title: '查看系统信息'
sidebar_position: 9
---

# 查看系统信息

显示操作系统的内核版本号。

```c#
uname -a
```

![3.9.1](./img/3.9.1.png)

查看系统主机名。
```c#
cat /etc/hostname
```

![3.9.2](./img/3.9.2.png)

查看系统登录开机信息，（备注：非自动登录时会打印开机信息）。
```c#
cat /etc/issue
```

![3.9.3](./img/3.9.3.png)

查看CPU相关信息。
```c#
cat /proc/cpuinfo
```

![3.9.4](./img/3.9.4.png)

查看内存相关信息。
```c#
cat /proc/meminfo
```

![3.9.5](./img/3.9.5.png)



