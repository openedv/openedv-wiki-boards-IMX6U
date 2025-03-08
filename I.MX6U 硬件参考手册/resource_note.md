---
title: '1.2 正点原子I.MX6U-ALPHA开发板资源说明'
sidebar_position: 2
---

# 1.2 正点原子I.MX6U-ALPHA开发板资源说明

&emsp;&emsp;资源说明部分，这两个开发板我们将分为两个部分说明：硬件资源说明和软件资源说明。

## 1.2.1 I.MX6U-ALPHA硬件资源说明

&emsp;&emsp;这里我们首先详细介绍I.MX6U-ALPHA开发板的各个部分，我们将按逆时针的顺序依次介绍：

&emsp;&emsp;**1、CAN接口**<br />
&emsp;&emsp;这是开发板板载的CAN总线接口（CAN），通过**2个**端口和外部CAN总线连接，即`CANH`和`CANL`。这里提醒大家：CAN通信的时候，必须CANH接CANH，CANL接CANL，否则可能通信不正常！

&emsp;&emsp;**2、RS232/485选择接口**<br />
&emsp;&emsp;这是开发板板载的RS232（COM3）/485选择接口（JP1），因为RS485基本上就是一个半双工的串口，为了节约IO，我们把RS232（COM3）和RS485共用一个串口，通过`JP1`来设置当前是使用RS232（COM3）还是RS485。<br />
&emsp;&emsp;这样的设计还有一个好处。就是我们的开发板既可以充当RS232到TTL串口的转换，又可以充当RS485到TTL485的转换。（注意，这里的TTL高电平是3.3V） 

&emsp;&emsp;**3、I.MX6ULL核心板接口**<br />
&emsp;&emsp;这是开发板底板上面的核心板接口，由2个`2*30`的贴片板对板接线端子（3710F公座）组成，可以用来插正点原子的I.MX6UL/ULL核心板等，从而学习I.MX6UL/6ULL等芯片，达到一个开发板，学习多款SOC的目的，减少重复投资。 

&emsp;&emsp;**4、RGBLCD接口**<br />
&emsp;&emsp;这是转接板自带的RGB LCD接口（LCD），可以连接各种正点原子的RGB LCD屏模块，并且支持触摸屏（电阻/电容屏都可以）。采用的是`RGB888`格式，可显示1677万色，色彩显示丰富。 

&emsp;&emsp;**5、后备电池接口**<br />
&emsp;&emsp;这是I.MX6UL/ULL后备区域的供电接口，可以用来给I.MX6UL/ULL的后备区域提供能量，在外部电源断电的时候，维持SNVS区域数据的存储，以及RTC的运行。 

&emsp;&emsp;**6、USB HOST(OTG)**<br />
&emsp;&emsp;*V2.4版本以前底板有此接口，V2.4及以后版本底板没有此接口了！*<br />
&emsp;&emsp;这是开发板板载的一个侧插式的USB-A座（USB_HOST），由于I.MX6U的USB支持OTG功能，所以USB既可作HOST，又可做SLAVE。<br />
&emsp;&emsp;我们可以通过这个USB-A座，连接U盘/USB鼠标/USB键盘等其他USB从设备，从而实现USB主机功能。不过特别注意，由于USB HOST和USB SLAVE是共用一个USB端口，所以两者不可以同时使用。

&emsp;&emsp;**7、USB串口/串口1**<br />
&emsp;&emsp;这是USB串口同I.MX6U的串口1进行连接的接口（`JP5`），标号RXD和TXD是USB转串口的2个数据口（对CH340C来说），而U1_TX(TXD)和U1_RX(RXD)则是I.MX6U串口1的两个数据口。他们通过跳线帽对接，就可以连接在一起了，从而实现I.MX6U的串口通信。<br />
&emsp;&emsp;设计成USB串口，是出于现在电脑上串口正在消失，尤其是笔记本，几乎清一色的没有串口。所以板载了USB串口可以方便大家调试。<br />
&emsp;&emsp;而在板子上并没有直接连接在一起，则是出于使用方便的考虑。这样设计，你可以把I.MX6U-ALPHA开发板当成一个USB转TTL串口，来和其他板子通信，而其他板子的串口，也可以方便地接到开发板上。

&emsp;&emsp;**8、USB SLAVE(OTG)**<br />
&emsp;&emsp;①、V2.4版本以前底板<br />
&emsp;&emsp;这是开发板板载的一个MiniUSB头（USB_SLAVE），用于USB从机（SLAVE）通信，与上面的USB HOST一起作为OTG功能。通过此MiniUSB头，开发板就可以和电脑进行USB通信了。注意：该接口不能和USB HOST同时使用。<br />
&emsp;&emsp;开发板总共板载了两个MiniUSB头，一个（USB_TTL）用于USB转串口，连接`CH340C`芯片；另外一个（USB_SLAVE）用于I.MX6U内部USB。同时开发板可以通过此MiniUSB头供电，板载两个`MiniUSB`头（不共用），主要是考虑了使用的方便性，以及可以给板子提供更大的电流（两个USB都接上）这两个因素。 <br />
&emsp;&emsp;②、V2.4及以后版本底板<br />
&emsp;&emsp;这是开发板板载的一个Type-C接口，用于USB OTG通信。通过此Type-C接口，开发板就可以和电脑进行USB通信了，实现OTG功能 <br />
&emsp;&emsp;开发板总共板载了两个Type-C接口，一个（USB_TTL）用于USB转串口，连接CH340C芯片；另外一个用于I.MX6U内部USB。 

&emsp;&emsp;**9、USB转串口**<br />
&emsp;&emsp;这是开发板板载的一个USB转串口接口，用于USB连接`CH340C`芯片，从而实现USB转串口。同时，此接头也是开发板的电源提供口，V2.4版本一般的底板此接口使用Mini USB，在V2.4及以后版本底板采用Type-C接口。

&emsp;&emsp;**10、摄像头模块接口**<br />
&emsp;&emsp;这是开发板板载的一个摄像头模块接口（P1），摄像头模块（需自备），对准插入到此插槽中。

&emsp;&emsp;**11、启动(BOOT)拨码开关**<br />
&emsp;&emsp;I.MX6U支持多种启动方式，比如`SD卡、EMMC、NAND、QSPI FALSH和USB`等，要想从某一种设备启动就必须先设置好启动拨码开关。<br />
&emsp;&emsp;I.MX6U-ALPHA开发板用了一个**8P**的拨码开关来选择启动方式，正点原子开发板支持从SD卡、EMCM、NAND和USB这四种启动方式，这四种启动方式对应的拨码开关拨动方式已经写在了开发板上。大家在使用的时候根据自己的实际需求设置拨码开关即可。

&emsp;&emsp;**12、TF卡接口**<br />
&emsp;&emsp;这是开发板板载的一个标准TF卡接口（TF_CARD），该接口在开发板的背面，采用小型的TF卡接口，USDHC方式驱动，有了这个TF卡接口，就可以满足海量数据存储的需求。

&emsp;&emsp;**13、光环境传感器**<br />
&emsp;&emsp;这是开发板板载的一个光环境三合一传感器（U9），它可以作为：环境光传感器、近距离（接近）传感器和红外传感器。通过该传感器，开发板可以感知周围环境光线的变化，接近距离等，从而可以实现类似手机的自动背光控制。

&emsp;&emsp;**14、蜂鸣器**<br />
&emsp;&emsp;这是一个有源蜂鸣器，通过高低电平控制蜂鸣器的开关。

&emsp;&emsp;**15、SDIO WIFI接口**<br />
&emsp;&emsp;这是开发板上的一个SDIO WIFI(P4)接口，可以通过此接口连接正点原子出品的SDIO WIFI模块。SDIO WIFI接口和TF卡共用一个`USDHC`接口，因此不能同时和TF卡使用。  

&emsp;&emsp;**16、ATK模块接口**<br />
&emsp;&emsp;这是开发板板载的一个正点原子通用模块接口（JP2），目前可以支持正点原子开发的GPS模块、蓝牙模块、MPU6050模块、激光测距模块和手势识别模块等，直接插上对应的模块，就可以进行开发。<br />
&emsp;&emsp;后续我们将开发更多兼容该接口的其他模块，实现更强大的扩展性能。

&emsp;&emsp;**17、左右声道喇叭接口**<br />
&emsp;&emsp;开发板板载了一个高性能的音频解码芯片`WM8960`，此芯片可以驱动左右声道**2个8Ω，1W**的小喇叭，这两个接口用于外接两个左右声道小喇叭。<br />
&emsp;&emsp;不过在I.MX6U-ALPHA开发板的背面已经默认焊接了一个小喇叭，这个小喇叭接到了右声道上，因此如果要在此接口的右声道上外接小喇叭，那么必须先将开发板上自带的喇叭拆掉，否则WM8960驱动能力可能不足。

&emsp;&emsp;**18、耳机输出接口**<br />
&emsp;&emsp;这是开发板板载的音频输出接口（PHONE），该接口可以插`3.5mm`的耳机，当`WM8960`放音的时候，就可以通过在该接口插入耳机，欣赏音乐。<br />
&emsp;&emsp;此接口支持耳机插入检测，如果耳机不插入的话默认通过喇叭播放音乐，如果插入耳机的话就关闭喇叭，通过耳机播放音乐。

&emsp;&emsp;**19、录音输入接口**<br />
&emsp;&emsp;这是开发板板载的外部录音输入接口（LINE_IN）,通过咪头我们只能实现单声道的录音，而通过这个LINE_IN，我们可以实现立体声录音。

&emsp;&emsp;**20、复位按键**<br />
&emsp;&emsp;这是开发板板载的复位按键（RESET），用于复位I.MX6U，还具有复位液晶的功能，因为液晶模块的复位引脚和I.MX6U的复位引脚是连接在一起的，当按下该键的时候，I.MX6U和液晶一并被复位。

&emsp;&emsp;**21、用户按键KEY**<br />
&emsp;&emsp;这是开发板板载的1个机械式输入按键（KEY0），可以做为普通按键输入使用。

&emsp;&emsp;**22、红色用户LED灯**<br />
&emsp;&emsp;这是开发板板载的1个LED灯，为红色，用户可以使用此LED灯。在调试代码的时候，使用LED来指示程序状态，这是非常不错的一个辅助调试方法。

&emsp;&emsp;**23、蓝色电源指示LED灯**<br />
&emsp;&emsp;这是开发板电源指示LED灯，为蓝色，当板子供电正常的时候此灯就会常亮。如果此灯不亮的话就说明开发板供电有问题(排除LED灯本身损坏的情况)。

&emsp;&emsp;**24、WM8960音频DAC**<br />
&emsp;&emsp;这是一颗欧胜公司出品的音频DAC芯片，用于实现音乐播放与录音。

&emsp;&emsp;**25、MIC(咪头)**<br />
&emsp;&emsp;这是开发板的板载录音输入口（MIC），该咪头直接接到**WM8960**的输入上，可以用来实现录音功能。

&emsp;&emsp;**26、Nano SIM卡接口**<br /> 
&emsp;&emsp;这是开发板上的Nano SIM卡接口，如果要使用4G模块的话就需要在此接口中插入Nano SIM卡。

&emsp;&emsp;**27、ICM20608六轴传感器**<br />
&emsp;&emsp;这是开发板板载的一个六轴传感器芯片(U6)，型号为**ICM20608**，此芯片采用SPI接口与I.MX6U相连接。<br />
&emsp;&emsp;ICM20608内部集成1个三轴加速度传感器和1个三轴陀螺仪，该传感器在姿态测量方面应用非常广泛。所以喜欢玩姿态测量的朋友，也可通过本开发板进行学习。

&emsp;&emsp;**28、Mini PCIE 4G接口**<br />
&emsp;&emsp;这是开发板板载的一个Mini PCIE座，但是本质上走的USB协议，通过此接口可以连接4G模块，比如高新兴物联的`ME3630`。<br />
&emsp;&emsp;接上4G模块以后I.MX6U-ALPHA开发板就可以实现4G上网功能，对于不方便布网线或者没有WIFI的场合来说是个不错的选择。

&emsp;&emsp;**29、DC6~16V电源输入**
&emsp;&emsp;这是开发板板载的一个外部电源输入口（DC_IN），采用标准的直流电源插座。开发板板载了`DC-DC`芯片（JW5060T），用于给开发板提供高效、稳定的5V电源。<br />
&emsp;&emsp;由于采用了`DC-DC`芯片，所以开发板的供电范围十分宽，大家可以很方便的找到合适的电源（只要输出范围在DC6~16V的基本都可以）来给开发板供电。<br />
&emsp;&emsp;在耗电比较大的情况下，比如用到4.3屏/7寸屏/网口的时候，建议使用外部电源供电，可以提供足够的电流给开发板使用。

&emsp;&emsp;**30、电源开关**<br />
&emsp;&emsp;这是开发板板载的电源开关（K1）。该开关用于控制整个开发板的供电。这是一个两段式拨动开关，拨到右边关闭开发板电源，整个开发板都将断电，电源指示灯（PWR）会随之熄灭。<br />
&emsp;&emsp;拨到右边打开开发板电源，整个板子开始供电，电源指示灯(PWR)点亮。 

&emsp;&emsp;**31、5V电源输入/输出**<br />
&emsp;&emsp;这是开发板板载的一组5V电源输入输出排针（2*3）（VOUT2），该排针用于给外部提供5V的电源，也可以用于从外部接5V的电源给板子供电。<br />
&emsp;&emsp;同样大家在实验的时候可能经常会为没有5V电源而苦恼不已，正点原子充分考虑到了大家需求，有了这组5V排针，你就可以很方便的拥有一个简单的5V电源（USB供电的时候，最大电流不能超过`500mA`，外部供电的时候，最大可达`3000mA`）。 

&emsp;&emsp;**32、3.3V电源输入/输出**
&emsp;&emsp;这是开发板板载的一组3.3V电源输入输出排针（2*3）（VOUT1），用于给外部提供3.3V的电源，也可以用于从外部接3.3V的电源给板子供电。<br />
&emsp;&emsp;大家在实验的时候可能经常会为没有3.3V电源而苦恼不已，有了`I.MX6U-ALPHA`开发板，你就可以很方便的拥有一个简单的3.3V电源（最大电流不能超过`3000mA`）。 

&emsp;&emsp;**33、3路USB HOST接口**<br /> 
&emsp;&emsp;这是开发板板载的3路USB HOST接口，I.MX6U有两个USB接口，正点原子的I.MX6U-ALPHA开发板通过`GL850`芯片将I.MX6U的USB2扩展成了4路USB HOST，其中一路用于连接4G模块，另外3路作为USB HSOT，用户可以通过这三路USB HOST接口连接USB鼠标、USB键盘、U盘等设备。

&emsp;&emsp;**34、引出的IO口**<br />
&emsp;&emsp;这是开发板IO引出端口JP6，采用`2*16`排针，总共引出31个IO口。

&emsp;&emsp;**35、以太网接口1(RJ45)**<br />
&emsp;&emsp;I.MX6U有两个网络接口：ENET1和ENET2，这是ENET1网络接口，可以用来连接网线，实现网络通信功能。该接口使用I.MX6U内部的MAC控制器外加**PHY**芯片，实现`10/100M`网络的支持。

&emsp;&emsp;**36、以太网接口2(RJ45)**<br />
&emsp;&emsp;这是开发板板载的以太网接口2，也就是I.MX6U的ENET2网络接口。 

&emsp;&emsp;**37、RS232接口（母）**<br />
&emsp;&emsp;这是开发板板载的另外一个RS232接口（COM3），通过一个标准的**DB9**母头和外部的串口连接。通过这个接口，我们可以连接带有串口的电脑或者其他设备，实现串口通信

&emsp;&emsp;**38、RS485接口**<br />
&emsp;&emsp;这是开发板板载的RS485总线接口（RS485），通过2个端口和外部485设备连接。这里提醒大家，RS485通信的时候，必须A接A，B接B。否则可能通信不正常

## 1.2.2 I.MX6U-ALPHA软件资源说明

&emsp;&emsp;上面我们详细介绍了正点原子`I.MX6U-ALPHA`开发板的硬件资源。接下来，我们将向大家简要介绍一下I.MX6U-ALPHA开发板的软件资源。

&emsp;&emsp;软件资源分为3部分：Linux系统驱动软件资源、裸机例程、Linux驱动例程，我们依次来看一下这三类软件资源的情况。关于Linux系统软件资源如下表所示：

| 类型              | 描述                                                         | 备注                                                         |
| :---------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
| uboot             | uboot版本为2016.03                                           | 提供源码。<br />支持LCD显示、支持SD卡和EMMC、支持网络、支持NAND Flash、支持环境变量修改等。 |
| Linux内核         | 内核版本为4.1.15                                             | 提供源码                                                     |
| 根文件系统rootfs  | 提供busybox、buildroot、yocto、ubuntu这四种根文件系统及其制作方法 | 提供详细的制作教程                                           |
| QT5根文件系统     | QT版本为5.6.1                                                | 提供详细的教程                                               |
| 交叉编译器        | arm-linux-gnueaihf，版本4.9.4                                | 提供软件                                                     |
| 系统烧写方法      | MFGTOOL和SD卡两种                                            | 提供详细的使用教程                                           |
| LCD驱动           | RGB LCD驱动                                                  | 提供源码                                                     |
| 触摸              | FT5xx6、GT9147等电容触摸屏(仅限正点原子在售)                 | 提供源码                                                     |
| 485               | RS485 驱动                                                   | 提供源码                                                     |
| 232               | RS232驱动                                                    | 提供源码                                                     |
| CAN               | CAN驱动                                                      | 提供源码                                                     |
| 网络              | PHY为LAN8720或SR8201F                                        | 提供源码                                                     |
| USB HOST          | USB HUB为GL850或SL2.1A                                       | 提供源码                                                     |
| USB OTG           | USB从机和主机                                                | 提供源码                                                     |
| 4G无线            | ME3630 4G模块                                                | 提供源码                                                     |
| 按键KEY           | GPIO                                                         | 提供源码                                                     |
| LED               | GPIO                                                         | 提供源码                                                     |
| 音频              | 音频DAC为WM8960                                              | 提供源码                                                     |
| SDIO WIFI         | 正点原子RTL8189模块                                          | 提供源码                                                     |
| GPS               | 正点原子GPS模块                                              | 提供源码                                                     |
| 环境光传感器(IIC) | AP3216C，IIC接口                                             | 提供源码                                                     |
| 六轴传感器(SPI)   | ICM20608，SPI接口                                            | 提供源码                                                     |
| TF卡/EMMC         | USDHC驱动                                                    | 提供源码                                                     |
| 摄像头            | OV5640驱动                                                   | 提供源码                                                     |
| 串口              | UART1驱动                                                    | 提供源码                                                     |
| PWM背光           | LCD PWM背光                                                  | 提供源码                                                     |
| RTC               | I.MX6U内部RTC                                                | 提供源码                                                     |
| USB WIFI          | RTL8188                                                      | 提供源码                                                     |


&emsp;&emsp;接下来看一下`I.MX6U-ALPHA`开发板的裸机例程，如下表所示：

<div class="imx6u_center-table-div">
<table class="imx6u_center-table">
  <tr>
    <th>编号</th>
    <th>实验名字</th>
    <th>编号</th>
    <th>实验名字</th>
  </tr>
  <tr>
    <td>1</td>
    <td>leds</td>
    <td>12</td>
    <td>highpreci_delay</td>
  </tr>
   <tr>
    <td>2</td>
    <td>ledc</td>
    <td>13</td>
    <td>uart</td>
  </tr>
  <tr>
    <td>3</td>
    <td>ledc_stm32</td>
    <td>14</td>
    <td>printf</td>
  </tr>
  <tr>
    <td>4</td>
    <td>ledc_sdk</td>
    <td>15</td>
    <td>ddr3</td>
  </tr>
  <tr>
    <td>5</td>
    <td>ledc_bsp</td>
    <td>16</td>
    <td>lcd</td>
  </tr>
  <tr>
    <td>6</td>
    <td>beep</td>
    <td>17</td>
    <td>rtc</td>
  </tr>
  <tr>
    <td>7</td>
    <td>key</td>
    <td>18</td>
    <td>i2c</td>
  </tr>
  <tr>
    <td>8</td>
    <td>clk</td>
    <td>19</td>
    <td>spi</td>
  </tr>
  <tr>
    <td>9</td>
    <td>int</td>
    <td>20</td>
    <td>touchscreen</td>
  </tr>
  <tr>
    <td>10</td>
    <td>epit_timer</td>
    <td>21</td>
    <td>pwm_lcdbacklight</td>
  </tr>
  <tr>
    <td>11</td>
    <td>key_filter</td>
    <td> </td>
    <td> </td>
  </tr>
</table>
</div>


&emsp;&emsp;从上表可以看出，正点原子的`I.MX6U-ALPHA`开发板裸机例程似乎不是很多，不像STM32、RT1052那样六七十个裸机例程，这是因为嵌入式Linux和单片机的开发方式以及应用场合不同。

&emsp;&emsp;单片机学名叫做`Microcontroller`，也就是微控制器，主要用于控制相关的应用，因此单片机的外设都比较多，比如很多路的IIC、SPI、UART、定时器等等。

&emsp;&emsp;嵌入式Linux开发主要注重于高端应用场合，比如音视频处理、网络处理等等。比如一个机器人，高性能处理器加Linux系统(或者其他系统)作为机器人的大脑，主要负责接收各个传感器采集的数据然后对原始数据进行处理，得到下一步执行指令，这个往往需要很高的性能。

&emsp;&emsp;当处理完成得到下一步要做的动作之后大脑就会将数据发给控制机器人各个关节电机的驱动控制器，这些驱动控制器一般都是单片机做的。

&emsp;&emsp;所以大家在学习嵌入式Linux开发的时候一定不要深陷裸机，我们之所以讲解裸机是为了给嵌入式Linux打基础，让大家了解所使用的SOC、了解GCC那一套工作流程，最终的目的都是为了嵌入式Linux做准备的。

&emsp;&emsp;看完裸机例程以后我们最后再来看一下正点原子为`I.MX6U-ALPHA`开发板准备的嵌入式Linux驱动例程，如下表所示：

<div class="imx6u_center-table-div">
<table class="imx6u_center-table">
  <tr>
    <th>编号</th>
    <th>实验名字</th>
    <th>编号</th>
    <th>实验名字</th>
  </tr>
  <tr>
    <td>1</td>
    <td>chrdevbase</td>
    <td>13</td>
    <td>irq</td>
  </tr>
  <tr>
    <td>2</td>
    <td>led</td>
    <td>14</td>
    <td>blockio</td>
  </tr>
  <tr>
    <td>3</td>
    <td>newchrled</td>
    <td>15</td>
    <td>noblockio</td>
  </tr>
  <tr>
    <td>4</td>
    <td>dtsled</td>
    <td>16</td>
    <td>asyncnoti</td>
  </tr>
  <tr>
    <td>5</td>
    <td>gpioled</td>
    <td>17</td>
    <td>platform</td>
  </tr>
  <tr>
    <td>6</td>
    <td>beep</td>
    <td>18</td>
    <td>dtsplatform</td>
  </tr>
  <tr>
    <td>7</td>
    <td>atomic</td>
    <td>19</td>
    <td>miscbeep</td>
  </tr>
  <tr>
    <td>8</td>
    <td>spinlock</td>
    <td>20</td>
    <td>input</td>
  </tr>
  <tr>
    <td>9</td>
    <td>semaphore</td>
    <td>21</td>
    <td>iic</td>
  </tr>
  <tr>
    <td>10</td>
    <td>mutex</td>
    <td>22</td>
    <td>spi</td>
  </tr>
  <tr>
    <td>11</td>
    <td>key</td>
    <td>23</td>
    <td>multitouch</td>
  </tr>
  <tr>
    <td>12</td>
    <td>timer</td>
    <td> </td>
    <td> </td>
  </tr>
</table>
</div>


## 1.2.3 I.MX6ULL核心板硬件资源说明

&emsp;&emsp;核心板资源参考前面核心板图片中的标注部分，我们将按逆时针的顺序依次介绍：

&emsp;&emsp;**1.	核心板电源指示灯**<br />
&emsp;&emsp;这是核心板板载的一个蓝色LED灯，用于指示核心板供电是否正常，如果核心板供电正常的话此灯就会点亮。

&emsp;&emsp;**2.	NAND/EMMC存储芯片**<br />
&emsp;&emsp;这是核心板上板载的存储芯片，分为NAND和EMMC两种。对于NAND版本的核心板共有**256MB和512MB**两种容量的NAND，型号分别为`MT29F2G08ABAEAWP-IT`或 `MT29F4G08ABADAWP-IT`，这两种型号的NAND FLASH工作温度范围都为工业级。EMMC版本的核心板使用**8GB**的EMMC，型号为`KLM8G1GET`。

&emsp;&emsp;**3.	DDR3L芯片**<br />
&emsp;&emsp;这是核心板板载的DDR3L芯片，NAND版本核心板的DDR3L容量为**256MB**，EMMC版本的核心板的DDR3L容量为**512MB**。型号分别为`NT5CC128M16JR-EK`和`NT5CC256M16EP-EK`。如果要用于UI开发，那么最好选择512MB的DDR3L，当然了，正点原子的I.MX6U核心板支持定制，具体定制方法请联系销售。

&emsp;&emsp;**4.	CPU**<br />
&emsp;&emsp;这是核心板的CPU，型号为`MCIMX6Y2CVM08AB`，`MCIMX6Y2CVM08AB`主频为**800MHz**(实际792MHz)。<br />
&emsp;&emsp;该芯片采用Coretx-A7内核，自带32KB的L1指令Cache、32KB的L1数据Cache、128KB的L2Cache、集成NEON和SIMDv2、支持硬件浮点(FPU)计算单元，浮点计算架构为VFPv4-D32、1个RGB LCD接口、2个CAN接口、2个10M/100M网络接口、2个USB OTG接口(USB2.0)、2路ADC、8个串口、3个SAI、4个定时器、8路PWM、4路I2C接口、4路SPI接口、一路CSI摄像头接口、2个USDHC接口，支持4位SD卡，最高可以支持UHS-I SDR 104模式，支持1/4/8位的EMMC，最高可达HS200模式、一个外部存储接口、支持16位的LPDDR2-800、DDR3-800和DDR3L-800、支持8位的MLC/SLC NAND Flash，支持2KB、4KB和8KB页大小，以及124个通用IO口等。

&emsp;&emsp;**5.	32.768KHz晶振**<br /> 
&emsp;&emsp;这是一个无源的**32.768KHz**晶振，供I.MX6U内部RTC使用。

&emsp;&emsp;**6.	24MHz晶振**<br />
&emsp;&emsp;这是一个无源的**24MHz**晶振，供I.MX6U使用。

&emsp;&emsp;另外，I.MX6U核心板的接口在底部，通过两个**2*30**的板对板端子（3710M母座）组成，总共引出了**104个IO**，通过这个接口，可以实现与`I.MX6U-ALPHA`底板对接。













