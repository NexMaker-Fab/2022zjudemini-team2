# 原型制作


## 材料准备


### 硬件

- Arduino-uno-r3 开发板一块
- 开发板USB线一条
- RFID-RC522读卡器一块
- 杜邦线
- arduino sensor shield v5.0拓展板
- 卡片若干
- HC-SR04模块
- 蜂鸣器
- 三头耳机
- DY-SV5W模块


 ### 软件

- Arduino驱动

## 技术支持

### 1. RFID RC522
我们使用了RFID RC522模块来实现*音乐的识别功能*，首先我们会有一些ic卡（M1类型IC卡），而RC522模块就是阅读器天线以及处理器和寄存器
- #### RFID工作原理
    RFID（Radio Frequency Identification）：无线射频识别
    RFID由2个部分组成：应答器/标签。无线接收器用于读取应答器/标签上的数据。
<img src="img/2/24.png">

<br>

- #### RFID介绍
<br>
<img src="img/2/25.png">

    VCC：要连接到2.5v到3.3v中，如果连接5v的接口可能会烧坏此RC522模块；

    RST：复位和断点输入引脚。低频时RC522关闭，包括振荡器，输入引脚，串口外围接口的关闭；

    GND：接地

    IRQ：中断警告引脚，当RFID标签靠近该设备时，通过此引脚进行触发。

    MISO/SCL/Tx：此接口为（Master In Slave Out）当SPI（串口外围接口）开启时有效。当使用I2C协议接口时此引脚为串口时钟，当为UART协议接口时，此引脚为串口数据输出口。

    MOSI(Master Out Slave In)：该引脚为此模块的SPI（串口外围接口）

    SCK(Serial Clock)：接收SPI提供的脉冲信号。

    SS/SDA/Rx：当SPI启动时，该引脚为输入信号，当为I2C协议接口时为串口数据口，当为UART时为串口输入口。

- #### 使用流程
1. 库的安装
打开Arduino终端中的：项目-加载库-管理库-搜索“MFRC522”库-安装
<img src="img/2/26.jpg">
<img src="img/2/27.jpg">

2. 定义RFID模块和数字输出引脚
<img src="img/2/28.png" width="300">

3. 初始化串口通信、SPI总线和MFRC522模块。

4. 编写相关程序。

>**tip**:  MFRC522的电源接口要连接3.3v电源。若使用的是5V的MCU，注意分压。

------

### 2. Arduino Sensor Shield v5 传感器扩展板
Sensor Shield V5.0适用于Uno，Mega 2560和类似外形的Arduino板，并提供了一种方便的方法来连接传感器和其他外围设备，例如伺服电机。

<img src="img/2/29.jpg" width="300">

- #### 主要功能：
 将标准的Arduino I / O引脚引到接头，以及每个I / O的专用接地和电源引脚，以方便将传感器连接到其他设备。
屏蔽层还具有许多专用连接器，如下所述，这些专用连接器是为特定目的而定义的，但也可以将它们视为通用连接点。
辅助电源连接器允许将单独的电源提供给与D0-D13引脚关联的电源引脚，这对于驱动伺服电机非常方便。
远程复位开关位于护罩上，以方便操作。它还将板上的针脚13“ L” LED灯带到屏蔽罩，以方便查看。

<img src="img/2/30.jpg" width="300">

- #### 硬件接线
<img src="img/2/34.jpg">

------

### 3. DY-SV5W 语音播放模块

- #### 硬件概述
    DY-SV5W是一款智能语音模块，集成IO分段触发，UART串口控制，ONE_line 单总线串口控制，标准MP3等7种工作模式；板载5W D类功放，可直接驱动4Ω，3~5W喇叭； 支持MP3,WAV解码格式，最大支持32G TF卡存储，可通过USB数据线连接电脑更新TF 卡存储 音频文件。

<img src="img/2/31.png" width="300">

- #### 模块引脚定义
<img src="img/2/32.png">

- #### 拨码开关模式配置
“按键组合播放”是指IO0-IO7输出对应的电平后恢复原来的高电平,类似于按键触发一次 “电平组合播放”是指IO0-IO7输出对应的电平后保持电平不变 “I/O组合（独立）模式0”与“I/O组合（独立）模式1”的区别在于前者模式释放电平后 继续播放当前曲目至结束，后者模式释放电平后立即停止播放曲目。

<img src="img/2/33.jpg" >

我们选用了**I/O独立模式0**

- #### 硬件接线
<img src="img/2/35.png">

<img src="img/2/36.png">

>**tip**:  串口是3.3V的TTL 电平，如果主机系统是 5V电平请在中间串1K 电阻。


## reference
[Arduino](https://www.arduino.cc/)<br>
[语音播放模块（DY-SV5W）](https://blog.csdn.net/qq_36955622/article/details/103512824)<br>
[RFID工作原理及RC522模块介绍](https://blog.csdn.net/qq78442761/article/details/105432385/?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-0--blog-128687619.pc_relevant_multi_platform_whitelistv4&spm=1001.2101.3001.4242.1&utm_relevant_index=3)<br>
[arduino rc522模块使用](https://blog.csdn.net/economics3/article/details/128687619?spm=1001.2101.3001.6650.2&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EYuanLiJiHua%7EPosition-2-128687619-blog-82667116.pc_relevant_3mothn_strategy_recovery&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EYuanLiJiHua%7EPosition-2-128687619-blog-82667116.pc_relevant_3mothn_strategy_recovery&utm_relevant_index=5)<br>
[Arduino Sensor Shield v5 传感器扩展板](https://cloud.tencent.com/developer/article/1691985)<br>