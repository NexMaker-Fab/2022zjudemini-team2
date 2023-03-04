# Arduino
### Arduino简介
Arduino 是一个基于易于使用的硬件和软件的开源电子平台。 Arduino 板能够读取输入 - 传感器上的光、按钮上的手指或 Twitter 消息 - 并将其转换为输出 - 激活电机、打开 LED、在线发布内容。您可以通过向板上的微控制器发送一组指令来告诉您的板要做什么。为此，您可以使用Arduino 编程语言（基于Wiring）和基于Processing 的Arduino 软件 (IDE)。
详情参照[此官网教程](https://www.arduino.cc/)

- **便宜**- 与其他微控制器平台相比，Arduino 板相对便宜。最便宜的 Arduino 模块版本可以手工组装，即使是预组装的 Arduino 模块成本也不到 50 美元

- **跨平台**——Arduino 软件 (IDE) 在 Windows、Macintosh OSX 和 Linux 操作系统上运行。大多数微控制器系统仅限于 Windows。

- **简单、清晰的编程环境**——Arduino 软件 (IDE) 易于初学者使用，但也足够灵活，高级用户也可以利用。对于教师来说，它基于 Processing 编程环境很方便，因此在该环境中学习编程的学生将熟悉 Arduino IDE 的工作原理。

- **开源和可扩展软件**——Arduino 软件作为开源工具发布，可供有经验的程序员扩展。该语言可以通过 C++ 库进行扩展，想要了解技术细节的人可以从 Arduino 飞跃到它所基于的 AVR C 编程语言。同样，您可以根据需要将 AVR-C 代码直接添加到您的 Arduino 程序中。

- **开源和可扩展的硬件**——Arduino 板的计划是根据知识共享许可发布的，因此经验丰富的电路设计师可以制作自己的模块版本，对其进行扩展和改进。即使是相对缺乏经验的用户也可以构建该模块的面包板版本，以了解其工作原理并节省资金。

### Arduino 板的说明
以下是 UNO 板的电路：
<img src="img/1/13.jpg">

以下是 UNO 板的详细内容
<img src="img/1/14.png">

1. **电源 USB**:Arduino 板可以通过使用计算机上的USB线供电。你需要做的是将 USB 线连接到 USB 接口。
2. **电源（桶插座）**:Arduino 板可以通过将其连接到电源插口直接从交流电源供电。

3. **稳压器**:稳压器的功能是控制提供给 Arduino 板的电压，并稳定处理器和其他元件使用的直流电压。

4. **晶体振荡器**:晶振帮助Arduino处理时间问题。Arduino 如何计算时间？答案是，通过使用晶体振荡器。在 Arduino 晶体顶部打印的数字是 16.000H9H。它告诉我们，频率是 16,000,000 赫兹或 16MHz。
	
5. **Arduino 重置**:你可以重置你的 Arduino 板，例如从一开始就启动你的程序。可以通过两种方式重置 UNO 板。首先，通过使用板上的复位按钮（17）。其次，你可以将外部复位按钮连接到标有 RESET（5）的 Arduino 引脚。

6. **引脚**（3.3，5，GND，Vin）:

- 3.3V（6） - 提供 3.3 输出电压

- 5V（7） - 提供 5 输出电压

- 使用3.3伏和5伏电压，与 Arduino 板一起使用的大多数组件可以正常工作。

- GND（8）（接地） - Arduino 上有几个 GND 引脚，其中任何一个都可用于将电路接地。

- VVin（9） - 此引脚也可用于从外部电源（如交流主电源）为 Arduino 板供电。

7. **模拟引脚**:Arduino UNO 板有六个模拟输入引脚，A0 到 A5。这些引脚可以从模拟传感器（如湿度传感器或温度传感器）读取信号，并将其转换为可由微处理器读取的数字值。

8. **微控制器**:每个 Arduino 板都有自己的微控制器（11）。你可以假设它作为板的大脑。Arduino 上的主 IC（集成电路）与板对板略有不同。微控制器通常是 ATMEL 公司的。在从 Arduino IDE 加载新程序之前，你必须知道你的板上有什么 IC。此信息位于 IC 顶部。
	
9. **ICSP 引脚**:大多数情况下，ICSP（12）是一个 AVR，一个由 MOSI，MISO，SCK，RESET，VCC 和 GND 组成的 Arduino 的微型编程头。它通常被称为 SPI（串行外设接口），可以被认为是输出的“扩展”。实际上，你是将输出设备从属到 SPI 总线的主机。

10. **电源 LED 指示灯**:当你将 Arduino 插入电源时，此 LED 指示灯应亮起，表明你的电路板已正确通电。如果这个指示灯不亮，那么连接就出现了问题。

11. **TX 和 RX LED**:在你的板上，你会发现两个标签：TX（发送）和RX（接收）。它们出现在 Arduino UNO 板的两个地方。首先，在数字引脚 0 和 1 处，指示引脚负责串行通信。其次，TX 和 RX LED（13）。发送串行数据时，TX LED 以不同的速度闪烁。闪烁速度取决于板所使用的波特率。RX 在接收过程中闪烁。

12. **数字 I/O**:Arduino UNO 板有 14 个数字 I/O 引脚（15）（其中 6 个提供 PWM（脉宽调制）输出），这些引脚可配置为数字输入引脚，用于读取逻辑值（0 或 1） ；或作为数字输出引脚来驱动不同的模块，如 LED，继电器等。标有“〜”的引脚可用于产生 PWM。
	
13. **AREF**:AREF 代表模拟参考。它有时用于设置外部参考电压（0 至 5 伏之间）作为模拟输入引脚的上限。

### Arduino 板的安装
1. 首先，你必须有Arduino板（你可以选择你喜欢的板）和一根USB线。如果你使用Arduino UNO，Arduino Duemilanove，Nano，Arduino Mega 2560或Diecimila，你将需要一个标准USB线（A插头到B插头）。
2. 下载Arduino IDE软件。

你可以从Arduino官方网站的[下载页面](https://www.arduino.cc/en/software)获得不同版本的Arduino IDE。你必须选择与你的操作系统（Windows，IOS或Linux）兼容的软件。文件下载完成后，解压缩文件。
3. 打开板的电源。

Arduino Uno，Mega，Duemilanove和Arduino Nano通过USB连接到计算机或外部电源自动获取电源。如果你使用Arduino Diecimila，则必须确保板的配置为从USB连接获取电源。电源选择使用跳线，一小块塑料安装在USB和电源插孔之间的三个引脚中的两个。检查它是否在最靠近USB端口的两个引脚上。

使用USB线将Arduino板连接到计算机。绿色电源LED等（标有PWR）应该发光。
4. 启动Arduino IDE。

下载Arduino IDE软件后，需要解压缩该文件夹。在文件夹中，你可以找到带有无穷大标签(application.exe)的应用程序图标。双击该图标以启动IDE。
5. 打开你的第一个项目。

一旦软件启动，你有两个选项：

- 创建一个新项目。
- 打开一个现有的项目示例。
- 要创建新项目，请选择Flie→New
<img src="img/1/15.png">

6. 选择你的Arduino主板。

为了避免在将程序上载到板上时出现任何错误，必须选择正确的Arduino板名称，该名称与连接到计算机的电路板相匹配。

转到Tools→Board，然后选择你的板。
<img src="img/1/16.jpg">

7. 选择串行端口。

选择Arduino板的串行设备。转到Tools→Serial Port菜单。这可能是COM3或更高（COM1和COM2通常保留为硬件串行端口）。要弄清楚的话，你可以断开你的Arduino板，并重新打开菜单，那么消失的条目应该是Arduino板。重新连接板并选择该串行端口。
<img src="img/1/17.png">

8. 将程序上传到你的板。

在解释如何将我们的程序上传到板之前，我们必须演示Arduino IDE工具栏中出现的每个符号的功能。
<img src="img/1/18.png">
A - 用于检查是否存在任何编译错误。

B - 用于将程序上传到Arduino板。

C - 用于创建新草图的快捷方式。

D - 用于直接打开示例草图之一。

E - 用于保存草图。

F - 用于从板接收串行数据并将串行数据发送到板的串行监视器。
点击环境中的“Upload”按钮。等待几秒钟，你将看到板上的RX和TX LED灯闪烁。如果上传成功，则状态栏中将显示“Done uploading”消息。



注意 - 如果你有Arduino Mini，NG或其他电路板，则需要在单击Arduino软件上的上传按钮之前，立即按下电路板上的复位按钮。

### Arduino 程序实验

#### 实验一：雨水感应灯
##### **实验背景**

    雨滴，下雨传感器，可用于各种天气状况的监测， 并转成数定信号和 AO 输出

##### **实验器材**
1. 面包板一块

2. 导线

3. Arduino主板

4. 雨滴传感器

5. led灯组一个

##### **雨滴传感器简介**
- 传感器介绍：
    接上 5V 电源，电源指示灯亮，感应板上没有水滴时，DO 输出为高电平， 开关指示灯灭 ，滴上一滴水，DO 输出为低电平，开关指示灯亮， 刷掉上面的水滴，又恢复到，输出高电态。 AO 模拟输出，可以连接单片机的 AD 口检测滴在上面的雨量大小。 DO TTL 数字输出也可以连接单片机检测是否有雨。
  <img src="img/1/19.jpg">

- 参数
1. 电压：5V
2. 输出信号LED指示。
3. 带有二极管反向保护
4. TTL电平输出
5. 二级管反向保护~（防止电源接反了）
6. TTL输出有效信号为低电平.驱动能力100MA左右，
可直接驱动继电器，蜂鸣器，小风扇，等等。
7. 高电平驱动能力4MA左右
8. 灵敏度可通过电位器调节
9. 没有雨时候LED点亮输出为高电平，雨滴上去，输出地电平，LED灭
10. 模拟量输出的电压0-3.5V之间
11. 雨滴板和控制板是分开的，方便将线引出
12. 大面积的雨滴板，更有利于检测到雨水
13. 板子带有定位孔方便大家安装
14. 控制板板子大小：31*20 MM
15. 大面积雨滴检测板 50*35 MM

- 电原理图
<img src="img/1/20.jpg">

- 功能介绍：
    接上 5V 电源，电源指示灯亮，感应板上没有水滴时，DO 输出为高电平，开关指示灯灭 ，滴上一滴水，DO 输出为低电平，开关指示灯亮，刷掉上面的水滴，又恢复到，输出高电平状态.......


    AO 模拟输出，可以连接单片机的 AD 口检测滴在上面的雨量大小，
    DO TTL 数字输出也可以连接单片机检测是否有雨。

- 接线图
<img src="img/1/21.jpg">

- 源代码

```
const int analogPin=A0; 
const int digitalPin=7; 
const int ledPin=13;
int redPin = 2;  //定义红色引脚
int yellowPin = 3; //定义黄色引脚 
int greenPin = 4; //定义绿色引脚 
int val = 0;    
int aState=0;
boolean dState=0;
void setup() {
  //设置红色引脚为输出
 pinMode(redPin, OUTPUT);
 pinMode(greenPin, OUTPUT);
 pinMode(yellowPin,OUTPUT);
 pinMode(digitalPin,INPUT);
 Serial.begin(9600);
}
void loop() {
  aState=analogRead(analogPin); 
  Serial.print("A0: ");
  Serial.println(aState); 
  dState=digitalRead(digitalPin); 
  Serial.print("D0: ");
  Serial.println(dState);
  if(dState==HIGH)  
  {
   digitalWrite(yellowPin,LOW);
   digitalWrite(greenPin, HIGH);
   digitalWrite(redPin, LOW); 
  }else{
    digitalWrite(yellowPin,LOW);
    digitalWrite(redPin, HIGH); 
    digitalWrite(greenPin, LOW); 
    }
}
```
- 效果展示：
<br>
<embed src="img/0/1.mp4" width=1080 heigh=600/>

#### 实验二：超声传感测距实验
##### **实验背景**

    超声波测距，接lcd显示屏，可用于障碍物距离的监测， 并转成数定信号和 AO 输出

##### **实验器材**
1. 面包板一块

2. 导线

3. Arduino主板

4. HC-SR04模块

5. lcd1602

##### **超声波传感器简介**
- 传感器介绍：
    HC-SR04超声波传感器使用声纳来确定物体的距离，就像蝙蝠一样。它提供了非常好的非接触范围检测，准确度高，读数稳定，易于使用，尺寸从2厘米到400厘米或1英寸到13英尺不等。

其操作不受阳光或黑色材料的影响，尽管在声学上，柔软的材料（如布料等）可能难以检测到。它配有超声波发射器和接收器模块。
  <img src="img/1/22.png">

- 参数 
1. 电源 - + 5V DC
2. 静态电流 - <2mA
3. 工作电流 - 15mA
4. 有效角度 - <15°
5. 测距距离 - 2厘米-400厘米/1英寸-13英尺
6. 分辨率 - 0.3厘米
7. 测量角度 - 30度

- 工作原理：
1. 采用IO触发测距10us的高电平信号;
2. 模块自动发送8个40khz的方波，自动检测是否有信号返回；
3. 有信号返回，通过IO输出一高电平，高电平持续的时间就是超声波从发射到返回的时间．
测试距离=(高电平时间*声速(340M/S))/2;



- 电原理图
<img src="img/1/23.jpg">

- 源代码
```
#include <LiquidCrystal.h>
LiquidCrystal lcd(3, 5, 7, 8, 9, 10);
const int TrigPin = 11;
const int EchoPin = 12;
float cm;
 
 

float distance;                   //定义距离变量
void setup()
{
  Serial.begin(9600);             //开启串口

  pinMode(TrigPin, OUTPUT);       //设置超声波传感器引脚模式
  pinMode(EchoPin, INPUT);
  
  lcd.setCursor(0,0);             //设置光标位置
  lcd.print("Distance test");     //显示内容
}
void loop()
{
  get_dis();                      //获取距离函数
  lcd_display();                  //lcd显示函数
  delay(500);                     //延时
}
void get_dis()                    //获取距离子函数
{
  digitalWrite(TrigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(TrigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(TrigPin, LOW);
  distance = pulseIn(EchoPin, HIGH) / 58.0; 
  Serial.print(distance);
  Serial.println("cm");
}

void lcd_display()                //lcd显示子函数
{
  int dis = int(distance);
  
  lcd.setCursor(0,1);
  if(dis >= 0 && dis < 1000)
  {
    lcd.print("Dis:");
    lcd.print(dis);
  }
  
  if(dis < 100) lcd.print(' ');
  
  lcd.setCursor(8,1);
  lcd.print("cm");
}
```