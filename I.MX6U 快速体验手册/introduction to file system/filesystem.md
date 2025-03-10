---
title: '5.1 文件系统目录简介'
sidebar_position: 1
---

# 5.1 文件系统目录简介

&emsp;&emsp;ATK-IMX6U 出厂 Qt 文件系统目录简介:

| **目录** | **目录功能或放置的内容**                                     |
| :------: | :----------------------------------------------------------- |
| /bin     | 系统放置了许多执行文件，如mv、cp、date等指令，这些指令一般是单用户维护模式使用，还可以被root用户使用 |
| /boot    | boot目录一般放开机启动文件，但是I.MX6U已经有单独一个分区boot存储启动文件（zImage和设备树dtb文件） |
| /dev     | Linux系统使用任何设备与接口都是以文件的形式存放在这个目录下，在Linux下一切皆文件 |
| /etc     | 系统配置文件几乎都放在这个目录，例如启动脚本及所有的服务文件等 |
| /home    | 默认用户主文件夹，默认存在root用户。新建的用户都会在此生成用户主文件夹 |
| /lib     | 系统函数库，及内核模块modules（驱动程序）                    |
| /mnt     | 一般用于临时挂载目录                                         |
| /opt     | 第三方软件放置的目录，所以出厂Qt应用程序及所用到歌曲歌词等都放在这个目录下 |
| /proc    | 此目录是一个虚拟的文件系统，它的数据在内存中，如内核、进程、外部设备和网络状态等，所以不占磁盘空间 |
| /run     | 放置系统运行时所需要文件，以前防止在/var/run中，后来拆分成独立的/run目录。重启后重新生成对应的目录数据 |
| /sbin    | 放置sbin目录下的指令是系统指令，只有root用户可以执行         |
| /sys     | 与/proc目录一样，是虚拟的文件系统，记录核心系统的硬件信息    |
| /tmp     | 存放临时文件目录                                             |
| /usr     | Linux核心目录，目录下包括非常多的文件，如共享文件，一些可执行文件等等 |
| /var     | 存放系统执行过程经常改变的文件                               |

