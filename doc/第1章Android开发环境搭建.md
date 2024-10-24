# 第 1 章　Android开发环境搭建 

本章介绍了如何在个人电脑上搭建Android开发环境，主要包括：Android开发的发展历史是怎样的、 

Android Studio的开发环境是如何搭建的、如何创建并编译App工程、如何运行和调试App。 

## 1.1 Android开发简介 

本节介绍Android开发的历史沿革，包括Android的发展历程和Android Studio的发展历程两个方面。 

## 1.1.1 Android的发展历程 

安卓（Android）是一种基于Linux内核（不包含GNU组件）的自由及开放源代码的操作系统。主要使用 

于移动设备，如智能手机和平板电脑，由美国Google公司和开放手机联盟领导及开发。Android操作系 

统最初由Andy Rubin开发，主要支持手机。 

- 2005 年 8 月由Google收购注资。 

- 2007 年 11 月，Google与 84 家硬件制造商、软件开发商及电信营运商组建开放手机联盟共同研发改

   良Android系统，并发布了Android的源代码。 

- 第一部Android智能手机发布于 2008 年 10 月，由 HTC 公司制造。Android逐渐扩展到平板电脑及其他领域上，如电视、数码相机、游戏机、智能手表、车载大屏、智能家居等，并逐渐成为了人们 日常生活中不可或缺的系统软件。 

- 2011 年第一季度，Android在全球的市场份额首次超过塞班系统，跃居全球第一。 

- 2013 年的第四季度，Android平台手机的全球市场份额已经达到78.1%。 2013 年 09 月 24 日谷歌开 发的操作系统Android在迎来了 5 岁生日，全世界采用这款系统的设备数量已经达到 10 亿台。 

- 2019 年，谷歌官方宣布全世界有 25 亿活跃的Android设备，还不包含大多数中国设备。 

Android几乎每年都要发布一个大版本，技术的更新迭代非常之快，表1-1展示了Android几个主要版本的发布时间。 

---

表1-2 Android Studio主要版本的发布时间 

| Android版本号 | 对应 API | 发布时间   |
| ------------- | -------- | ---------- |
| Android 13    | 33       | 2022年2月  |
| Android 12    | 31       | 2021年10月 |
| Android 11    | 30       | 2020年9月  |
| Android 10    | 29       | 2019年8月  |
| Android 9     | 28       | 2018年8月  |
| Android 8     | 26/27    | 2017年8月  |
| Android 7     | 24/25    | 2016年8月  |
| Android 6     | 23       | 2015年9月  |
| Android 5     | 21/22    | 2014年6月  |
| Android 4.4   | 19/20    | 2013年9月  |



### 1.1.2 Android Studio的发展历程 

虽然Android基于Linux内核，但是Android手机的应用App主要采用Java语言开发。为了吸引众多的Java程序员，早期的App开发工具使用Eclipse，通过给Eclipse安装ADT插件，使之支持开发和调试App。然而Eclipse毕竟不是专门的App开发环境，运行速度也偏慢，因此谷歌公司在 2013 年 5 月推出了全新的 Android开发环境—Android Studio。Android Studio基于IntelliJ IDEA演变而来，既保持了IDEA方便快捷的特点，又增加了Android开发的环境支持。自 2015 年之后，谷歌公司便停止了ADT的版本更新，转而重点打造自家的Android Studio，数年升级换代下来，Android Studio的功能愈加丰富，性能也愈高效，使得它逐步成为主流的App开发环境。表1-2展示了、几个主要版本的发布时间。 

## 1.2　搭建Android Studio开发环境 

本节介绍在电脑上搭建Android Studio开发环境的过程和步骤，首先说明用作开发机的电脑应当具备哪些基本配置，接着描述了Android Studio的安装和配置详细过程，然后叙述了如何下载Android开发需要的SDK组件及相关工具。 

### 1.2.1　开发机配置要求 

工欲善其事，必先利其器。要想保证Android Studio的运行速度，开发用的电脑配置就要跟上。现在一般用笔记本电脑开发App，下面是对电脑硬件的基本要求： 

（ 1 ）内存要求至少8GB，越大越好。 

（ 2 ）CPU要求1.5GHz以上，越快越好。 

（ 3 ）硬盘要求系统盘剩余空间10GB以上，越大越好。 

（ 4 ）要求带无线网卡与USB插槽。 

下面是对操作系统的基本要求（以Windows为例）。 

（ 1 ）必须是 64 位系统，不能是 32 位系统。 

（ 2 ）Windows系统至少为Windows 7，推荐Windows 10，不支持Windows XP。 

下面是对网络的基本要求： 

（ 1 ）最好连接公众网，因为校园网可能无法访问国外的网站。 

（ 2 ）下载速度至少每秒1MB，越快越好。因为Android Studio安装包大小为1GB左右，还需要另外下载几百MB的SDK，所以网络带宽一定要够大，否则下载文件都要等很久。 

### 1.2.2　安装Android Studio 

Android Studio的官方下载页面是https://developer.android.google.cn/studio/index.html，单击网页中央的DOWNLOAD按钮即可下载Android Studio的安装包。或者下拉网页找到“Android Studio downloads”区域，选择指定操作系统对应的Android Studio安装包。 

双击下载完成的Android Studio安装程序。

### 1.2.3　下载Android的SDK 

Android Studio只提供了App的开发环境界面，编译App源码还需另外下载Android官方的SDK，上一小 

节中的图1-10便展示了初始下载安装的SDK工具包。SDK全称为Software Development Kit，意即软件 

开发工具包，它可将App源码编译为可执行的App应用。随着Android版本的更新换代，SDK也需时常在 

线升级，接下来介绍如何下载最新的SDK。 

在Android Studio主界面，依次选择菜单Tools→SDK Manager，或者在Android Studio右上角中单击 

图标，如图1-14所示。

![](https://gitee.com/xiaweifeng/picgo/raw/master/images/ImageFrom笔记-Android 开发从入门到实战.png) 

此时弹出SDK Manager的管理界面，窗口右边是SDK安装配置区域，初始画面如图1-15所示。注意 

Android SDK Location一栏，可单击右侧的Edit链接，进而选择SDK下载后的保存路径。其下的三个选 

项卡默认显示SDK Platforms，也就是各个SDK平台的版本列表，勾选每个列表项左边的复选框，表示需 

要下载该版本的SDK平台，然后单击OK按钮即可自动下载并安装SDK。也可单击中间SDK Tools选项 

---

图1-15 SDK平台的管理列表 

![](https://gitee.com/xiaweifeng/picgo/raw/master/images/ImageFrom笔记-Android 开发从入门到实战12.png)

图1-16 SDK工具的管理列表 

![](https://gitee.com/xiaweifeng/picgo/raw/master/images/Image From 笔记-Android 开发从入门到实战232.png)

卡，此时会切换到SDK工具的管理列表，如图1-16所示。在这个工具管理界面，能够在线升级编译工具 

Build Tools、平台工具Platform Tools，以及开发者需要的其他工具。 

SDK下载完成，可以到“我的电脑”中打开Android SDK Location指定的SDK保存路径，发现下面还有十几 

个目录，其中比较重要的几个目录说明如下： 

build-tools目录，存放各版本Android的编译工具。 

emulator目录，存放模拟器的管理工具。 

platforms目录，存放各版本Android的资源文件与内核JAR包android.jar。 

platform-tools目录，存放常用的开发辅助工具，包括客户端驱动程序adb.exe、数据库管理工具 

sqlite3.exe，等等。 

sources目录，存放各版本Android的SDK源码。 

## 1.3　创建并编译App工程 

本节介绍使用Android Studio创建并编译App工程的过程和步骤，首先叙述了如何通过Android Studio 

创建新的App项目，接着描述了如何导入已有的App工程（包括导入项目和导入模块两种方式），然后 

阐述了如何手工编译App工程。 

### 1.3.1 创建新项目 

在“1.2.2　安装Android Studio”小节最后一步出来的图1-13中，单击第一项的Start a new Android 

Studio project会创建初始的新项目。如果要创建另外的新项目，也可在打开Android Studio之后，依次 

选择菜单File→New→New Project。以上两种创建方式都会弹出如图1-17所示的项目创建对话框，在该 

对话框中选择第一行第四列的“Empty Activity”，单击Next按钮跳到下一个配置对话框如图1-18所示。 

---

图1-18　指定目标设备 

图1-19　刚刚创建的新项目页面 

在配置对话框的Name栏输入应用名称，在Package Name栏输入应用的包名，在Save Location栏输入 

或者选择项目工程的保存目录，在Language下拉框中选择编码语言为Java，在Minimun SDK下拉框中 

选择最低支持到“API19:Android 4.4(KitKat)”，Minimun SDK下方的文字提示当前版本支持设备的市场 

份额为98.1%。下面有个复选框“User legacy android.support libraries”，如果勾选表示采用旧的 

support支持库，如果不勾选表示采用新的androidx库，因为Android官方不再更新旧的support库，所 

以此处无须勾选，默认采用新的androidx库就可以了。 

然后单击Finish按钮完成配置操作，Android Studio便自动创建规定配置的新项目了。稍等片刻， 

Android Studio将呈现刚创建好的项目页面，如图1-19所示。 

![Image From 笔记-Android 开发从入门到实战](https://gitee.com/xiaweifeng/picgo/raw/master/images/202207032103036.png)

工程创建完毕后，Android Studio自动打开activity_main.xml与MainActivity.java，并默认展示 

MainActivity.java的源码。MainActivity.java上方的标签表示该文件的路径结构，注意源码左侧有一列标 

签，从上到下依次是Project、Resource Manager、Structure、Build Variants、Favorites。单击 

Project标签，左侧会展开小窗口表示该项目工程的目录结构，如图1-20所示。单击Structure标签，左 

侧会展开小窗口表示该代码的内部方法结构。 

### 1.3.2　导入已有的工程 

本书提供了所有章节的示例源码，为方便学习，读者可将本书源码直接导入Android Studio。根据App 

工程的组织形式，有两种源码导入方式，分别是导入整个项目，以及导入某个模块，简要说明如下。 

1 ．导入整个项目 

以本书源码MyApp为例，依次选择菜单File→Open，或者依次选择菜单File→New→Import Project，

在文件对话框中选中待导入的项目路径，再单击对话框下方的OK按钮。此时文件对话框关闭，弹出另一

确认对话框右下角有 3 个按钮，分别是This Window、New Window和Cancel，其中This Window按钮 

表 

示在当前窗口打开该项目，New Window按钮表示在新窗口打开该项目，Cancel按钮表示取消打开操 

作。此处建议单击New Window按钮，即可在新窗口打开App项目。 

2 ．导入某个模块 

如果读者已经创建了自己的项目，想在当前项目导入某章的源码，应当通过Module方式导入模块源码。 

依次选择菜单File→New→Import Module，弹出如图1-24所示的导入对话框。 

单击Source Directory输入框右侧的文件夹图标，在文件对话框中选择待导入的模块路径，再单击对话框下方的OK按钮，可见导入对话框已经自动填上了待导入模块的完整路径，单击对话框右下角的Finish按钮完成导入操 

作。然后Android Studio自动开始模块的导入和编译动作，等待导入结束即可在Android Studio左上角 

的项目结构图中看到导入的chapter02模块。

### 1.3.3　编译App工程 

Android Studio跟IDEA一样，被改动的文件会自动保存，无须开发者手工保存。它还会自动编译最新的 

代码，如果代码有误，编辑界面会标红提示出错了。但是有时候可能因为异常关闭的缘故，造成 

Android Studio的编译文件发生损坏，此时需要开发者手动重新编译，手动编译有以下 3 种途径： 

（ 1 ）依次选择菜单Build→Make Project，该方式会编译整个项目下的所有模块。 

（ 2 ）依次选择菜单Build→Make Module ***，该方式会编译指定名称的模块。 

（ 3 ）先选择菜单Build→Clean Project，再选择菜单Build→Rebuild Project，表示先清理当前项目，再 

对整个项目重新编译。 

不管是编译项目还是编译模块，编译结果都展示在Android Studio主界面下方的Build窗口中，如图1-28 

所示。 

由编译结果可知，当前项目编译耗时 2 分 29 秒，共发现了 1 个警告，未发现错误。 

## 1.4 运行和调试App 

---

图1-29　打开AVD Manager的图标栏 

图1-30　模拟器的创建窗口 

本节介绍使用Android Studio运行和调试App的过程，首先叙述了如何创建Android Studio内置的模拟 

器，接着描述了如何在刚创建的模拟器上运行测试App，然后阐述了如何在Android Studio中查看App 

的运行日志。 

### 1.4.1 创建内置模拟器 

所谓模拟器，指的是在电脑上构造一个演示窗口，模拟手机屏幕的App运行效果。App通过编译之后， 

只说明代码没有语法错误，若想验证App能否正确运行，还得让它在Android设备上跑起来。这个设备可 

以是真实手机，也可以是电脑里的模拟器。依次选择菜单Run→Run （也可按快捷键Shift+F10），或者 

选择菜单Run→Run...，在弹出的小窗中选择待运行的模块名称，Android Studio会判断当前是否存在已 

经连接的设备，如果已有连接上的设备就在该设备上安装测试App。 

因为一开始没有任何已连上的设备，所以运行App会报错“Error running ：No target device found.”， 

意思是未找到任何目标设备。此时要先创建一个模拟器，依次选择菜单Tools→AVD Manager，或者在 

Android Studio右上角的按钮中单击图标，如图1-29所示。 

此时Android Studio打开模拟器的创建窗口，如图1-30所示。 

单击创建窗口中的Create Virtual Device按钮，弹出如图1-31所示的硬件选择对话框。 

---

图1-31　硬件选择对话框 

图1-32　系统镜像选择对话框 

在对话框的左边列表单击Phone表示选择手机，在中间列表选择某个手机型号如Pixel 2，然后单击对话 

框右下角的Next按钮，跳到下一页的系统镜像选择对话框如图1-32所示。 

看到镜像列表顶端的发布名称叫R，对应的API级别为 30 ，它正是Android 11的系统镜像。单击R右边的 

Download链接，弹出如图1-33所示的许可授权对话框。 

---

图1-33　许可授权对话框 

图1-34　镜像下载对话框 

单击许可授权对话框的Accept选项，表示接受上述条款，再单击Next按钮跳到下一页的镜像下载对话 

框，如图1-34所示。 

等待镜像下载完成，单击右下角的Finish按钮，返回到如图1-35所示的系统镜像选择对话框。 

此时R右边的Download链接消失，说明电脑中已经存在该版本的Android镜像。于是选中R这行，再单 

击Next按钮，跳到模拟器的配置对话框如图1-36所示。 

---

图1-35　系统镜像选择对话框 

图1-36　模拟器的配置对话框 

配置对话框左上方的AVD Name用于填写模拟器的名称，这里保持默认名称不动，单击对话框右下角的 

Finish按钮完成创建操作。一会儿对话框关闭，回到如图1-37所示的模拟器列表对话框，可见多了个名 

为Pixel 2 API 30的模拟器，且该模拟器基于Android 11（API 30）。 

---

图1-37　模拟器的列表对话框 

图1-38　顶部工具栏出现刚创建的模拟器 

图1-39　模拟器正在启动 

### 1.4.2　在模拟器上运行App 

模拟器创建完成后，回到Android Studio的主界面，即可在顶部工具栏的下拉框中发现多了个“Pixel 2 

API 30”，它正是上一小节创建好的模拟器，如图1-38所示。 

重新选择菜单Run→Run 'app'，也可直接单击“Pixel 2 API 30”右侧的三角运行按钮，Android Studio便 

开始启动名为“Pixel 2 API 30”的模拟器，如图1-39所示。等待模拟器启动完毕，出现模拟器的开机画面 

如图1-40所示。再过一会儿，模拟器自动打开如图1-41所示的App界面。 

---

图1-40　模拟器的开机画面 

---

图1-41　模拟器运行App 

可见模拟器屏幕左上角的应用名称为MyApp，页面内容为Hello World！它正是刚才想要运行的测试 

App，说明已经在模拟器上成功运行App了。 

### 1.4.3　观察App的运行日志 

虽然在模拟器上能够看到App的运行，却无法看到App的调试信息。以前写Java代码的时候，通过 

System.out.println可以很方便地向IDEA的控制台输出日志，当然Android Studio也允许查看App的运 

行日志，只是Android不使用System.out.println，而是采用Log工具打印日志。 

有别于System.out.println，Log工具将各类日志划分为 5 个等级，每个等级的重要性是不一样的，这些 

日志等级按照从高到低的顺序依次说明如下： 

Log.e：表示错误信息，比如可能导致程序崩溃的异常。 

Log.w：表示警告信息。 

Log.i：表示一般消息。 

Log.d：表示调试信息，可把程序运行时的变量值打印出来，方便跟踪调试。 

Log.v：表示冗余信息。 

一般而言，日常开发使用Log.d即可，下面是给App添加日志信息的代码例子： 

（完整代码见app\src\main\java\com\example\app\MainActivity.java）

## 1.5 小结 

​		本章主要介绍了Android开发环境的搭建过程，包括：Android开发简介（Android的发展历程、 

  Android Studio的发展历程）、搭建Android Studio开发环境（开发机配置要求、安装Android 

  Studio、下载Android的SDK）、创建并编译App工程（创建新项目、导入已有的工程、编译App工 

  程）、运行和调试App（创建内置模拟器、在模拟器上运行App、观察App的运行日志）。 

  通过本章的学习，读者应该掌握Android Studio的基本操作技能，能够使用自己搭建的Android Studio 

  环境创建简单的App工程，并在模拟器上成功运行测试App。 