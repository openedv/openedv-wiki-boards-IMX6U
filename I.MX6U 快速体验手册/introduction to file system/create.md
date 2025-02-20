---
title: '5.4 如何创建自启动程序'
sidebar_position: 4
---

# 5.4 如何创建自启动程序

&emsp;&emsp;与出厂Qt UI一样，自启动脚本/程序指令可以放到`/etc/rc.local`这个文件里，因为`/etc/rc.local`是系统启动最后一个执行的。当然也可以放在/etc/rc5.文件夹下。

&emsp;&emsp;若要放在rc5.d文件夹下，请参考/etc/rc5.d文件里的自启动文件即可。笔者不推荐初学者使用，因为初学者容易做错。启动程序直接写在上一小节的`/etc/rc.local`里即可！
