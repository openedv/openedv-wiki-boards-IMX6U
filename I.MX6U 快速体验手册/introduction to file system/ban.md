---
title: '5.3 如何禁用Qt桌面启动'
sidebar_position: 3
---

# 5.3 如何禁用Qt桌面启动

&emsp;&emsp;在出厂文件系统/etc/rc.local文件里，如下图。不需要启动 Qt 界面，注意在2024年12月，最新的出厂系统UI由QDesktop改名为systemui。

&emsp;&emsp;可以在/opt/ui/systemui >/dev/null 2>&1 &行首前面加“#”注释掉这个指令即可。想要开启时再去除除“#”即可。

<center>
![5.3.1](./img/5.3.1.png)<br />
图5.3 1 查看出厂Qt GUI界面启动指令
</center>