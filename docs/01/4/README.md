# processing
## processsing简介

Processing 在 2001 年诞生于麻省理工学院（MIT）的媒体实验室，主创者为 Ben Fry 和 Casey Reas，项目发起的初衷，本是为了满足他们自身的教学和学习需要。后来，当Casey在意大利的伊夫雷亚交互设计学院（Interaction Design Institute Ivrea）进行教学的时候，基于Processing，衍生出了Wiring和Arduino项目。随着时间的推移，又诞生了多个语言的版本，比如基于JavaScript的Processing.js，还有基于Python、Ruby、ActionScript以及Scala等版本。而当前的Processing，成立了相应的基金会，由基金会负责软件的开发和维护工作。
Processing项目是Java开发的，所以Processing天生就具有跨平台的特点，同时支持Linux、Windows以及Mac OSX三大平台，并且支持将图像导出成各种格式。对于动态应用程序，甚至可以将 Processing 应用程序作为 Java™ applet 导出以用在 Web 环境内。当然，为了降低设计师的学习门槛，用Processing进行图形设计的编程语言并不是Java，而是重新开发了一门类C的编程语言，这也让非计算机科班出身的设计师很容易上手。这里要多提一句，Processing支持OpenGL和WebGL，不但可以渲染2D图形，还可以渲染3D图形。
在过去的2015年，随着移动设备的普及，以及各大浏览器厂商对HTML5的支持日渐成熟，Processing也迎来了一次重大的升级。不但对开发工具做了优化和完善，也开始逐步支持Android应用的开发。Web方面，基于HTML5，重新开发了JavaScript版本的Processing，并且单独为其提供了Web开发工具，同时这也让Processing在网页上开发应用变的更加简单便捷。这里顺便提及一点的是，Processing可不只是能够渲染漂亮的图形，还支持与其他软件的通信，结合之前提到的Arduino项目，甚至可以和外部硬件进行交互！

> Processing可供免费下载使用，官网：https://processing.org



## processsing环境搭建

1. Processing 环境：
   第一步是安装 Processing 环境。去到 Processing.org（https://processing.org/download/), 单击Download Processing 并选择您的操作系统。此外，还需要确保 Java 技术已经可用。在windows上，下载解压后直接运行processing.exe即可。
   这应该会弹出 Processing Development Environment（PDE 或 Processing IDE），占此窗口较大的部分是文本编辑器。如果输入图中所示的两行代码，然后单击 Run（左上角的三角形），出现一个窗口，显示您所输入的简单程序（或 Processing 术语所指的 sketch）的结果。单击 Stop（左上角的方框）退出程序，窗口消失。

2. Processing 语言
   Processing 是用 Java 编程语言写的，并且 Java 语言也是在语言树中最接近 Processing 的。所以，如果您熟悉 C 或 Java 语言，Processing 将很容易学。并且在程序如何构造方面，也作了一些简化。Processing 并不包括 Java 语言的一些较为高级的特性，但这些特性中的很多特性均已集成到了 Processing， 所以您无需了解它们。
   之所以选择 Java 语言是因为 Processing 应用程序被翻译成 Java 代码执行。选择 Java 范型简化了这种翻译并让开发和执行可视化程序变得十分简单和直观。

3. 图形环境
   在 Processing 内进行开发涉及到的是 PDE 和显示窗口。2-D 图形的坐标系如图 2 所示。size 关键字以像素为单位定义了显示窗口的大小并且通常都是 Processing 应用程序内的首要步骤。

   size 关键字指定显示窗口的 X 和 Y 坐标。line 关键字则会在两个像素点之间绘制一条线（以 x1、y1 to x2、y2 的格式）。超出屏幕边界（size 定义的边界外）画线并非不允许，只是被忽略了而已。
    size 接受可选的第三个参数 mode。 mode 用来定义要使用的呈现引擎并支持 PDF（直接呈现为 Adobe® PDF 文档）、OPENGL （利用一个可用的 Open-GL 图形适配器）、P3D（为了迅速的 3-D 呈现）等。默认的是 JAVA2D，它最适合于高质量的 2-D 成像。


4. 图形原语
   Processing 包含了大量各种各样的几何形状以及这些形状的控件。
5. Processing 应用程序的结构
   至此，通过几个简单的脚本，您已经对 Processing 语言有了大致的了解，但这些脚本是一些非结构化的代码，只提供了应用程序的一些简单元素。Processing 应用程序是有一定结构的，这一点在开发能够持续运行且随时更改显示窗口的图形应用程序（比如动画）时非常重要。在这种情况下，就凸显了 setup 和 draw 这两个函数的重要性。
   setup 函数用于初始化，由 Processing 运行时执行一次。通常，setup 函数包含 size 函数（用于定义窗口的边界）以及在操作期间要使用的变量的初始化。Processing 运行时会不断执行 draw 函数。每次 draw 函数结束后，就会在显示窗口绘制一个新的画面，并且 draw 函数也会被再次调用。默认的绘制速度是每秒 60 个画面，但是您也可以通过调用 frameRate 函数来更改这个速度。
   此外，还可以使用 noLoop 和 draw 来控制在何时绘制画面。noLoop 函数会导致绘制停止，而使用 loop 函数则可以重新开始绘制。通过调用 redraw 可以控制 draw 在何时调用。

## processing与arduino联动实验
### Arduino与processing联通过程
这两个程序的关系是，Arduino程序通过超声波传感器读取距离值，并通过串口通信将距离值发送到Processing程序。Processing程序则根据距离值来改变圆球的大小，从而实现交互效果。
具体来说，Arduino程序通过Serial.begin()函数初始化串口通信，并通过Serial.println()函数将距离值发送到串口。Processing程序则通过Serial port = new Serial(this, "COM3", 9600);语句连接串口，并使用port.available()函数读取串口缓冲区中是否有可读数据。如果有数据，就使用port.readStringUntil('\n')函数读取一行数据，并使用map()函数将距离值映射到合适的圆球大小。最后，Processing程序通过ellipse()函数画出圆球，并实现交互效果。

在实际应用中，需要将Arduino程序上传到Arduino板子中，并将Arduino板子通过USB线连接到计算机上。然后，运行Processing程序，在串口连接的窗口中选择对应的串口号和波特率，即可实现Arduino和Processing程序之间的联通。

- #### Arduino引线连接方法如下:
1. 将超声波传感器的VCC引脚连接到Arduino的5V引脚，GND引脚连接到
Arduino的GND引脚。
2. 将超声波传感器的Trig引脚连接到Arduino的9号引脚，Echo引脚连接到
Arduino的10号引脚。

- #### 实物连接图
<img src="img/1/25.jpg">

- #### arduino源代码

```
const int trigPin = 9; //超声波传感器触发引脚
const int echoPin = 10; //超声波传感器回响引脚
const int ledPin = 13; //LED引脚

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(ledPin, OUTPUT);
  Serial.begin(9600); //启动串口通信
}
void loop() {
  // 发送10微秒的高电平信号，以触发传感器发送超声波
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  // 读取回响时间，并计算出距离
  long duration = pulseIn(echoPin, HIGH);
  float distance = duration * 0.034 / 2;

  // 控制LED灯的亮灭，距离小于20cm时亮灯，否则灭灯
  if (distance < 20) {
    digitalWrite(ledPin, HIGH);
  } else {
    digitalWrite(ledPin, LOW);
  }

  Serial.println(distance); //在串口监视器中输出距离值
  delay(100); //延迟100毫秒
}
```

- #### processing源代码

```
import processing.serial.*;

Serial port;
int radius = 50;

void setup() {
  size(500, 500);
  port = new Serial(this, "COM3", 9600); //连接串口
}

void draw() {
  background(255);

  // 读取距离值
  if (port.available() > 0) {
    String distanceStr = port.readStringUntil('\n');
    if (distanceStr != null) {
      distanceStr = distanceStr.trim();
      float distance = float(distanceStr);
      // 根据距离值改变圆球的大小
      radius = int(map(distance, 0, 50, 20, 100));
    }
  }

  // 画圆球
  fill(255, 0, 0);
  noStroke();
  ellipse(width/2, height/2, radius, radius);
}
```


- #### 效果展示
<img src="img/0/3.gif">

### processing小游戏
- #### 效果展示
 
<embed src="img/0/0.mp4" width="500" heigh="500"/>

<iframe frameborder="0" width="960px" height="540px" src="//player.bilibili.com/player.html?aid=610648344&bvid=BV1k84y1P7R2&cid=1043389112&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>


- #### 源代码：
```
import ddf.minim.*;
Minim minim;
AudioPlayer music;
Back back;//背景类
Main main;//主机类
PFont Font1,Font2;//字体
Enemey[] enemey=new Enemey[10];//敌机类
boolean[] keys = new boolean[128];
Bullet bullet;//子弹一
Bullet bullet1;//子弹二
int LF=10;//接收换行符的acsii码
boolean shoot;
int correction=-20;
int alpha=255;
int score=0;
int bestScore;
int life;
int times = 1;
float voice = 0;
boolean gameOver;
boolean regameOver;
void setup()
{
  size(600,400);//画布大小
  minim=new Minim(this);
  music=minim.loadFile("music.mp3",1024);//导入音乐
  back = new Back(0,0);//初始化背景
  Font1 = createFont("fangsong",50);
  Font2 = createFont("fangsong",30);
  main = new Main(250,300);//初始化主机
  for(int i=0;i<10;i++)
  {
    enemey[i] = new Enemey(random(0,600),random(-200,-100));
  }//初始化敌人
  bullet = new Bullet(main.x-20,main.y+20,correction,alpha);
  bullet1= new Bullet(main.x+65,main.y+20,correction+85,alpha);
}
void draw()
{
  if(gameOver==false)
  {
    showBegin();
  }
  if(keyPressed && key=='s' && !gameOver)
  {
    gameOver=true;
    music.loop();
  }
  if(!gameOver)
  {
    return;
  }
  voice=music.mix.level();
  regameOver=false;
  if(life<=0)
  {
    showOver();
    if(keyPressed && key=='r' && !regameOver)
    {
      reGame();
    }
    if(!regameOver)
    {
      return;
    }
  }
  back.display();//画布流动
  main.display();//主机模型和方向
  interFace();//显示分数，生命
  bullet.update();
  bullet.display();
  bullet1.update();
  bullet1.display();
  for(int i=0;i<10;i++)
  {
    enemey[i].display();
    enemey[i].update();
  if(enemey[i].bruise())
  {
    life-=1;
    enemey[i].life=0;
    enemey[i].die();
  }//判断敌机是否撞到主机 如果是主机生命减一
  if(enemey[i].check())
  {
    enemey[i].life-=1;
    if(enemey[i].direction==1)
    {
      bullet.die();//左边击中
    }
    if(enemey[i].direction==2)
    {
      bullet1.die();//右边击中
    }
    enemey[i].die();//判断敌机是否死亡
  }//判断敌机是否被击中 如果是敌机生命减一
  if(enemey[i].reach())
  {
    enemey[i].x = random(0,600);
    enemey[i].y = random(-50,-30);
    enemey[i].life = enemey[i].type+1;
  }//判断敌机是否安全到达 如果是初始化其位置
  }
}
//-----------------------------------------------------------------------按键函数
void keyPressed()
{
  keys[key] = true;
}
void keyReleased()
{
  keys[key] = false;
}
//-----------------------------------------------------------------------界面
void interFace()
{
  int difficulty=0;
  for(int i=0; i<10; i++)
  {
    difficulty = difficulty+enemey[i].type;
  }
  PImage[] png;
  fill(255);
  textSize(20);
  text("Score:",25,40);
  text(score,90,40);
  text("DY:",130,40);
  text("V:",200,40);
  text("Mainlife:",365,40);
  png = new PImage[5];
  for(int i=0;i<life;i++)
  {
    int j=i+1;
    png[i] = loadImage("Mainlife.png");
    png[i].resize(25,25);
    image(png[i],425+j*30,22);
  }
  if(score>100*times)
  {
    life+=1;
    times+=1;
    if(life>5)
    {
      life=5;
    }
  }
  fill(255);
  rect(220,27.5,120,10,10);
  noStroke();
  fill(bullet.v*(255/15),150,0);
  rect(220,27.5,bullet.v*(120/15),10,10);
  if(difficulty>=13)
  {
    fill(255,0,0);
  }
  if(difficulty<13 && difficulty>8)
  {
    fill(255,255,0);
  }
  if(difficulty<=8)
  {
    fill(0,255,0);
  }
  ellipse(170,33,15,15);
}
//-----------------------------------------------------------------------开始
void showBegin()
{
  fill(0);
  rect(0,0,width,height);
  fill(255);
  textFont(Font1);
  text("太 空 大 战",160,180);
  textFont(Font2);
  text("按's'开始",230,240);
}
//-----------------------------------------------------------------------结束
void showOver()
{
  music.pause();
  fill(0);
  rect(0,0,width,height);
  fill(255);
  textFont(Font1);
  text("太 空 大 战",160,180);
  textFont(Font2);
  text("按'r'重新开始",210,240);
  text("Score:",200,90);
  text(score,350,90);
  if(bestScore<score)
  {
    bestScore=score;
  }
  text("bestScore:",200,120);
  text(bestScore,350,120);
}
void reGame()
{
  main = new Main(250,300);
  regameOver=true;
  score=0;
  life=3;
  for(int i=0;i<10;i++)
  {
    enemey[i] = new Enemey(random(0,600),random(-50,-30));
  }
  minim=new Minim(this);
  music=minim.loadFile("music.mp3",1024);//导入音乐
  music.loop();
}
//-----------------------------------------------------------------------背景类
class Back
{
  PImage[] background;
  int x;
  int y;
  int y1;
  int y2;
  Back(int x,int y)
  {
    background = new PImage[2];
    this.y1=y;
    this.y2=y-400;
    this.x=x;
    for (int i=0;i<2;i++)
    {    
      background[i] = loadImage("background.jpg");
    }
  }
  void display()
  {
    y1++;
    y2++;
    if(y1==400)
    {
      y1=-400;
    }
    if(y2==400)
    {
      y2=-400;
    }
    tint(255,255);
    image(background[0],x,y1);
    image(background[1],x,y2);   
  }
}
//-----------------------------------------------------------------------主机类
class Main
{
  int r;
  int x;
  int y;
  int state;
  boolean[] direction;
  PImage aircraft;
  Main(int x,int y)
  {
    this.x=x;
    this.y=y; 
    life = 3;
    r=20;
    direction = new boolean[4];
    aircraft=loadImage("Main.png");
  }
  void up()
  {
    if(keys['w'] && y>0)
    {
      y-=2;
    }
  }
  void down()
  {
    if(keys['s'] && y<300)
    {
      y+=2;
    }
  }
  void left()
  {
    if(keys['a'] && x>0)
    {
      x-=2;
    }
  }
  void right()
  {
    if(keys['d'] && x<500)
    {
      x+=2;
    }
  }
  void display()
  {
    up();
    down();
    left();
    right();
    tint(255,255);
    image(aircraft,x,y);
  }
}
//-----------------------------------------------------------------------子弹类
class Bullet
{
  int x;
  int y;
  int r;
  int v;
  boolean shoots;
  int alpha;
  int corrections;
  PImage png;
  Bullet(int x,int y,int corrections,int alpha)
  {
    this.alpha=alpha;
    this.corrections=corrections;
    this.x=x;
    this.y=y;
    png = loadImage("Bullet.png");
    png.resize(50,50);
    r=5;
  }
  void update()
  {
    if(voice<=0.01)
    {
      voice=0.01;
    }
    if(voice>=0.2)
    {
      voice=0.2;
    }
    v=(int)map(voice,0.01,0.2,1,15);
    println(v);
    y=y-v;
  }
  void display()
  {
    tint(255,alpha);
    image(png,x,y);
    if(y<-10)
    {
      alpha=255;
      r=5;
      x=main.x+corrections;
      y=main.y+20;
    }
  }
  boolean check()
  {
    if(y<=20)
    {
      return true;     
    }
    return false;
  }
  void die()
  {
    alpha=0;
    r=-100;    
  }
}
//-----------------------------------------------------------------------敌人类
class Enemey
{
  float x;
  float y;
  float v=1;
  float a=1.5;
  int r;
  int type;
  boolean exist;
  int life;
  PImage[] png;
  PImage[] png1;
  int direction;
  Enemey(float x,float y)
  {
    png = new PImage[3];
    png1 = new PImage[2];
    this.x=x;
    this.y=y;
    r=15;
    type = (int)random(0,3);
    life = type+1;
    String a = "Explosion.png";
    String b = "enemey"+type+".png";
    png[type] = loadImage(b); 
    png[type].resize(50,50);
    for(int i=0;i<2;i++)
    {
      png1[i] = loadImage(a); 
      png1[i].resize(50,50);
    }
  }
  void update()
  {
    if(type == 0)
    v=1;
    if(type == 1)
    v=1.5;
    if(type == 2)
    v=2;   
    v=v+a;
    y=y+v;    
  }
  void display()
  {
    tint(255,255);
    image(png[type],x,y);
  }
  boolean bruise()
  {
    if(dist(x-5,y,main.x+22.5,main.y)<main.r+r)
    {
      return true;
    }
    return false;
  }
  boolean check()
  {
    if(dist(x,y,bullet.x,bullet.y)<bullet.r+r)
    {
    direction = 1;
    return true;    
    }
    if(dist(x,y,bullet1.x,bullet1.y)<bullet1.r+r)
    {
    direction = 2;  
    return true;    
    }
    return false;
  }
  void die()
  {
    if(life<=0)
    {      
      //explosion.display();
      if(type==0)
      {
        score++;
      }
      if(type==1)
      {
        score+=3;
      }
      if(type==2)
      {
        score+=5;
      }
      for(int i=0;i<2;i++)
      {
        image(png1[i],x,y);
      }
      x = random(0,600);
      y = random(-50,-30);
      direction = 0;  
      life = type+1;
    }
  }
  boolean reach()
  {
    if(y>height+50)
    {
    return true;    
    }
    return false;
  }
}
```

## reference
[processing](https://processing.org/)<br>
[processing 教程](https://www.oschina.net/informat/processing+%E6%95%99%E7%A8%8B)<br>
[Processing+Arduino互动编程](https://blog.csdn.net/wangpuqing1997/article/details/105201551)<br>
