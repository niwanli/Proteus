Proteus实验指导手册
==================
　　　
# 第1章   前言

## 1.1  编写目的
《微机原理与接口技术》是北京邮电大学为通信工程、信息工程、电子信息工程、电子科学与技术、计算机科学与技术、网络工程等工科电子信息类专业开设的一门必修课程。为了配合该课程的学习，我们编写了本实验指导手册。在教学过程中，用于指导学生进一步理解教材内容并验证所学知识，也可给从事该课程教学的教师提供一个巩固和深化课堂效果的教学环境。
　　

本实验指导手册，突出强调了软硬件结合的思维方法和实践动手能力的培养，侧重微机系统的设计。指导手册中的实验全部按照课程内容进行规划，实验题目均来自于课程教材（*田辉，徐慧民等. 微机原理与接口技术[M]. 北京：高等教育出版社，2015.*）,以更好地适应教学的需要。

本实验指导手册的主要任务是使学生从系统的角度出发，掌握微机系统的基本组成 、工作原理、接口电路及应用方法，使学生掌握微机系统的开发能力以及熟悉Proteus仿真平台的使用方法。

## 1.2  适用范围

本实验指导手册适合以下人员阅读：

* 通信工程、电子信息、计算机等工科专业的教学人员
* 对Proteus仿真感兴趣的广大科技人员

## 1.3  内容结构

本实验指导手册一共分为7个章节和2个附录，具体内容概括如下：

* 第1章主要介绍了本实验指导手册的编写目的、适用范围以及内容结构。
* 第2章主要介绍了Proteus仿真平台的安装过程，以及Proteus软件原理图绘制界面的相关工具和工程管理的操作步骤。
* 第3章主要介绍了实验中需要使用的元件及其管脚功能、工作原理。
* 第4章主要介绍了实验中需要使用的数据传送方式。
* 第5章主要介绍了实验要求和实验目的。
* 第6章主要介绍了Proteus电路中各模块的设计思路和原理图绘制过程，以及设计代码的流程图。
* 第7章主要介绍了硬件和软件联调的方法。
* 附录一中展示了Proteus中绘制的完整原理图。
* 附录二中展示了完整的汇编语言源程序。
　
# 第2章   Proteus仿真平台使用指导

## 2.1  Proteus仿真平台简介

Proteus是英国Labcenter公司开发的电路分析与实物仿真及印刷电路板设计软件，它运行于Windows操作系统上，可以仿真、分析各种模拟电路与集成电路。Proteus提供了大量模拟与数字元器件、外部设备和各种虚拟仪器，特别是它具有对常用控制芯片及其外围电路组成的综合系统的交互仿真功能。本实验指导手册主要介绍如何利用Proteus绘制电路原理图，以及如何利用外部编译器编译8086汇编程序并进行基于8086微处理器的VSM仿真。

## 2.2  Proteus软件的安装
### 2.2.1  安装准备

（1）系统要求

本文作者是在Windows 7操作系统的环境下进行安装的，如果你的电脑是其他操作系统，可能会出现无法安装的情况，比如Linux系统天生就不支持Proteus软件。如果你是Windows操作系统的其他版本，可能需要在解决某些环境配置问题后才能正常安装运行。安装过程中遇到的具体问题，请同学们自行上网解决，此处不做赘述。

（2）安装文件

本文作者用到的安装文件主要是以下4个。如果你的电脑需要配置某些环境，那么可能会需要更多的环境配置文件，请根据安装过程提示的信息自行联网安装。

* Proteus 8.4 SP0 Pro-Demo Setup.exe
* Grassington North Yorkshire.lxk
* Update Proteus 8.4 SP0 Demo to PRO ENG v1.0.exe
* proteus8.4汉化包.zip

### 2.2.2  安装步骤

Proteus 8.4版本软件的安装步骤如下：

（1）点击Proteus 8.4 SP0 Pro-Demo Setup.exe程序进行安装；

（2）在安装过程中，有一个步骤会提示你选择证书。也就是说，需要我们选择证书文件Grassington North Yorkshire.lxk；

（3）在上面的安装完成之后，再运行Update Proteus 8.4 SP0 Demo to PRO ENG v1.0.exe；

（4）最后，只需要把汉化包解压出来的Translations文件复制到Proteus的安装目录下，并覆盖同名文件即可。

## 2.3  可视化界面及工具

软件安装成功后，运行Proteus软件并打开工程后，就会看到如图2-1所示的窗口界面。为了方便介绍，图中标记了窗口内各部分中文说明。下面简单介绍个部分的功能。

![](https://github.com/niwanli/Proteus/raw/master/pictures/0201.jpg "Proteus工作界面")

### 2.3.1  原理图编辑窗口

原理图编辑窗口是用来绘制原理图的，整个窗口被蓝色方框圈起来，元件要放到其中。需要注意的是，这个窗口是没有滚动条的，但可以用预览窗口来改变原理图的可视范围。正是由于这个与大多数软件不同的特点，使得很多初学者都难以适应该软件的操作，毕竟大多数人都习惯了使用鼠标上的滚动键来控制窗口的上下移动。但是，在Proteus软件中鼠标的滚动键只能用来控制视图的放大和缩小。那么我们要如何操作才能将视图进行移动呢？

视图的移动可以通过如下2种方式：

（1）单击预览窗口中想要显示的位置，这将使编辑窗口显示以鼠标为中心的内容。

（2）在编辑窗口内移动鼠标，先按下“Shift”键，然后用鼠标“撞击”视图的边框，这会使显示平移，把这称为Shift-Pan。

笔者比较推荐的做法是，大范围的视图移动采用方法1，小范围的视图移动采用方法2。某国人习惯于将类似的人或物进行比较，以便分出优劣。但笔者认为，世界的丰富多彩并没有优劣之分，对于这两种方法而言，你觉得哪种用着顺手就用哪种就好了。


## 2.3.2  预览窗口

预览窗口用于显示整个电路图的缩略图，单击预览窗口中想要显示的位置，将使编辑窗口显示以鼠标为中心的内容。

### 2.3.3  模式选择工具栏

模型选择工具栏主要用于切换当前工作模式，在绘制原理图时，根据需要选择不同的模式。在不同的模式下，预览窗口和对象选择器会显示不同的内容。主要的以下6个常用模式工具的功能：

（1）![](https://github.com/niwanli/Proteus/raw/master/pictures/image006.jpg "选择模式")：选择模式，用于选择对象。

（2）![](https://github.com/niwanli/Proteus/raw/master/pictures/image008.jpg "元器件选择模式")：元器件选择模式，用于放置元器件以及进行元器件库管理。

（3）![](https://github.com/niwanli/Proteus/raw/master/pictures/image010.jpg "接点模式")：接点模式，用于放置连接点。

（4）![](https://github.com/niwanli/Proteus/raw/master/pictures/image012.jpg "网络标号模式")：网络标号模式，用于给导线或者总线分支放置标号。

（5）![](https://github.com/niwanli/Proteus/raw/master/pictures/image014.jpg "总线模式")：总线模式，用于绘制总线。

（6）![](https://github.com/niwanli/Proteus/raw/master/pictures/image016.jpg "终端模式")：终端模式，用于选择电源、地等8种终端。
 
###2.3.4  元件列表

在点击“元件模式”按钮![](https://github.com/niwanli/Proteus/raw/master/pictures/image008.jpg "元器件选择模式")后，单击P按钮![](https://github.com/niwanli/Proteus/raw/master/pictures/image018.jpg "P按钮")会打开“选择元器件”对话框。在对话框中进行关键字搜索可以找到你所需要的元器件（前提是Proteus的元器件库里面有该元器件的模型），选择了一个元器件后，单击“确认”按钮，该元器件就会在元件列表中显示。以后要用到该元件时，只需要在元件列表中选择即可。

### 2.3.5  旋转/镜像控制按钮

Proteus提供了选择、镜像控制按钮，用来改变对象选择器中选中对象的方向。旋转、镜像控制按钮的功能如下所示：

（1）![](https://github.com/niwanli/Proteus/raw/master/pictures/image020.jpg "选择按钮")：选择按钮，用于将元器件进行90度的整数倍的旋转。

（2）![](https://github.com/niwanli/Proteus/raw/master/pictures/image022.jpg "元水平镜像按钮")：水平镜像，用于将元器件进行水平镜像操作。

（3）![](https://github.com/niwanli/Proteus/raw/master/pictures/image024.jpg "元垂直镜像按钮")：垂直镜像，用于将元器件进行垂直镜像操作。

### 2.3.6  仿真控制按钮

用户可以通过仿真控制按钮来观测电路的各种状态和输出。仿真按钮主要用于交互式仿真过程中的实时控制，其按钮功能如下所示：

（1）![](https://github.com/niwanli/Proteus/raw/master/pictures/image026.jpg "运行按钮")：运行按钮，点击后开始仿真，快捷键为Shift+F12。

（2）![](https://github.com/niwanli/Proteus/raw/master/pictures/image028.jpg "单步运行按钮")：单步运行，每点击一下，仿真进行一个步长的时间后停止。

（3）![](https://github.com/niwanli/Proteus/raw/master/pictures/image030.jpg "元暂停按钮")：暂停按钮，用于暂停交互仿真，也可以在单击暂停按钮后以单步形式继续仿真。

（4）![](https://github.com/niwanli/Proteus/raw/master/pictures/image032.jpg "停止按钮")：停止按钮，用于停止当前仿真。

## 2.4  工程管理

工程管理主要涉及到3个方面：新建工程，打开工程和工程保存。下面，就让我们来逐个学习工程管理的相关知识。这一小节的内容比较简单，同学们可以带着比较轻松的心情来阅读。

### 2.4.1  新建工程

新建工程一共需要6个步骤。在有的步骤中，我们需要修改默认参数；在有的步骤中，我们只需要在确认默认参数后点击“下一步”即可。

**步骤1**：鼠标单击“文件”菜单，选择“新建工程”

![](https://github.com/niwanli/Proteus/raw/master/pictures/image033.png "")

**步骤2**：在“新建工程向导：开始”里，修改“工程名称”和“工程路径”，并选择“新工程”按钮，然后单击“下一步”

![](https://github.com/niwanli/Proteus/raw/master/pictures/image034.png "")

**步骤3**：在“新建工程向导：Schematic Design”里，选择“DEFAULT”设计模板，然后单击“下一步”


![](https://github.com/niwanli/Proteus/raw/master/pictures/image036.png "")

**步骤4**：在“新建工程向导：PCB Layout”里，选择“不创建PCB布板设计”，然后单击“下一步”

![](https://github.com/niwanli/Proteus/raw/master/pictures/image038.png "")

**步骤5**：在“新建工程向导：Firmware”里，选择“创建固件项目”，系列选择8086，控制器选择8086，编译器选择MASM32，勾选“创建快速启动文件”，然后单击“下一步”

![](https://github.com/niwanli/Proteus/raw/master/pictures/image040.png "")

**步骤6**：在“新建工程向导：总结”里，确认各项信息之后，单击“完成”即可。

![](https://github.com/niwanli/Proteus/raw/master/pictures/image042.png "")

通过以上6个步骤，我们就建立好了一个新的工程项目，并且Proteus软件会自动弹出一个原理图绘制界面和一个源代码界面。接下来，我们就可以在原理图绘制界面里面进行硬件电路的设计，在源代码界面里面进行软件的设计了。

### 2.4.2  打开工程

打开工程和新建工程相比，操作要简单得多，只需要单击“文件”菜单，然后单击“打开工程”，最后找到已经建立好的工程所在位置，选中后单击“打开”即可。

![](https://github.com/niwanli/Proteus/raw/master/pictures/image044.png "")

### 2.4.3  保存工程

保存工程有两种方式，一种是直接单击保存按钮![](https://github.com/niwanli/Proteus/raw/master/pictures/image046.png "保存按钮")；另一种方式是先单击“文件”菜单，然后选择“保存工程即可”。
　　
# 第3章   元件介绍

## 3.1  地址锁存器74LS373

74LS373是三态输出的八D锁存器，74LS373的输入端D0～D7 可以直接与总线相连。当三态允许控制端口OE为低电平，并且锁存允许端口LE为高电平时，Q端口的数据随D端口的数据变化而变化。

![](https://github.com/niwanli/Proteus/raw/master/pictures/0301.jpg "")
　　
## 3.2  3-8译码器74LS138

74LS138为3线－8线译码器，当一个选通端E1为高电平，另两个选通端E2和E3为低电平时，可将地址端A、B、C的二进制编码在Y0至Y7对应的输出端以低电平译出。比如：当CBA=110时，Y6端输出低电平。

![](https://github.com/niwanli/Proteus/raw/master/pictures/0302.jpg "")
　　
## 3.3  总线收发器74LS245

74LS245是常用的芯片，用来驱动LED或者其他的设备，它是一种具有三态输出的8位同相双向总线收发器，可双向传输数据。

74LS245有两个控制信号：控制数据传送方向的信号AB/BA和输出允许信号CE。当CE无效时，缓冲器呈现高阻状态，74LS245在两个方向上都不能传送数据。当CE有效，AB/BA为高电平时，A0-A7为输入端，实现A到B的数据传输；当CE有效，AB/BA为低电平时，B0-B7为输入端，实现B到A的数据传输。
　　
![](https://github.com/niwanli/Proteus/raw/master/pictures/0303.jpg "")
　　
# 第4章   数据传送方式

CPU和外部设备之间的数据传送方式通常分为4种：无条件传送方式、查询传送方式、中断传送方式以及DMA方式。由于本次实验中只需要用到无条件传送方式，所以本章只详细介绍无条件传送方式。对于另外3种数据传送方式，请同学们根据自己的知识盲点去查阅教材中相应的知识点（第7章，第3小节）。


无条件传送是指CPU不管外部设备的状态，在需要和外部设备交换信息的时候，就用输入指令或输出指令和外部设备交换信息。在这种方式下，CPU和外部设备之间只有数据信息的传送，没有状态信息的传送。接口电路也比较简单，只有数据通道，一般就只有输出锁存器和输入缓冲器。

![](https://github.com/niwanli/Proteus/raw/master/pictures/0401.jpg "")

无条件传送主要用于外部设备总是处于准备好的状态，外部设备必须在微处理器限定的指令时间内准备就绪，并完成数据的接收或发送。为了保证数据传送的正确性，无条件传送方式常用于简单的外部设备控制。
　　
# 第5章   I/O口读写实验

## 5.1  实验要求

在Proteus仿真平台上，利用8086微处理器和相关外围芯片设计一个采用无条件传送方式控制的电路，要求当控制开关S0-S7打开时，对应的发光二极管VD0-VD7亮；当控制开关S0-S7闭合时，对应的发光二极管VD0-VD7不亮。编写相应的控制程序。

## 5.2  实验说明
一般情况下， CPU 的总线会挂很多器件，如何是这些器件不造成冲突，就需要使用一些总线隔离器件，如 74LS373、 74LS245。 74LS245 是三态总线收发器，本实验用它做输入缓冲器和输出锁存器，片选地址分别为 0008H 和 000CH。74LS373 是地址锁存器，本实验用它做 CPU 输出地址的锁存。

## 5.3  实验目的

（1）了解CPU常用端口的功能及连线方式；

（2）掌握74LS373、74LS138和74LS245等芯片的使用方法；

（3）熟悉无条件传送方式的工作原理；

（4）学会Proteus仿真平台的基本操作。

# 第6章  Proteus电路设计

## 6.1  电路元件

该电路中用到的仿真元件信息见表6-1。

![](https://github.com/niwanli/Proteus/raw/master/pictures/0501.jpg "")

## 6.2  地址锁存模块

### 6.2.1  地址锁存模块设计思路

由于8086的16位地址线和16位数据线复用管脚，为了将数据信号和地址信号分开，需要使用锁存器74LS373将地址信号进行锁存锁存，然后用来输出译码、片选。

由于每片74LS373只能锁存8位地址，如果需要锁存20位地址信号，那么一共需要使用3片373。但是本次实验只使用地址线的低4位来进行译码，所以只需要使用1片373进行锁存即可。

下图使用了2片373进行锁存，但是后面译码的时候只用到了第1片373锁存输出的A0到A3地址信号，第2片的地址锁存输出信号没有使用。

### 6.2.2  地址锁存模块Proteus制图

（1）首先，分别将两片74LS373的D0到D7管脚接到8086的AD[0..15]总线上；

（2）然后，将两片373的OE端口接地；

（3）接着，将8086的地址锁存信号ALE作为两片373的锁存允许信号，接到两片373的LE口；

（4）最后，画出地址锁存373的输出信号A0到A15即可。
   
![](https://github.com/niwanli/Proteus/raw/master/pictures/0601.jpg "")
 
## 6.3  译码/片选模块

### 6.3.1  译码/片选模块设计思路

由于基本输入和输出模块使用的两片双向数据传送器74LS245各需要1位片选信号，所以需要使用3-8译码器74LS138来实现译码、片选的功能。

### 6.3.2  译码/片选模块Proteus制图

（1）首先，将地址锁存器373输出的地址信号A0到A3分别接到138的A、B、C和E1口。

（2）然后，将138的E2和E3口接地，使138仅由A3来进行片选。

（3）最后，将138的输出信号Y0作为基本输入接口的片选信号，Y4作为基本输出接口的片选信号。

![](https://github.com/niwanli/Proteus/raw/master/pictures/0602.jpg "")

## 6.4  输入缓冲模块

### 6.4.1  输入缓冲模块设计思路

由于系统总线上连接的存储器和外设端口较多，而CPU引脚的驱动能力较弱，通常需要在数据总线上连接数据总线收发器，增强总线驱动能力。由于数据总线的传送方向是双向的，所以常常使用双向总线驱动器74LS245。

本次实验中，使用8位三态缓冲器74LS245作为基本输入接口，将8位开关的状态读取并传输给CPU。虽然245可以实现数据的双向传输，但本次实验中只把245当成是一个单向的三态缓冲器来使用。

### 6.4.2  输入缓冲模块Proteus制图

（1）首先，将245的B0到B7接到8位开关上。

（2）然后，将245的A0到A7接到CPU的数据总线AD0到AD7上。

（3）接着，将CPU的M/IO信号、RD信号和138的Y0信号作为245的片选信号，经过两个或门后，接到245的CE口。

（4）最后，将245的AB/BA口接地，使245始终处于输入状态。

![](https://github.com/niwanli/Proteus/raw/master/pictures/0603.jpg "")

## 6.5  输出锁存模块

### 6.5.1  输出锁存模块设计思路

CPU通过总线送到外设的数据后，命令一般需要经锁存器进行锁存，以便外设有足够的时间进行接收和处理。CPU在进行输出操作时，M/IO为低电平，WR为低电平，地址线A3-A0发出所选I/O端口地址，并经译码器138输出Y4信号（低电平）。它们经或门后，在74LS245的CE段产生一个负脉冲，将CPU在数据线上输出的数据打入锁存器245中，这个锁存数据立即从B7-B0端输出，点亮或熄灭8个发光二极管。

### 6.5.2  输出锁存模块Proteus制图

（1）首先，将245的B0到B7接到8个LED灯上。

（2）然后，将245的A0到A7接到CPU的数据总线AD0到AD7上。

（3）接着，将CPU的M/IO信号、WR信号和138的Y4信号作为245的片选信号，进过两个与门后，接到245的CE口。

（4）最后，将245的AB/BA口高电平（+5V），使245始终处于输出状态。

![](https://github.com/niwanli/Proteus/raw/master/pictures/0604.jpg "")

## 6.6  代码设计

本实验通过读取开关状态来控制LED的闪烁与否，流程图如图5-5所示。根据流程图编写相应的控制代码如附录二所示。

![](https://github.com/niwanli/Proteus/raw/master/pictures/0605.jpg "")
　　
# 第7章  系统调试

## 7.1  仿真调试

在原理图绘制界面将电路设计完成之后，再将汇编语言源程序写入源代码界面，然后我们就可以点击“运行”按钮进行仿真了。这时，我们发现Proteus软件报错（红色部分），错误信息内容如下：

> Invalid internal memory size == NULL ( Cheat mode)

> Real Time Simulation failed to start.

![](https://github.com/niwanli/Proteus/raw/master/pictures/0701.jpg "")

错误信息提示说，“内存大小无效”、“实时仿真无法启动”。现在回到源代码界面，注释信息里有这样一句话：

> Before starting simulation set Internal Memory Size in the 8086 model properties to 0x10000

![](https://github.com/niwanli/Proteus/raw/master/pictures/0702.jpg "")

翻译过来就是：

> 在开始仿真之前，将8086模型属性中的内部内存大小设置为0x10000

然后我们就去设置8086的内存大小吧，设置方法如下：


（1）在原理图绘制界面，鼠标双击8086处理器，弹出 “编辑元件”窗口。

![](https://github.com/niwanli/Proteus/raw/master/pictures/0703.jpg "")

（2）在“编辑元件”窗口，点击下拉菜单，选择Internal Memory Size，然后将其值设为0x10000，最后单击“确认”按钮即可。

![](https://github.com/niwanli/Proteus/raw/master/pictures/0704.jpg "")
　　
现在，我们再单击“运行”按钮，得到如图7-5所示结果，电路运行正常。然后，我们通过单击开关，来回切换开关状态，观察发光二极管的变化，即：某开关闭合，则点亮与该开关对应的发光二极管，如图7-6所示。

![](https://github.com/niwanli/Proteus/raw/master/pictures/0705.jpg "")

![](https://github.com/niwanli/Proteus/raw/master/pictures/0706.jpg "")

## 7.2  单步调试

在源程序调试窗口，单击“单步运行”按钮。选择菜单“调试”下的“Register”选项，然后就可以从打开的寄存器窗口中看到执行到断点处的寄存器的值。

![](https://github.com/niwanli/Proteus/raw/master/pictures/0707.jpg "")
　　
在“调试”菜单下有一系列的调试键，但是多数时候用F11键来单步运行程序。按一次F11键，左边的红色箭头下将移到下一条指令。通过观察寄存器窗口的寄存器的变化，来监测指令的运行情况。

![](https://github.com/niwanli/Proteus/raw/master/pictures/0708.jpg "")
　　
# 附录一  Proteus完整制图

![](https://github.com/niwanli/Proteus/raw/master/pictures/0801.jpg "")

![](https://github.com/niwanli/Proteus/raw/master/pictures/0802.jpg "")

# 附录二  汇编语言源程序

```
CODE    SEGMENT PUBLIC 'CODE'
        ASSUME CS:CODE

START:
        MOV  DX,0008H
        IN   AL,DX
        MOV  DX,000CH
        OUT  DX,AL
        JMP  START
CODE    ENDS
        END START
```
