# processing
### processsing简介

Processing 在 2001 年诞生于麻省理工学院（MIT）的媒体实验室，主创者为 Ben Fry 和 Casey Reas，项目发起的初衷，本是为了满足他们自身的教学和学习需要。后来，当Casey在意大利的伊夫雷亚交互设计学院（Interaction Design Institute Ivrea）进行教学的时候，基于Processing，衍生出了Wiring和Arduino项目。随着时间的推移，又诞生了多个语言的版本，比如基于JavaScript的Processing.js，还有基于Python、Ruby、ActionScript以及Scala等版本。而当前的Processing，成立了相应的基金会，由基金会负责软件的开发和维护工作。
Processing项目是Java开发的，所以Processing天生就具有跨平台的特点，同时支持Linux、Windows以及Mac OSX三大平台，并且支持将图像导出成各种格式。对于动态应用程序，甚至可以将 Processing 应用程序作为 Java™ applet 导出以用在 Web 环境内。当然，为了降低设计师的学习门槛，用Processing进行图形设计的编程语言并不是Java，而是重新开发了一门类C的编程语言，这也让非计算机科班出身的设计师很容易上手。这里要多提一句，Processing支持OpenGL和WebGL，不但可以渲染2D图形，还可以渲染3D图形。
在过去的2015年，随着移动设备的普及，以及各大浏览器厂商对HTML5的支持日渐成熟，Processing也迎来了一次重大的升级。不但对开发工具做了优化和完善，也开始逐步支持Android应用的开发。Web方面，基于HTML5，重新开发了JavaScript版本的Processing，并且单独为其提供了Web开发工具，同时这也让Processing在网页上开发应用变的更加简单便捷。这里顺便提及一点的是，Processing可不只是能够渲染漂亮的图形，还支持与其他软件的通信，结合之前提到的Arduino项目，甚至可以和外部硬件进行交互！

> Processing可供免费下载使用，官网：https://processing.org



### processsing环境搭建

1. Processing 环境：
   第一步是安装 Processing 环境。去到 Processing.org（https://processing.org/download/), 单击Download Processing 并选择您的操作系统。此外，还需要确保 Java 技术已经可用。在windows上，下载解压后直接运行processing.exe即可。
   这应该会弹出 Processing Development Environment（PDE 或 Processing IDE），如图 1 所示。占此窗口较大的部分是文本编辑器。如果输入图中所示的两行代码，然后单击 Run（左上角的三角形），出现一个窗口，显示您所输入的简单程序（或 Processing 术语所指的 sketch）的结果。单击 Stop（左上角的方框）退出程序，窗口消失。

2. Processing 语言
   Processing 是用 Java 编程语言写的，并且 Java 语言也是在语言树中最接近 Processing 的。所以，如果您熟悉 C 或 Java 语言，Processing 将很容易学。并且在程序如何构造方面，也作了一些简化。Processing 并不包括 Java 语言的一些较为高级的特性，但这些特性中的很多特性均已集成到了 Processing， 所以您无需了解它们。
   之所以选择 Java 语言是因为 Processing 应用程序被翻译成 Java 代码执行。选择 Java 范型简化了这种翻译并让开发和执行可视化程序变得十分简单和直观。

3. 图形环境
   在 Processing 内进行开发涉及到的是 PDE 和显示窗口。2-D 图形的坐标系如图 2 所示。size 关键字以像素为单位定义了显示窗口的大小并且通常都是 Processing 应用程序内的首要步骤。

   

   如图 2 所示，size 关键字指定显示窗口的 X 和 Y 坐标。line 关键字则会在两个像素点之间绘制一条线（以 x1、y1 to x2、y2 的格式）。请注意，超出屏幕边界（size 定义的边界外）画线并非不允许，只是被忽略了而已。
   本文无意对此做深入探讨，但 size 接受可选的第三个参数 mode。 mode 用来定义要使用的呈现引擎并支持 PDF（直接呈现为 Adobe® PDF 文档）、OPENGL （利用一个可用的 Open-GL 图形适配器）、P3D（为了迅速的 3-D 呈现）等。默认的是 JAVA2D，它最适合于高质量的 2-D 成像。
   现在，我们来看一些基本的图形原语，然后再深入探讨几个示例应用程序。

   

4. 图形原语
   Processing 包含了大量各种各样的几何形状以及这些形状的控件。
5. Processing 应用程序的结构
   至此，通过几个简单的脚本，您已经对 Processing 语言有了大致的了解，但这些脚本是一些非结构化的代码，只提供了应用程序的一些简单元素。Processing 应用程序是有一定结构的，这一点在开发能够持续运行且随时更改显示窗口的图形应用程序（比如动画）时非常重要。在这种情况下，就凸显了 setup 和 draw 这两个函数的重要性。
   setup 函数用于初始化，由 Processing 运行时执行一次。通常，setup 函数包含 size 函数（用于定义窗口的边界）以及在操作期间要使用的变量的初始化。Processing 运行时会不断执行 draw 函数。每次 draw 函数结束后，就会在显示窗口绘制一个新的画面，并且 draw 函数也会被再次调用。默认的绘制速度是每秒 60 个画面，但是您也可以通过调用 frameRate 函数来更改这个速度。
   此外，还可以使用 noLoop 和 draw 来控制在何时绘制画面。noLoop 函数会导致绘制停止，而使用 loop 函数则可以重新开始绘制。通过调用 redraw 可以控制 draw 在何时调用。
