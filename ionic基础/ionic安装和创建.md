### 一、简介

ionic是一个强大的HTML5应用程序开发框架。可以帮助您使用web技术，比如HTML、CSS、javascript构建接近原生体验的移动应用程序。

ionic是一个轻量级的手机UI库，具有速度快，界面现代化、美观等特点。为了解决其他一些UI库在手机上运行缓慢的问题，它直接放弃了IOS6和android4.1以下的版本支持，来获取更好的使用体验。

### 二、特点

- ionic基于angular语法，简单易学
- ionic是一个轻量级框架
- ionic完美的融合下一代移动框架，支持angularJS特性，MVC，代码易维护
- ionic提供了漂亮的设计，通过SASS构建应用程序，它提供了很多UI组件来帮助开发者开发强大的应用
- ionic专注原声，让你看不出混合应用和原生的区别
- ionic提供了强大的命令行工具
- ionic性能优越，运行速度快

### 三、安装

下载地址：http://ionicframework.com/docs/v1/overview/#download 或 https://github.com/driftyco/ionic

下载后解压压缩包，包含以下目录：

| 文件名          | 文件内容       |
| ------------ | ---------- |
| css/         | 样式         |
| fonts/       | 字体文件       |
| js/          | javascript |
| version.json | 版本更新说明     |

接下来，我们只需要在项目中引入以上目录中的css/ionic.min.css和js/ionic.bundle.min.js文件即可创建ionic应用。

```html
<html ng-app="ionicApp">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="initial-scale=1, maximum-scale=1, user-scalable=no, width=device-width">
    <title>hello world</title>
    <link href="https://cdn.bootcss.com/ionic/1.3.2/css/ionic.css" rel="stylesheet">
    <script src="https://cdn.bootcss.com/ionic/1.3.2/js/ionic.bundle.min.js"></script>
    <script type="text/javascript">
    angular.module('ionicApp', ['ionic'])
    .controller('MyCtrl', function($scope) {
    });
    </script>
    <style>
    body {
    cursor: url('http://www.runoob.com/static/img/finger.png'), auto;
    }
    </style>
</head>
<body ng-controller="MyCtrl">
    <ion-header-bar class="bar-positive">
    	<h1 class="title">Hello World!</h1>
    </ion-header-bar>
    <ion-content>
        <p>我的第一个 ionic 应用。</p>
    </ion-content>
    </body>
</html>
```

### 四、命令行安装（移动设备上运行）

首先需要安装[node.js](http://www.runoob.com/nodejs/nodejs-install-setup.html)，因为接下来的安装中需要用到[npm工具](http://www.runoob.com/nodejs/nodejs-npm.html)。然后通过命令行工具安装最新版本的cordova和ionic。通过参考[android](http://cordova.apache.org/docs/en/latest/guide/platforms/android/index.html)和[ios](http://cordova.apache.org/docs/en/latest/guide/platforms/ios/index.html)官方文档来安装。

#### 4.1安装node.js（最好安装最新版本）

首先，从[node.js官网](https://nodejs.org/)下载，网速过慢请移步[国内镜像](https://pan.baidu.com/s/1kU5OCOB#list/path=%2Fpub%2Fnodejs)。

- 在windows上安装时务必选择全部组件，包括勾选Add to Path。
- 安装完成后，打开命令输入`node -v`，如果安装正常，就会显示版本的输出。
- 继续在命令输入`node`，此刻你将进入node.js的交互环境，你可以输入任意javascript语句。

#### 4.2npm工具

npm是随同node.js一起安装的包管理工具（package manager），能解决node.js代码部署上的很多问题，常见的场景有以下几种：

- 允许用户从npm服务器下载别人编写的第三方包到本地使用
- 允许用户从npm服务器下载并安装别人编写的命令行程序到本地使用
- 允许用户将自己编写的包或命令行程序上传到npm服务器供别人使用

为啥我们需要一个包管理工具呢？因为我们在Node.js上开发时，会用到很多别人写的JavaScript代码。如果我们要使用别人写的某个包，每次都根据名称搜索一下官方网站，下载代码，解压，再使用，非常繁琐。于是一个集中管理的工具应运而生：大家都把自己开发的模块打包后放到npm官网上，如果要使用，直接通过npm安装就可以直接用，不用管代码存在哪，应该从哪下载。

更重要的是，如果我们要使用模块A，而模块A又依赖于模块B，模块B又依赖于模块X和模块Y，npm可以根据依赖关系，把所有依赖的包都下载下来并管理起来。否则，靠我们自己手动管理，肯定既麻烦又容易出错。

其实npm已经在node.js安装的时候顺带安装好了，在命令行上输入`npm -v`就可以看到版本的输出。

```
$ npm -v
2.3.0
```

如果你安装的是旧版本的npm，可以很容易的通过npm命令来升级，命令如下：

```
$ sudo npm install npm -g
```

如果是window系统使用以下命令：

```
npm install npm -g
```

使用淘宝镜像的命令

```
cnpm install npm -g
```

##### 4.2.1使用npm命令安装模块

npm安装node.js模块语法格式如下：

```
$ npm install <module name>
我们使用 npm 命令安装常用的 Node.js web框架模块 express:
$ npm install express
```

安装好之后，express 包就放在了工程目录下的 node_modules 目录中，因此在代码中只需要通过 **require('express')** 的方式就好，无需指定第三方包路径。

```
var express = require('express')
```

##### 4.2.2全局安装与本地安装

npm的包安装分为本地安装（local）、全局安装（global）两种，从敲的命令行来看，差别只是有没有-g而已：

```
npm install express   //本地安装
npm install express -g //全局安装
```

如果出现以下错误：

```
npm err! Error: connect ECONNREFUSED 127.0.0.1:8087
```

解决办法为：

```
$ npm config set proxy null
```

###### 本地安装

- 将安装包放在./node_modules下（运行npm命令时所在的目录），如果没有node_modules目录，会在当前执行npm命令的目录下生成node_modules目录。
- 可以通过require()来引入本地安装的包。

###### 全局安装

- 将安装包放在/usr/local下或者你的node的安装目录
- 可以直接在命令里使用

如果你希望具备两者功能，则需要在两个地方安装它或使用`npm link`

接下来我们使用全局方式安装express

```
$ npm install express -g
```

安装过程输出如下内容，第一行输出了模块的版本号及安装位置

```
express@4.13.3 node_modules/express
```

###### 查看安装信息

```
$ npm list -g
```

如果要查看某个模块的版本号，可以使用命令如下：

```
$ npm list grunt
```

###### 卸载模块

```
$ npm uninstall express
```

卸载后，你可以到/node_modules/目录下查看包是否还存在，或者使用命令查看：

```
$ npm ls
```

###### 更新模块

```
$ npm update express
```

###### 搜索模块

```
$ npm search express
```

#### 4.3安装cordova和ionic

window和linux上打开命令行工具执行以下命令：

```
$ npm install -g cordova ionic
```

mac系统上使用以下命令：

```
sudo npm install -g cordova ionic
```

如果你已经安装了以上环境，可以执行以下命令来更新新版本：

```
npm update -g cordova ionic
```

或

```
sudo npm update -g cordova ionic
```

### 五、创建应用前的安装

#### 5.1安装node.js

前面内容已经说明了怎么安装。

#### 5.2下载JDK，并配置java环境

- [下载JDK](http://www.oracle.com/technetwork/java/javase/downloads/index.html)
- 安装JDK选择安装目录，安装过程中会出现两次安装提示 。第一次是安装 jdk ，第二次是安装 jre 。建议两个都安装在同一个java文件夹中的不同文件夹中。（不能都安装在java文件夹的根目录下，jdk和jre安装在同一文件夹会出错）
- 安装jdk随意选择目录只需把默认安装目录 \java 之前的目录修改即可；安装jre→更改→ \java 之前目录和安装 jdk 目录相同即可。
- 安装完JDK后配置环境变量  计算机→属性→高级系统设置→高级→环境变量
- 系统变量→新建 JAVA_HOME 变量 。变量值填写jdk的安装目录（本人是 E:\Java\jdk1.7.0）
- 系统变量→寻找 Path 变量→编辑，在变量值最后输入 `%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;`（注意原来Path的变量值末尾有没有;号，如果没有，先输入；号再输入上面的代码）。
- 系统变量→新建 CLASSPATH变量，变量值填写  `.;%JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar`（注意最前面有一点）系统变量配置完毕。
- 检验是否配置成功 运行`cmd` 输入 `java -version` （java 和 -version 之间有空格）或输入`javac`。若显示版本信息 则说明安装和配置成功。

####5.3安装ant，并配置相应的环境

- [下载ant](http://ant.apache.org/bindownload.cgi)

  ![QQ截图20170514144632](.\img\QQ截图20170514144632.png)

  ![QQ截图20170514144643](.\img\QQ截图20170514144643.png)

- 可以下载官网上对应系统的最新版本不，也可以在old ant版本中选择自己需要的版本。

  ![QQ截图20170514144656](.\img\QQ截图20170514144656.png)

- 选择系统对应的版本，windows系统，选择zip下载。下载完成后，解压到指定路径下。

- 配置环境变量

  ![QQ截图20170514150706](.\img\QQ截图20170514150706.png)

  ![QQ截图20170514150732](.\img\QQ截图20170514150732.png)

  ![QQ截图20170514150706](.\img\QQ截图20170514150724.png)

  - ANT_HOME      E:\ant\apache-ant-1.9.9
  - path                  E:\ant\apache-ant-1.9.9\bin
  - classpath         E:\ant\apache-ant-1.9.9\lib

- ant验证：win+R  --  cmd

  输入如下命令：ant

  如果出现如下内容，说明安装成功：

  Buildfile: build.xml does not exist!

  Build failed

  说明ant安装成功！因为ant默认运行build.xml文件，这个文件需要我们建立。

  查看版本：ant  -version

  但如果出现 

  'ant' 不是内部或外部命令，也不是可运行的程序或批处理文件

  说明安装失败：（可以重复前述步骤，直至安装成功。）

#### 5.4安装cordova，[官网有](http://cordova.axuer.com/)

![QQ截图20170514152007](.\img\QQ截图20170514152007.png)

#### 5.5安装express

- `npm install express`

#### 5.6安装ionic

- `npm install -g ionic`
- 安装android SDK(安装前先要安装java环境也就是JDK)
  - 在系统变量里找到Path选中
  - 在变量值里加入androidSDK中platform-tools和tools的目录路径，这里我的是E:\android-sdk_r20.0.3-windows\android-sdk-windows\platform-tools和E:\adt-bundle-windows-x86_64-20130729\sdk\tools。当然两个之间要加个分号“;”。
  - 在windows运行符上运行adb
- 检测是否安装好ionic， `ionic -v`

#### 5.7以上安装尽量使用淘宝镜像来安装

- 安装淘宝镜像

  ```
  $ npm install -g cnpm --registry=http://registry.npm.taobao.org
  ```

- 安装完成后，所有插件都使用`cnpm`这个命令来安装

  ```
  $ cnpm update -g cordova ionic
  ```

  ​

### 六、创建应用

使用ionic官方提供的现成的应用程序模板，或一个空白的项目创建一个ionic应用：

```
$ ionic start myApp tabs
```

##### 运行我们刚才创建的ionic项目

使用ionic tool创建，测试，运行你的apps(或者通过cordova直接创建)。

##### 创建android应用

```
$ cd myApp
$ ionic platform add android  //如果执行到这一步报错 那就要安装SDK
$ ionic build android
$ ionic emulate android
```

如果一切正常就会弹出模拟器

##### 创建IOS应用

```
$ cd myApp
$ ionic platform add ios  //如果执行到这一步报错 那就要安装SDK
$ ionic build ios
$ ionic emulate ios
```

如果出现`ios-sim was not not found`错误，可以执行以下命令：

```
npm install -g ios-sim
```

如果一切正常就会弹出模拟器

##### lonic Lab

Ionic Lab 是桌面版的开发环境，如果你不喜欢使用命令行操作，Ionic Lab 将会满足你的需求。Ionic Lab 为开发者提供了一个更简单的方法来开始，编译，运行，和模拟运行Ionic的应用程序。

Ionic Lab 支持的平台有：Window、Mac OS X、Linux，下载地址为：http://lab.ionic.io/，下载后直接安装即可。

通过以上界面你可以完成以下操作：

- 创建应用

- 预览应用

- 编译应用

- 运行应用

- 上传应用

- 运行日志查看

- ……