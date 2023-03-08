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

- #### 程序编写
代码编写方面，案例代码相对比较简单，不用加头文件，可以在任意Arduino编译平台上编写，其中串口发送简单指令进行语音模块的控制，常用指令如下表所示，需要注意的是要以十六进制格式发送数据
<img src="img/2/36.png">

>**tip**:  串口是3.3V的TTL 电平，如果主机系统是 5V电平请在中间串1K 电阻。

## 程序设计

### part 1 被动辅助演奏：RFID识别播放

- #### 程序逻辑
该程序是用于Arduino的RFID音乐识别控制器，可读取RFID卡片的UID，并根据UID控制音乐播放器。程序使用MFRC522库来与RFID模块通信，使用TimerOne库创建一个定时器，在一段时间内检查是否读取到了卡片，然后根据读取到的卡片UID控制8个数字输出引脚的状态来控制音乐播放器的开关。

<img src="img/2/39.png">

- #### 效果展示

<iframe frameborder="0" width="960px" height="540px"  src="//player.bilibili.com/player.html?aid=823157997&bvid=BV1Hg4y1t7RM&cid=1044071768&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>


程序的逻辑如下：

1. 导入SPI、MFRC522和TimerOne库。
2. 定义RFID模块和数字输出引脚的针脚。
3. 初始化串口通信、SPI总线和MFRC522模块。
4. 初始化数字输出引脚和定时器，设置一个定时器中断函数来计时。
5. 在循环中检查定时器的时间是否大于1秒，如果是，则关闭所有数字输出引脚。
6. 使用MFRC522库检查是否有新的RFID卡片在读卡器附近。
7. 如果有卡片，则读取卡片的UID，并将UID转换为字符串格式。
8. 如果卡片的UID与预设的UID匹配，则根据卡片的UID设置数字输出引脚的状态来控制电子锁的开关。
9. 重置定时器时间为0。
10. 要连接Arduino线路，请按照以下方式连接：<br>
    将MFRC522模块的SDA引脚连接到Arduino的数字针脚10。<br>
    将MFRC522模块的SCK引脚连接到Arduino的数字针脚13。<br>
    将MFRC522模块的MOSI引脚连接到Arduino的数字针脚11。<br>
    将MFRC522模块的MISO引脚连接到Arduino的数字针脚12。<br>
    将MFRC522模块的RST引脚连接到Arduino的数字针脚9。<br>
    将8个数字输出引脚分别连接到电子锁的控制引脚。在代码中，它们被定义为K1到K8，它们分别连接到Arduino的数字针脚2到数字针脚16。



- #### 源代码

```
//Viral Science
//RFID
#include <SPI.h>
#include <MFRC522.h>
#include <TimerOne.h>
#define SS_PIN 10  //定义SDA即信号输入口（读取）
#define RST_PIN 9   //定义RST即断点输入口（复位）
MFRC522 mfrc522(SS_PIN, RST_PIN);   // Create MFRC522 instance.（创建一个该项目）
int K1 = 2;
int K2 = 3;
int K3 = 4;
int K4 = 5;
int K5 = 6;//语音播放模块
int K6 = 14;
int K7 = 15;
int K8 = 16;
int a = 0;//定时器用

void timerIsr()
{
  a++;
}
void setup()
{
  Serial.begin(9600);   // Initiate a serial communication
  SPI.begin();      // Initiate  SPI bus      （初始化SPI总线）
  mfrc522.PCD_Init();   // Initiate MFRC522    （初始化MFRC522）
  Serial.println("Put your card to the reader...");
  Serial.println();
  pinMode(K1, OUTPUT);
  pinMode(K2, OUTPUT);
  pinMode(K3, OUTPUT);
  pinMode(K4, OUTPUT);
  pinMode(K5, OUTPUT);
  pinMode(K6, OUTPUT);
  pinMode(K7, OUTPUT);
  pinMode(K8, OUTPUT);
  digitalWrite(K1, HIGH);
  digitalWrite(K2, HIGH);
  digitalWrite(K3, HIGH);
  digitalWrite(K4, HIGH);
  digitalWrite(K5, HIGH);
  digitalWrite(K6, HIGH);
  digitalWrite(K7, HIGH);
  digitalWrite(K8, HIGH);
  Timer1.initialize(100000);
  Timer1.attachInterrupt( timerIsr );
}
void loop()
{
  if (a > 1) //时间大于1秒
  {
    digitalWrite(K1, HIGH);
    digitalWrite(K2, HIGH);
    digitalWrite(K3, HIGH);
    digitalWrite(K4, HIGH);
    digitalWrite(K5, HIGH);
    digitalWrite(K6, HIGH);
    digitalWrite(K7, HIGH);
    digitalWrite(K8, HIGH);
  }
  // Look for new cards       （找卡————是否识别到新卡，如果无，返回数值）
  if ( ! mfrc522.PICC_IsNewCardPresent())
  {
    return;
  }
  // Select one of the cards    （选择识别卡————验证NUID是否可读，读不出就返回数值）
  if ( ! mfrc522.PICC_ReadCardSerial())
  {
    return;
  }
  //Show UID on serial monitor
  //Serial.print("UID tag :");
  String content = "";
  byte letter;
  for (byte i = 0; i < mfrc522.uid.size; i++)       // 将NUID保存到nuidPICC数组
    Serial.print(mfrc522.uid.uidByte[i] < 0x10 ? " 0" : " ");   //将字节数组以十六进制值的形式转储到串行的辅助例程
  {
    Serial.print(mfrc522.uid.uidByte[i], HEX);    //HEX为数据转十六进制输出
    content.concat(String(mfrc522.uid.uidByte[i] < 0x10 ? " 0" : " "));
    content.concat(String(mfrc522.uid.uidByte[i], HEX));
  }
  //Serial.println();
  //Serial.print("Message : ");
  content.toUpperCase();
  if (content.substring(1) == "53 3E 2C AD" || content.substring(1) == "03 16 27 AD" || content.substring(1) == "D3 23 A3 AC" || content.substring(1) == "23 24 A0 AC" || content.substring(1) == "83 C2 92 AC") //change here the UID of the card/cards that you want to give access
  {
    if (content.substring(1) == "53 3E 2C AD")
    {
      Serial.println("A");
      digitalWrite(K1, LOW);
      digitalWrite(K2, HIGH);
      digitalWrite(K3, HIGH);
      digitalWrite(K4, HIGH);
      digitalWrite(K5, HIGH);
      digitalWrite(K6, HIGH);
      digitalWrite(K7, HIGH);
      digitalWrite(K8, HIGH);
      a = 0;
    }
    if (content.substring(1) == "03 16 27 AD")
    {
      Serial.println("B");
      digitalWrite(K1, HIGH);
      digitalWrite(K2, LOW);
      digitalWrite(K3, HIGH);
      digitalWrite(K4, HIGH);
      digitalWrite(K5, HIGH);
      digitalWrite(K6, HIGH);
      digitalWrite(K7, HIGH);
      digitalWrite(K8, HIGH);
      a = 0;
    }
    if (content.substring(1) == "D3 23 A3 AC")
    {
      Serial.println("C");
      digitalWrite(K1, HIGH);
      digitalWrite(K2, HIGH);
      digitalWrite(K3, LOW);
      digitalWrite(K4, HIGH);
      digitalWrite(K5, HIGH);
      digitalWrite(K6, HIGH);
      digitalWrite(K7, HIGH);
      digitalWrite(K8, HIGH);
      a = 0;
    }
    if (content.substring(1) == "23 24 A0 AC")
    {
      Serial.println("D");
      digitalWrite(K1, HIGH);
      digitalWrite(K2, HIGH);
      digitalWrite(K3, HIGH);
      digitalWrite(K4, LOW);
      digitalWrite(K5, HIGH);
      digitalWrite(K6, HIGH);
      digitalWrite(K7, HIGH);
      digitalWrite(K8, HIGH);
      a = 0;
    }
    if (content.substring(1) == "83 C2 92 AC")
    {
      Serial.println("E");
      digitalWrite(K1, HIGH);
      digitalWrite(K2, HIGH);
      digitalWrite(K3, HIGH);
      digitalWrite(K4, HIGH);
      digitalWrite(K5, LOW);
      digitalWrite(K6, HIGH);
      digitalWrite(K7, HIGH);
      digitalWrite(K8, HIGH);
      a = 0;
    }
  }

  else   {
    Serial.println(" Access denied");
  }
}
```


### part 2 主动识别演奏：超声波测距播放

- #### 程序逻辑
该程序利用超声波传感器检测不同距离来控制无源蜂鸣器发出不同音调的声音，并结合RGB LED显示出不同颜色的灯光

<img src="img/2/38.png">

- #### 接线图
<img src="img/2/40.png">

- #### 效果展示

<iframe frameborder="0" width="960px" height="540px" src="//player.bilibili.com/player.html?aid=908249890&bvid=BV1AM4y1C71B&cid=1043386909&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>

- #### 源代码

```
#define NTC0 -1
#define NTC1 262
#define NTC2 294
#define NTC3 330
#define NTC4 350
#define NTC5 393
#define NTC6 441
#define NTC7 495

const int TrigPin = 2;
const int EchoPin = 3;
float cm;
int tonepin=8;   

int redPin = 11;
int greenPin = 10;
int bluePin = 9;

void setup()
{
Serial.begin(9600);
pinMode(TrigPin, OUTPUT);
pinMode(EchoPin, INPUT);
pinMode(tonepin,OUTPUT);

pinMode(redPin, OUTPUT);
pinMode(greenPin, OUTPUT);
pinMode(bluePin, OUTPUT);
}

void loop()
{
digitalWrite(tonepin, LOW);

digitalWrite(TrigPin, LOW); //低高低电平发一个短时间脉冲去TrigPin
delayMicroseconds(2);
digitalWrite(TrigPin, HIGH);
delayMicroseconds(10);
digitalWrite(TrigPin, LOW);

cm = pulseIn(EchoPin, HIGH) / 58.0; //将回波时间换算成cm
cm = (int(cm * 100.0)) / 100.0; //保留两位小数

if (cm>=1 && cm<=5){
  digitalWrite(tonepin, HIGH);
  tone(tonepin,NTC1);
  setColor(0, 255, 0); // 红色亮
  delay(1000);   
  noTone(tonepin);}

else if (cm>=6 && cm<=10){
  digitalWrite(tonepin, HIGH);
  tone(tonepin,NTC2);
  setColor(255, 0, 0); 
  delay(1000);   
  noTone(tonepin);}

else if (cm>=11 && cm<=15){
  digitalWrite(tonepin, HIGH);
  tone(tonepin,NTC3);
  setColor(0, 0, 255); 
  delay(1000);   
  noTone(tonepin);}

else if (cm>=16 && cm<=20){
  digitalWrite(tonepin, HIGH);
  tone(tonepin,NTC4);
  setColor(80, 0, 80); 
  delay(1000);   
  noTone(tonepin);}

else if (cm>=21 && cm<=25){
  digitalWrite(tonepin, HIGH);
  tone(tonepin,NTC5);
  setColor(255, 0, 255); 
  delay(1000);   
  noTone(tonepin);}

else if (cm>=26 && cm<=30){
  digitalWrite(tonepin, HIGH);
  tone(tonepin,NTC6);
  setColor(255, 0, 0); 
  delay(1000);   
  noTone(tonepin);}

else if (cm>=31 && cm<=35){
  digitalWrite(tonepin, HIGH);
  tone(tonepin,NTC7);
  setColor(0, 0, 255); 
  delay(1000);   
  noTone(tonepin);}

} 

void setColor(int red, int green, int blue)
{
  analogWrite(redPin, 255-red);
  analogWrite(greenPin, 255-green);
  analogWrite(bluePin, 255-blue);  
}
```





## reference
[Arduino](https://www.arduino.cc/)<br>
[语音播放模块（DY-SV5W）](https://blog.csdn.net/qq_36955622/article/details/103512824)<br>
[RFID工作原理及RC522模块介绍](https://blog.csdn.net/qq78442761/article/details/105432385/?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-0--blog-128687619.pc_relevant_multi_platform_whitelistv4&spm=1001.2101.3001.4242.1&utm_relevant_index=3)<br>
[arduino rc522模块使用](https://blog.csdn.net/economics3/article/details/128687619?spm=1001.2101.3001.6650.2&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EYuanLiJiHua%7EPosition-2-128687619-blog-82667116.pc_relevant_3mothn_strategy_recovery&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EYuanLiJiHua%7EPosition-2-128687619-blog-82667116.pc_relevant_3mothn_strategy_recovery&utm_relevant_index=5)<br>
[Arduino Sensor Shield v5 传感器扩展板](https://cloud.tencent.com/developer/article/1691985)<br>