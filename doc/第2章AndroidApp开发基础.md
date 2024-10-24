# 第 2 章　Android App开发基础 

本章介绍基于Android系统的App开发常识，包括以下几个方面：App开发与其他软件开发有什么不一 

样，App工程是怎样的组织结构又是怎样配置的，App开发的前后端分离设计是如何运作实现的，App的 

活动页面是如何创建又是如何跳转的。 

## 2.1 App的开发特点 

本节介绍了App开发与其他软件开发不一样的特点，例如：App能在哪些操作系统上运行、App开发用到 

了哪些编程语言、App能操作哪些数据库等，搞清楚了App的开发运行环境，才能有的放矢不走弯路。 

---

### 2.1.1 App的运行环境 

App是在手机上运行的一类应用软件，而应用软件依附于操作系统，无论电脑还是手机，刚开机都会显 

示桌面，这个桌面便是操作系统的工作台。个人电脑的操作系统主要有微软的Windows和苹果的Mac 

OS，智能手机流行的操作系统也有两种，分别是安卓手机的Android和苹果手机的iOS。本书讲述的App 

开发为Android上的应用开发，Android系统基于Linux内核，但不等于Linux系统，故App应用无法在 

Linux系统上运行。 

Android Studio是谷歌官方推出的App开发环境，它提供了三种操作系统的安装包，分别是Windows、 

Mac和Linux。这就产生一个问题：开发者可以在电脑上安装Android Studio，并使用Android Studio开 

发App项目，但是编译出来的App在电脑上跑不起来。这种情况真是令人匪夷所思的，通常学习C语言、 

Java或者Python，都能在电脑的开发环境直接观看程序运行过程，就算是J2EE开发，也能在浏览器通过 

网页观察程序的运行结果。可是安卓的App应用竟然没法在电脑上直接运行，那该怎样验证App的界面 

展示及其业务逻辑是否正确呢？ 

为了提供App开发的功能测试环境，一种办法是利用Android Studio创建内置的模拟器，然后启动内置 

模拟器，再在模拟器上运行App应用，详细步骤参见第一章的“1.4.2　在模拟器上运行App”。 

另一种办法是使用真实手机测试App，该办法在实际开发中更为常见。由于模拟器本身跑在电脑上面， 

占用电脑的CPU和内存，会拖累电脑的运行速度；况且模拟器仅仅是模拟而已，无法完全验证App的所 

有功能，因此最终都得通过真机测试才行。 

利用真机调试要求具备以下 5 个条件： 

1 ．使用数据线把手机连到电脑上 

手机的电源线拔掉插头就是数据线。数据线长方形的一端接到电脑的USB接口，即可完成手机与电脑的 

连接。 

2 ．在电脑上安装手机的驱动程序 

一般电脑会把手机当作USB存储设备一样安装驱动，大多数情况会自动安装成功。如果遇到少数情况安 

装失败，需要先安装手机助手，由助手软件下载并安装对应的手机驱动。 

3 ．打开手机的开发者选项并启用USB调试 

手机出厂后默认关闭开发者选项，需要开启开发者选项才能调试App。打开手机的设置菜单，进入“系统” 

→“关于手机”→“版本信息”页面，这里有好几个版本项，每个版本项都使劲点击七、八下，总会有某个版 

本点击后出现“你将开启开发者模式”的提示。继续点击该版本开启开发者模式，然后退出并重新进入设 

置页面，此时就能在“系统”菜单下找到“开发者选项”或“开发人员选项”了。进入“开发者选项”页面，启用 

“开发者选项”和“USB调试”两处开关，允许手机通过USB接口安装调试应用。 

4 ．将连接的手机设为文件传输模式，并允许计算机进行USB调试 

手机通过USB数据线连接电脑后，屏幕弹出如图2-1所示的选择列表，请求选择某种USB连接方式。这里 

记得选中“传输文件”，因为充电模式不支持调试App。 

选完之后手机桌面弹出如图2-2所示的确认窗口，提示开发者是否允许当前计算机进行USB调试。这里勾 

选“始终允许使用这台计算机进行调试”选项，再点击右下角的确定按钮，允许计算机在手机上调试App。 

5 ．手机要能正常使用 

锁屏状态下，Android Studio向手机安装App的行为可能会被拦截，所以要保证手机处于解锁状态，才 

能顺利通过电脑安装App到手机上。 

有的手机还要求插入SIM卡才能调试App，还有的手机要求登录会员才能调试App，总之如果遇到无法安 

装的问题，各种情况都尝试一遍才好。 

经过以上步骤，总算具备通过电脑在手机上安装App的条件了。马上启动Android Studio，在顶部中央 

的执行区域看到已连接的手机信息，如图2-3所示。此时的设备信息提示这是一台华为手机，单击手机名 

称右边的三角运行按钮，接下来就是等待Android Studio往手机上安装App了。 

### 2.1.2 App的开发语言 

基于安卓系统的App开发主要有两大技术路线，分别是原生开发和混合开发。原生开发指的是在移动平 

台上利用官方提供的编程语言（例如Java、Kotlin等）、开发工具包（SDK）、开发环境（Android 

Studio）进行App开发；混合开发指的是结合原生与H5技术开发混合应用，也就是将部分App页面改成 

内嵌的网页，这样无须升级App、只要覆盖服务器上的网页，即可动态更新App页面。 

不管是原生开发还是混合开发，都要求掌握Android Studio的开发技能，因为混合开发本质上依赖于原 

生开发，如果没有原生开发的皮，哪里还有混合开发的毛呢？单就原生开发而言，又涉及多种编程语 

言，包括Java、Kotlin、C/C++、XML等，详细说明如下。 

1 ．**Java** 

Java是Android开发的主要编程语言，在创建新项目时，看见Language栏默认选择了Java，表示该项目采用Java编码。虽然Android开发需要Java环境，但没要求电脑上必须事先安装JDK，因为Android Studio已经自带了JRE。依次选择菜单File→Project Structure，单击项目结构对话框左侧的SDK Location，对话框右边从上到下依次排列着“Android SDK location”、“Android NDK location”、“JDK location”，其中下方的JDK location提示位于Android Studio安装路径的JRE目录下，它正是Android Studio自带的Java运行环境。 

可是Android Studio自带的JRE看不出来基于Java哪个版本，它支不支持最新的Java版本呢？其实 

Android Studio自带的JRE默认采用Java 7编译，如果在代码里直接书写Java 8语句就会报错，比如Java 8 

引入了Lambda表达式，下面代码通过Lambda表达式给整型数组排序： 

倘若由Android Studio编译上面代码，结果提示出错“Lambda expressions are not supported at 

language level '7'”，意思是Java 7不支持Lambda表达式， 原来Android Studio果真默认支持Java 7而非Java 8，但Java 8增添了诸多新特性，其拥趸与日俱增，有 

的用户习惯了Java 8，能否想办法让Android Studio也支持Java 8呢？当然可以，只要略施小计便可，依 

次选择菜单File→Project Structure，在弹出的项目结构对话框左侧单击Modules，此时对话框如图2-7 

所示。

![Image From 笔记-Android 开发从入门到实战](https://gitee.com/xiaweifeng/picgo/raw/master/images/202207032123567.png)

 2 ．**Kotlin** 

  Kotlin是谷歌官方力推的又一种编程语言，它与Java同样基于JVM（Java Virtual Machine，即Java虚拟 

  机），且完全兼容Java语言。创建新项目时，在Language栏下拉可选择Kotlin，此时项目结构对话框如

  一旦在创建新项目时选定Kotlin，该项目就会自动加载Kotlin插件，并将Kotlin作为默认的编程语言。不 

  过本书讲述的App开发采用Java编程，未涉及Kotlin编程。 

 3 ．**C/C++** 

  不管是Java还是Kotlin，它们都属于解释型语言，这类语言在运行之时才将程序翻译成机器语言，故而执 

  行效率偏低。虽然现在手机配置越来越高，大多数场景的App运行都很流畅，但是涉及图像与音视频处 

  理等复杂运算的场合，解释型语言的性能瓶颈便暴露出来。 

  编译型语言在首次编译时就将代码编译为机器语言，后续运行无须重新编译，直接使用之前的编译文件 

  即可，因此执行效率比解释型语言高。C/C++正是编译型语言的代表，它能够有效弥补解释型语言的性 

  能缺憾，借助于JNI技术（Java Native Interface，即Java原生接口），Java代码允许调用C/C++编写的程 

  序。事实上，Android的SDK开发包内部定义了许多JNI接口，包括图像读写在内的底层代码均由 

  C/C++编写，再由外部通过封装好的Java方法调用。 

  不过Android系统的JNI编程属于高级开发内容，初学者无须关注JNI开发，也不要求掌握C/C++。 

  4 ．**XML** 

  XML全称为Extensible Markup Language，即可扩展标记语言，严格地说，XML并非编程语言，只是一 

  种标记语言。它类似于HTML，利用各种标签表达页面元素，以及各元素之间的层级关系及其排列组 

  合。每个XML标签都是独立的控件对象，标签内部的属性以“android:”打头，表示这是标准的安卓属 

  性，各属性分别代表控件的某种规格。比如下面是以XML书写的文本控件： 

  上面的标签名称为TextView，翻译过来叫文本视图，该标签携带 4 个属性，说明如下： 

 ```xml
 <TextView android:id="@+id/tv_hello" 
           android:layout_width="wrap_content" 
           android:layout_height="wrap_content" 
           android:text="Hello World!" /> 
 ```

-  id：控件的编号。 

- layout_width：控件的布局宽度，wrap_content表示刚好包住该控件的内容。 

- layout_height：控件的布局高度，wrap_content表示刚好包住该控件的内容。 

- text：控件的文本，也就是文本视图要显示什么文字。 

  综合起来，以上XML代码所表达的意思为：这是一个名为tv_hello的文本视图，显示的文字内容是“Hello 

  World!”，它的宽度和高度都要刚好包住这些文字。 

  以上就是Android开发常见的几种编程语言，本书选择了Java路线而非Kotlin路线，并且定位安卓初学者 

  教程，因此读者需要具备Java和XML基础。 

### 2.1.3 App连接的数据库 

  在学习Java编程的时候，基本会学到数据库操作，通过JDBC连接数据库进行记录的增删改查，这个数据 

  库可能是MySQL，也可能是Oracle，还可能是SQL Server。然而手机应用不能直接操作上述几种数据 

  库，因为数据库软件也得像应用软件那样安装到操作系统上，比如MySQL提供了Windows系统的安装 

  包，也提供了Linux系统的安装包，可是它没有提供Android系统的安装包呢，所以MySQL没法在 

  Android系统上安装，手机里面的App也就不能直连MySQL。 

  既然MySQL、Oracle这些企业数据库无法在手机安装，那么App怎样管理业务方面的数据记录呢？其实 

  Android早已内置了专门的数据库名为SQLite，它遵循关系数据库的设计理念，SQL语法类似于 

  MySQL。不同之处在于，SQLite无须单独安装，因为它内嵌到应用进程当中，所以App无须配置连接信 

  息，即可直接对其增删改查。由于SQLite嵌入到应用程序，省去了配置数据库服务器的开销，因此它又 

  被归类为嵌入式数据库。 

  可是SQLite的数据库文件保存在手机上，开发者拿不到用户的手机，又该如何获取App存储的业务数 

  据？比如用户的注册信息、用户的购物记录，等等。如果像Java Web那样，业务数据统一保存在后端的 

  数据库服务器，开发者只要登录数据库服务器，就能方便地查询导出需要的记录信息。 

  手机端的App，连同程序代码及其内置的嵌入式数据库，其实是个又独立又完整的程序实体，它只负责 

  手机上的用户交互与信息处理，该实体被称作客户端。而后端的Java Web服务，包括Web代码和数据库 

  服务器，同样构成另一个单独运行的程序实体，它只负责后台的业务逻辑与数据库操作，该实体被称作 

  服务端。客户端与服务端之前通过HTTP接口通信，每当客户端觉得需要把信息发给服务端，或者需要从 

  服务端获取信息时，客户端便向服务端发起HTTP请求，服务端收到客户端的请求之后，根据规则完成数 

  据处理，并将处理结果返回给客户端。这样客户端经由HTTP接口并借服务端之手，方能间接读写后端的 

  数据库服务器（如MySQL）。 

  由此看来，一个具备用户管理功能的App系统，实际上并不单单只是手机上的一个应用，还包括与其对 

  应的Java Web服务。手机里的客户端App，面向的是手机用户，App与用户之间通过手机屏幕交互；而 

  后端的服务程序，面向的是手机App，客户端与服务端之间通过HTTP接口交互。客户端和服务端这种多 

  对一的架构关系如图2-11所示。 

  总结一下，手机App能够直接操作内置的SQLite数据库，但不能直接操作MySQL这种企业数据库。必须 

  事先搭建好服务端程序（如Java Web），然后客户端与服务端通过HTTP接口通信，再由服务端操作以 

  MySQL为代表的数据库服务器。 

## 2.2 App的工程结构 

  本节介绍App工程的基本结构及其常用配置，首先描述项目和模块的区别，以及工程内部各目录与配置文件的用途说明；其次阐述两种级别的编译配置文件build.gradle，以及它们内部的配置信息说明；再次讲述运行配置文件AndroidManifest.xml的节点信息及其属性说明。 

### 2.2.1 App工程目录结构 

  App工程分为两个层次，第一个层次是项目，依次选择菜单File→New→New Project即可创建新项目。另一个层次是模块，模块依附于项目，每个项目至少有一个模块，也能拥有多个模块，依次选择菜单 File→New→New Module即可在当前项目创建新模块。一般所言的“编译运行App”，指的是运行某个模块，而非运行某个项目，因为模块才对应实际的App。单击Android Studio左上角竖排的Project标签， 

  可见App工程的项目结构如图2-12所示。 

![Image From 笔记-Android 开发从入门到实战](https://gitee.com/xiaweifeng/picgo/raw/master/images/202207032146003.png)

  图2-12 App工程的项目结构图 

  从图2-12中看到，该项目下面有两个分类：一个是app（代表app模块）；另一个是Gradle Scripts。其 

  中，app下面又有 3 个子目录，其功能说明如下： 

  （ 1 ）manifests子目录，下面只有一个XML文件，即AndroidManifest.xml，它是App的运行配置文 

  件。 

  （ 2 ）java子目录，下面有 3 个com.example.myapp包，其中第一个包存放当前模块的Java源代码，后 

  面两个包存放测试用的Java代码。 

  （ 3 ）res子目录，存放当前模块的资源文件。res下面又有 4 个子目录： 

-  drawable目录存放图形描述文件与图片文件。 

- layout目录存放App页面的布局文件。 

- mipmap目录存放App的启动图标。 

- values目录存放一些常量定义文件，例如字符串常量strings.xml、像素常量dimens.xml、颜色常量colors.xml、样式风格定义styles.xml等。 

  Gradle Scripts下面主要是工程的编译配置文件，主要有： 

  （ 1 ）build.gradle，该文件分为项目级与模块级两种，用于描述App工程的编译规则。 

  （ 2 ）proguard-rules.pro，该文件用于描述Java代码的混淆规则。 

  （ 3 ）gradle.properties，该文件用于配置编译工程的命令行参数，一般无须改动。 

  （ 4 ）settings.gradle，该文件配置了需要编译哪些模块。初始内容为include ':app'，表示只编译app模 

  块。 

  （ 5 ）local.properties，项目的本地配置文件，它在工程编译时自动生成，用于描述开发者电脑的环境 

  配置，包括SDK的本地路径、NDK的本地路径等。 

---

### 2.2.2　编译配置文件build.gradle 

  新创建的App项目默认有两个build.gradle，一个是Project项目级别的build.gradle；另一个是Module 

  模块级别的build.gradle。 

  项目级别的build.gradle指定了当前项目的总体编译规则，打开该文件在buildscript下面找到 

  repositories和dependencies两个节点，其中repositories节点用于设置Android Studio插件的网络仓 

  库地址，而dependencies节点用于设置gradle插件的版本号。由于官方的谷歌仓库位于国外，下载速度 

  相对较慢，因此可在repositories节点添加阿里云的仓库地址，方便国内开发者下载相关插件。修改之后 

  的buildscript节点内容如下所示： 

```groovy
buildscript {
   repositories {
       // 以下四行添加阿里云的仓库地址，方便国内开发者下载相关插件
       maven { url 'https://maven.aliyun.com/repository/jcenter' }
       maven { url 'https://maven.aliyun.com/repository/google'}
       maven { url 'https://maven.aliyun.com/repository/gradle-plugin'}
       maven { url 'https://maven.aliyun.com/repository/public'}
       google()
       jcenter()
 }
   dependencies {
       // 配置gradle插件版本，下面的版本号就是Android Studio的版本号
       classpath 'com.android.tools.build:gradle:4.1.0'
 } 
}
```

  模块级别的build.gradle对应于具体模块，每个模块都有自己的build.gradle，它指定了当前模块的详细 

  编译规则。下面给chapter02模块的build.gradle补充文字注释，方便读者更好地理解每个参数的用途。 

  （完整代码见chapter02\build.gradle） 

```groovy
android {
   // 指定编译用的SDK版本号。比如30表示使用Android 11.0编译 
   compileSdkVersion 30
   // 指定编译工具的版本号。这里的头两位数字必须与compileSdkVersion保持一致，具体的版本号可 
在sdk安装目录的“sdk\build-tools”下找到
   buildToolsVersion "30.0.3"
   defaultConfig {
       // 指定该模块的应用编号，也就是App的包名
       applicationId "com.example.chapter02"
       // 指定App适合运行的最小SDK版本号。比如19表示至少要在Android 4.4上运行
       minSdkVersion 19
       // 指定目标设备的SDK版本号。表示App最希望在哪个版本的Android上运行
       targetSdkVersion 30
       // 指定App的应用版本号
       versionCode 1
       // 指定App的应用版本名称
       versionName "1.0"
       testInstrumentationRunner "androidx.test.runner.AndroidJUnitRunner"
 }
   buildTypes {
       release {
           minifyEnabled false
           proguardFiles getDefaultProguardFile('proguard-android- 
optimize.txt'), 'proguard-rules.pro'
    } 
 } 
}
// 指定App编译的依赖信息 
dependencies {
   // 指定引用jar包的路径
   implementation fileTree(dir: 'libs', include: ['*.jar'])
   // 指定编译Android的高版本支持库。如AppCompatActivity必须指定编译appcompat库 
   //appcompat库各版本见
https://mvnrepository.com/artifact/androidx.appcompat/appcompat 
   implementation 'androidx.appcompat:appcompat:1.2.0'
   // 指定单元测试编译用的junit版本号
   testImplementation 'junit:junit:4.13'
   androidTestImplementation 'androidx.test.ext:junit:1.1.2'
   androidTestImplementation 'androidx.test.espresso:espresso-core:3.3.0' 
}
```

  为啥这两种编译配置文件的扩展名都是Gradle呢？这是因为它们采用了Gradle工具完成编译构建操作。 

  Gradle工具的版本配置在gradle\wrapper\gradle-wrapper.properties，也可以依次选择菜单 

  File→Project Structure→Project，在弹出的设置页面中修改Gradle Version。注意每个版本的Android 

  Studio都有对应的Gradle版本，只有二者的版本正确对应，App工程才能成功编译。比如Android 

  Studio 4.1对应的Gradle版本为6.5，更多的版本对应关系见https://developer.android.google.cn/studi 

  o/releases/gradle-plugin#updating-plugin。 

### 2.2.3　运行配置文件AndroidManifest.xml 

  AndroidManifest.xml指定了App的运行配置信息，它是一个XML描述文件，初始内容如下所示： 

  （完整代码见chapter02\src\main\AndroidManifest.xml） 

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
   package="com.example.chapter02">
   <application
       android:allowBackup="true"
       android:icon="@mipmap/ic_launcher"
       android:label="@string/app_name"
       android:roundIcon="@mipmap/ic_launcher_round"
       android:supportsRtl="true"
       android:theme="@style/AppTheme">
       <activity android:name=".Main2Activity"></activity>
       <!-- activity节点指定了该App拥有的活动页面信息，其中拥有 
android.intent.action.MAIN的activity说明它是入口页面 -->
       <activity android:name=".MainActivity"> 
           <intent-filter>
               <action android:name="android.intent.action.MAIN" />
               <category android:name="android.intent.category.LAUNCHER" /> 
           </intent-filter>
       </activity> 
   </application>
</manifest>
```

可见AndroidManifest.xml的根节点为manifest，它的package属性指定了该App的包名。manifest下 
面有个application节点，它的各属性说明如下：

- android:allowBackup，是否允许应用备份。允许用户备份系统应用和第三方应用的apk安装包和 
  应用数据，以便在刷机或者数据丢失后恢复应用，用户即可通过adb backup和adb restore来进行 
  对应用数据的备份和恢复。为true表示允许，为false则表示不允许。

- android:icon，指定App在手机屏幕上显示的图标。

- android:label，指定App在手机屏幕上显示的名称。

- android:roundIcon，指定App的圆角图标。

- android:supportsRtl，是否支持阿拉伯语／波斯语这种从右往左的文字排列顺序。为true表示支 
  持，为false则表示不支持。

- android:theme，指定App的显示风格。

注意到application下面还有个activity节点，它是活动页面的注册声明，只有在AndroidManifest.xml中 
正确配置了activity节点，才能在运行时访问对应的活动页面。初始配置的MainActivity正是App的默认 
主页，之所以说该页面是App主页，是因为它的activity节点内部还配置了以下的过滤信息：

```xml
<intent-filter>
   <action android:name="android.intent.action.MAIN" />
   <category android:name="android.intent.category.LAUNCHER" /> 
</intent-filter>
```

其中action节点设置的android.intent.action.MAIN表示该页面是App的入口页面，启动App时会最先打 
开该页面。而category节点设置的android.intent.category.LAUNCHER决定了是否在手机屏幕上显示 
App图标，如果同时有两个activity节点内部都设置了android.intent.category.LAUNCHER，那么桌面就 
会显示两个App图标。以上的两种节点规则可能一开始不太好理解，读者只需记住默认主页必须同时配 
置这两种过滤规则即可。 

## 2.3 App的设计规范 

  本节介绍了App工程的源码设计规范，首先App将看得见的界面设计与看不见的代码逻辑区分开，然后 

  利用XML标记描绘应用界面，同时使用Java代码书写程序逻辑，从而形成App前后端分离的设计规约， 

  有利于提高App集成的灵活性。 

### 2.3.1　界面设计与代码逻辑 

  手机的功能越来越强大，某种意义上相当于微型电脑，比如打开一个电商App，仿佛是在电脑上浏览网 

  站。网站分为用户看得到的网页，以及用户看不到的Web后台；App也分为用户看得到的界面，以及用 

  户看不到的App后台。虽然Android允许使用Java代码描绘界面，但不提倡这么做，推荐的做法是将界面 

  设计从Java代码剥离出来，通过单独的XML文件定义界面布局，就像网站使用HTML文件定义网页那样。 

  直观地看，把界面设计与代码逻辑分开，不仅参考了网站的Web前后端分离，还有下列几点好处。 

  （ 1 ）使用XML文件描述App界面，可以很方便地在Android Studio上预览界面效果。比如新创建的App 

  项目，默认首页布局为activity_main.xml，单击界面右上角的Design按钮，即可看到预览界面。 

  如果XML文件修改了Hello World的文字内容，立刻就能在预览区域观看最新界面。倘若使用Java代码描 

  绘界面，那么必须运行App才能看到App界面，无疑费时许多。 

  （ 2 ）一个界面布局可以被多处代码复用，比如看图界面，既能通过商城购物代码浏览商品图片，也能通 

  过商品评价代码浏览买家晒单。 

  （ 3 ）反过来，一段Java代码也可能适配多个界面布局，比如手机有竖屏与横屏两种模式，默认情况App 

  采用同一套布局，然而在竖屏时很紧凑的界面布局，切换到横屏往往变得松垮乃至变形，鉴于竖屏与横屏遵照一样的业务逻辑，仅仅是屏幕方向不同，若要调整的话，只需分别给出竖屏时候的界面布局，以及横屏时候的界面布局。因为用户多数习惯竖屏浏览，所以res/layout目录下放置的XML 

  文件默认为竖屏规格，另外在res下面新建名为layout-land的目录，用来存放横屏规格的XML文件。 

  land是landscape的缩写，意思是横向，Android把layout-land作为横屏XML的专用布局目录。然后在 

  layout-land目录创建与原XML同名的XML文件，并重新编排界面控件的展示方位，调整后的横屏界面如，从而有效适配了屏幕的水平方向。 

  总的来说，界面设计与代码逻辑分离的好处多多，后续的例程都由XML布局与Java代码两部分组成。 

---

### 2.3.2　利用XML标记描绘应用界面 

  在前面“2.1.2 App的开发语言”末尾，给出了安卓控件的XML定义例子，如下所示： 

```xml
<TextView
android:id="@+id/tv_hello"
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:text="Hello World!" />
```

  注意到TextView标签以“<”开头，以“/>”结尾，为何尾巴多了个斜杆呢？要是没有斜杆，以左右尖括号包 

  裹标签名称，岂不更好？其实这是XML的标记规范，凡是XML标签都由标签头与标签尾组成，标签头以 

  左右尖括号包裹标签名称，形如“”；标签尾在左尖括号后面插入斜杆，以此同标签头区分开，形如“”。标 

  签头允许在标签名称后面添加各种属性取值，而标签尾不允许添加任何属性，因此上述TextView标签的 

  完整XML定义是下面这样的： 

```xml
<TextView
android:id="@+id/tv_hello"
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:text="Hello World!"> 
</TextView>    
```

  考虑到TextView仅仅是个文本视图，其标签头和标签尾之间不会插入其他标记，所以合并它的标签头和 

  标签尾，也就是让TextView标签以“/>”结尾，表示该标签到此为止。 

  然而不是所有情况都能采取简化写法，简写只适用于TextView控件这种末梢节点。好比一棵大树，大树 

  先有树干，树干分岔出树枝，一些大树枝又分出小树枝，树枝再长出末端的树叶。一个界面也是先有根 

  节点（相当于树干），根节点下面挂着若干布局节点（相当于树枝），布局节点下面再挂着控件节点 

  （相当于树叶）。因为树叶已经是末梢了，不会再包含其他节点，所以末梢节点允许采用“/>”这种简写 

  方式。 

  譬如下面是个XML文件的布局内容，里面包含了根节点、布局节点，以及控件节点： 

  （完整代码见chapter02\src\main\res\layout\activity_main.xml） 

```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
   android:layout_width="match_parent"
   android:layout_height="match_parent">
   <!-- 这是个线性布局， match_parent意思是与上级视图保持一致-->
   <LinearLayout
       android:layout_width="match_parent"
       android:layout_height="match_parent">
       <!-- 这是个文本视图，名字叫做tv_hello，显示的文字内容为“Hello World!” -->
       <TextView
           android:id="@+id/tv_hello"
           android:layout_width="wrap_content"
           android:layout_height="wrap_content"
           android:text="Hello World!" />
   </LinearLayout> 
</LinearLayout>
```

上面的XML内容，最外层的LinearLayout标签为该界面的根节点，中间的LinearLayout标签为布局节 

  点，最内层的TextView为控件节点。由于根节点和布局节点都存在下级节点，因此它们要有配对的标签 

  头与标签尾，才能将下级节点包裹起来。根节点其实是特殊的布局节点，它的标签名称可以跟布局节点 

  一样，区别之处在于下列两点： 

  （ 1 ）每个界面只有一个根节点，却可能有多个布局节点，也可能没有中间的布局节点，此时所有控件节 

  点都挂在根节点下面。 

  （ 2 ）根节点必须配备“xmlns:android="http://schemas.android.com/apk/res/android"”，表示指定 

  XML内部的命名空间，有了这个命名空间，Android Studio会自动检查各节点的属性名称是否合法，如 

  果不合法就提示报错。至于布局节点就不能再指定命名空间了。 

  有了根节点、布局节点、控件节点之后，XML内容即可表达丰富多彩的界面布局，因为每个界面都能划 

  分为若干豆腐块，每个豆腐块再细分为若干控件罢了。三种节点之外，尚有“”这类注释标记，它的作用 

  是包裹注释性质的说明文字，方便其他开发者理解此处的XML含义。 

### 2.3.3　使用Java代码书写程序逻辑 

  在XML文件中定义界面布局，已经明确是可行的了，然而这只是静态界面，倘若要求在App运行时修改 

  文字内容，该当如何是好？倘若是动态变更网页内容，还能在HTML文件中嵌入JavaScript代码，由js片 

  段操作Web控件。但Android的XML文件仅仅是布局标记，不能再嵌入其他语言的代码了，也就是说， 

  只靠XML文件自身无法动态刷新某个控件。 

  XML固然表达不了复杂的业务逻辑，这副重担就得交给App后台的Java代码了。Android Studio每次创 

  建新项目，除了生成默认的首页布局activity_main.xml之外，还会生成与其对应的代码文件 

  MainActivity.java。赶紧打开MainActivity.java，看看里面有什么内容，该Java文件中MainActivity类的 

  内容如下所示： 

```java
public class MainActivity extends AppCompatActivity { 
   @Override
   protected void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState);
       setContentView(R.layout.activity_main); 
 }
}
```

可见MainActivity.java的代码内容很简单，只有一个MainActivity类，该类下面只有一个onCreate方 

  法。注意onCreate内部的setContentView方法直接引用了布局文件的名字activity_main，该方法的意 

  思是往当前活动界面填充activity_main.xml的布局内容。现在准备在这里改动，把文字内容改成中文。 

  首先打开activity_main.xml，在TextView节点下方补充一行android:id="@+id/tv_hello"，表示给它起 

  个名字编号；然后回到MainActivity.java，在setContentView方法下面补充几行代码，具体如下： 

  （完整代码见chapter02\src\main\java\com\example\chapter02\MainActivity.java） 

```java
public class MainActivity extends AppCompatActivity { 
   @Override
   protected void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState);
       // 当前的页面布局采用的是res/layout/activity_main.xml 
       setContentView(R.layout.activity_main);
       // 获取名叫tv_hello的TextView控件，注意添加导包语句import 
android.widget.TextView;
       TextView tv_hello = findViewById(R.id.tv_hello); 
       // 设置TextView控件的文字内容
       tv_hello.setText("你好，世界"); 
 }
}
```

  新增的两行代码主要做了这些事情：先调用findViewById方法，从布局文件中取出名为tv_hello的 

  TextView控件；再调用控件对象的setText方法，为其设置新的文字内容。 

  代码补充完毕，重新运行测试App，发现应用界面变成了如图2-19所示的样子。 

![Image From 笔记-Android 开发从入门到实战](https://gitee.com/xiaweifeng/picgo/raw/master/images/202207032204098.png)

  可见使用Java代码成功修改了界面控件的文字内容。 

## 2.4 App的活动页面 

  本节介绍了App活动页面的基本操作，首先手把手地分三步创建新的App页面，接着通过活动创建菜单 

  快速生成页面源码，然后说明了如何在代码中跳到新的活动页面。 

### 2.4.1　创建新的App页面 

  每次创建新的项目，都会生成默认的activity_main.xml和MainActivity.java，它们正是App首页对应的 

  XML文件和Java代码。若要增加新的页面，就得由开发者自行操作了，完整的页面创建过程包括 3 个步 

  骤：创建XML文件、创建Java代码、注册页面配置，分别介绍如下： 

  **1 ．创建XML文件** 

  在Android Studio左上方找到项目结构图，右击res目录下面的layout，在右键菜单中依次选择New→XML→Layout XML File， 在XML创建对话框的Layout File Name输入框中填写XML文件名，例如activity_main2，然后单击窗口右下角的Finish按钮。之后便会在layout目录下面看到新创建的XML文件activity_main2.xml，双击它即打开该XML的编辑窗口，再往其中填写详细的布局内容。 

  **2 ．创建Java代码** 

  同样在Android Studio左上方找到项目结构图，右击java目录下面的包名，弹出右键菜单。在右键菜单中依次选择New→Java Class，弹出如图2-23所示的代码创建窗口。 在代码创建窗口的Name输入框中填写Java类名，例如Main2Activity，然后单击窗口下方的OK按钮。之 

  后便会在Java包下面看到新创建的代码文件Main2Activity，双击它即可打开代码编辑窗口，再往其中填 

  写如下代码，表示加载来自activity_main2的页面布局。 

  （完整代码见chapter02\src\main\java\com\example\chapter02\Main2Activity.java） 

```xml
public class Main2Activity extends AppCompatActivity { 
   @Override
   protected void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState);
       setContentView(R.layout.activity_main2); 
 }
}
```

  3 ．注册页面配置 

  创建好了页面的XML文件及其Java代码，还得在项目中注册该页面，打开AndroidManifest.xml，在 

  application节点内部补充如下一行配置： 

```xml
<activity android:name=".Main2Activity"></activity>
```

  添加了上面这行配置，表示给该页面注册身份，否则App运行时打开页面会提示错误“activity not 

  found”。如果activity的标记头与标记尾中间没有其他内容，则节点配置也可省略为下面这样：

```xml
<activity android:name=".Main2Activity /"> 
```

  完成以上 3 个步骤后，才算创建了一个合法的新页面。 

### 2.4.2　快速生成页面源码 

  上一小节经过创建XML文件、创建Java代码、注册页面配置 3 个步骤，就算创建好了一个新页面，没想到 

  区区一个页面也这么费事，怎样才能提高开发效率呢？其实Android Studio早已集成了快速创建页面的 

  功能，只要一个对话框就能完成所有操作。 

  仍旧在项目结构图中，右击java目录下面的包名，弹出如图2-24所示的右键菜单。 

  右键菜单中依次选择New→Activity→Empty Activity，弹出如图2-25所示的页面创建对话框。 

![Image From 笔记-Android 开发从入门到实战](https://gitee.com/xiaweifeng/picgo/raw/master/images/202207032210408.png)

​	图2-25　活动页面的创建窗口 

  在页面创建对话框的Activity Name输入框中填写页面的Java类名（例如Main2Activity），此时下方的 

  Layout Name输入框会自动填写对应的XML文件名（例如activity_main2），单击对话框右下角的Finish 

  按钮，完成新页面的创建动作。 

  回到Android Studio左上方的项目结构图，发现res的layout目录下多了个activity_main2.xml，同时 

  java目录下多了个Main2Activity，并且Main2Activity代码已经设定了加载activity_main2布局。接着打 

  开AndroidManifest.xml，找到application节点发现多了下面这行配置： 

```xml
<activity android:name=".Main2Activity"></activity>
```

  检查结果说明，只要填写一个创建页面对话框，即可实现页面创建的 3 个步骤。 

### 2.4.3　跳到另一个页面 

  一旦创建好新页面，就得在合适的时候跳到该页面，假设出发页面为A，到达页面为B，那么跳转动作是 

  从A跳到B。由于启动App会自动打开默认主页MainActivity，因此跳跃的起点理所当然在MainActivity， 

  跳跃的终点则为目标页面的Activity。这种跳转动作翻译为Android代码，格式形如“startActivity(new 

  Intent(源页面.this, 目标页面.class));”。如果目标页面名为Main2Activity，跳转代码便是下面这样的：

```java
// 活动页面跳转，从MainActivity跳到Main2Activity
startActivity(new Intent(MainActivity.this, Main2Activity.class));
```

  因为跳转动作通常发生在当前页面，也就是从当前页面跳到其他页面，所以不产生歧义的话，可以使用 

  this指代当前页面。简化后的跳转代码如下所示： 

```java
startActivity(new Intent(this, Main2Activity.class));
```

  接下来做个实验，准备让App启动后在首页停留 3 秒， 3 秒之后跳到新页面Main2Activity。此处的延迟处 

  理功能，用到了Handler工具的postDelayed方法，该方法的第一个参数为待处理的Runnable任务对 

  象，第二个参数为延迟间隔（单位为毫秒）。为此在MainActivity.java中补充以下的跳转处理代码： 

  （完整代码见chapter02\src\main\java\com\example\chapter02\MainActivity.java） 

```java
@Override
   protected void onResume() {
       super.onResume();
       goNextPage(); // 跳到下个页面
 }
   // 跳到下个页面
   private void goNextPage() {
       TextView tv_hello = findViewById(R.id.tv_hello);
       tv_hello.setText("3秒后进入下个页面");
       // 延迟3秒（3000毫秒）后启动任务mGoNext
       new Handler(Looper.myLooper()).postDelayed(mGoNext, 3000);
 }
   private Runnable mGoNext = new Runnable() {
       @Override
       public void run() {
           // 活动页面跳转，从MainActivity跳到Main2Activity
           startActivity(new Intent(MainActivity.this, Main2Activity.class));
    }
  };
```

  运行测试App，过了 3 秒发生跳转事件的App界面，可见成功跳到了新页面。 

  当然，以上的跳转代码有些复杂，比如：Intent究竟是什么东西？为何在onResume方法中执行跳转动 

  作？Handler工具的处理机制是怎样的？带着这些疑问，后续章节将会逐渐展开，一层一层拨开Android 

  开发的迷雾。 

## 2.5　小结 

 本章主要介绍了App开发必须事先掌握的基础知识，包括App的开发特点（App的运行环境、App的开发 

  语言、App访问的数据库）、App的工程结构（App工程的目录结构、编译配置文件build.gradle、运行 

  配置文件AndroidManifest.xml）、App的设计规范（界面设计与代码逻辑、利用XML标记描绘应用界 

  面、使用Java代码书写程序逻辑）、App的活动页面（创建新的App页面、快速生成页面源码、跳转到另 

  一个页面）。 

  通过本章的学习，读者应该了解App开发的基本概念，并且熟悉App工程的组织形式，同时掌握使用 

  Android Studio完成一些简单操作。 