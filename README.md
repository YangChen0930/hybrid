# hybrid 简易开发环境搭建

## 软件安装

### JDK

[Java SE Downloads](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

#### 环境变量
JDK
```
JAVA_HOME
D:\Program Files\Java\jdk1.8.0_172
PATH
%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;
CLASSPATH
.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;
```

### Android Studio

[Download Android Studio](https://developer.android.google.cn/studio/)

[安装 Android Studio](https://developer.android.com/studio/install?hl=zh-cn)

#### 配置代理

安装过程中弹出配置代理的提示框
选择手动配置代理
安装过程中的提示框配置，与下图(下图为安装完成后File->Settings的截图)，类似

![](hybrid简易开发环境搭建/2018-07-06-10-08-14.png)

**Android Studio 在构建应用的过程中需要下载 SDK, Gradle, build tools 等等**

#### 环境变量

![](hybrid简易开发环境搭建/2018-07-06-10-26-01.png)

![](hybrid简易开发环境搭建/2018-07-06-10-26-44.png)

Android
```
ANDROID_HOME
C:\Users\Administrator\AppData\Local\Android\Sdk
PATH
%ANDROID_HOME%\tools;%ANDROID_HOME%\tools\bin;%ANDROID_HOME%\platform-tools;
```

Gradle
```
GRADLE_HOME
D:\Program Files\Android\Android Studio\gradle\gradle-4.4
PATH
%GRADLE_HOME%\bin;
```

### Genymotion

[Genymotion Desktop](https://www.genymotion.com/desktop/)

个人版
https://www.genymotion.com/fun-zone/
完整版
https://www.genymotion.com/get-full-version/

上面都是下载的同一个安装文件

![](hybrid简易开发环境搭建/2018-07-11-16-20-31.png)

下载个人版

![](hybrid简易开发环境搭建/2018-07-11-16-28-00.png)
前面 virtual box 已经单独安装过了
所以选择不带 virtualbox 的

![](hybrid简易开发环境搭建/2018-07-11-16-33-24.png)
可以 personal use

但是 Add 模拟器的时候需要登陆
![](hybrid简易开发环境搭建/2018-07-11-16-36-05.png)
创建完模拟器后可以 退出账号，不影响一般使用

![](hybrid简易开发环境搭建/2018-07-11-16-40-45.png)
没有登陆的情况下，选择Personal use，模拟器底部会又这个水印
登陆的情况下，账号的试用期超过30天就用不了吧。

#### 在 Genymotion 中配置使用 Android Studio 的 tools

![](hybrid简易开发环境搭建/2018-07-06-11-00-39.png)

#### 在 Android Studio 中配置 Genymotion

安装 Genymotion 的插件

![](hybrid简易开发环境搭建/2018-07-06-10-20-38.png)

指定 Genymotion 的安装目录

![](hybrid简易开发环境搭建/2018-07-06-10-21-22.png)

#### 配置代理

![](hybrid简易开发环境搭建/2018-07-06-10-23-44.png)

#### 新建模拟器

![](hybrid简易开发环境搭建/2018-07-06-10-35-47.png)

![](hybrid简易开发环境搭建/2018-07-06-10-36-37.png)

![](hybrid简易开发环境搭建/2018-07-06-10-36-51.png)

#### 在 Android Studio 中新建项目

新建项目

![](hybrid简易开发环境搭建/2018-07-06-10-39-13.png)

指定包名

![](hybrid简易开发环境搭建/2018-07-06-10-40-34.png)

目标 API 版本

![](hybrid简易开发环境搭建/2018-07-06-10-41-46.png)

添加一个 Activity

![](hybrid简易开发环境搭建/2018-07-06-10-43-08.png)
![](hybrid简易开发环境搭建/2018-07-06-10-43-21.png)

新建项目完成

![](hybrid简易开发环境搭建/2018-07-06-10-45-08.png)

运行

![](hybrid简易开发环境搭建/2018-07-06-10-45-54.png)
![](hybrid简易开发环境搭建/2018-07-06-10-49-52.png)
![](hybrid简易开发环境搭建/2018-07-06-10-50-05.png)

修改

![](hybrid简易开发环境搭建/2018-07-06-10-49-31.png)
![](hybrid简易开发环境搭建/2018-07-06-10-51-43.png)
![](hybrid简易开发环境搭建/2018-07-06-10-51-51.png)

### nodejs

https://nodejs.org/zh-cn/

#### 配置国内镜像源

```bash
node -v
npm config -g set registry "https://registry.npm.taobao.org"
npm config list -g
```

![](hybrid简易开发环境搭建/2018-07-06-11-10-58.png)

### Cordova 

https://cordova.apache.org/#getstarted

```bash
npm i -g cordova
```

#### 新建项目

```bash
cordova create RunningMan
cd RunningMan
cordova platform add android
cordova platform ls
cordova run android
```

Genymotion 的模拟器正在运行的情况下，Cordova 会把打包好的 apk push 过去

![](hybrid简易开发环境搭建/2018-07-06-14-28-50.png)

#### 打包例子 vue-tetris
https://github.com/Binaryify/vue-tetris/
把 vue-tetris 项目 clone 到本机，修改配置，安装依赖，build
![](hybrid简易开发环境搭建/2018-07-06-11-52-35.png)
修改 `config/index.js => build => assetsPublicPath`
```javascript
assetsPublicPath: './',
```
![](hybrid简易开发环境搭建/2018-07-06-11-49-12.png)
把`npm run build` 生成的 dist 目录下的文件全部复制到 Cordova 项目的 www 文件下
在 Cordova 项目下运行 `cordova run android`
发现 Genymotion 模拟器中运行了，但一直是加载的画面

浏览器中连接 Android
`chrome://inspect/#devices`
![](hybrid简易开发环境搭建/2018-07-06-13-37-46.png)
console 报错 `navigator.languages.find is not a function`
搜索后定位到 `src/unit/const.js`
![](hybrid简易开发环境搭建/2018-07-06-11-48-14.png)
修改源码后重新 `npm run build`
把生成的 dist 目录下的文件全部复制到 Cordova 项目的 www 文件下
在 Cordova 项目下运行 `cordova run android`
![](hybrid简易开发环境搭建/2018-07-06-13-39-15.png)


#### 打包例子 Vux

https://doc.vux.li/zh-CN/install/biolerplate.html

```bash
npm install vue-cli -g # 如果还没安装
vue init airyland/vux2 projectPath

cd projectPath
npm i # 安装依赖 或者 yarn
npm run dev # 或者 yarn dev
npm run build # 或者 yarn build
```

```bash
#  不使用 yarn 可以忽略
npm i -g yarn
yarn config set registry https://registry.npm.taobao.org
```

修改 `config/index.js => build => assetsPublicPath`
```javascript
assetsPublicPath: './',
```

把生成的 dist 目录下的文件全部复制到 Cordova 项目的 www 文件下
在 Cordova 项目下运行 `cordova run android`

![](hybrid简易开发环境搭建/2018-07-06-14-08-30.png)

#### Camera
[cordova-plugin-camera](https://cordova.apache.org/docs/en/latest/reference/cordova-plugin-camera/index.html)

```bash
cd cordova8
cordova plugin add cordova-plugin-camera
cordova plugin ls
```

[Cordova结合Vue学习Camera](https://www.jianshu.com/p/2370548b25ab)
![](hybrid简易开发环境搭建/indexhtmladdcordovajs.png)
![](hybrid简易开发环境搭建/indexhtmladdcordova.png)

>	别忘了在cordova项目下添加camera插件
>	vuejs工程build出来的dist/index.html里面加上cordova.js
>	否则调用不到相机插件
>	看看那个cordova framework7 的模板build出来的dist/index.html是不是被模板自动加上了cordova.js

---

## 参考

### 文档文章

### 常见错误

#### Cordova

* cordova 创建工程失败

	为此，执行以下这些命令后，
	把工程放到了 git 管理，https://gitee.com/boston/cordova8
	方便以后重复使用
	```bash
	cordova create cordova8
	cd cordova8
	cordova platform add android
	```

	把项目 clone 到本机，执行 `npm i`，不用 `yarn`
	![](hybrid简易开发环境搭建/cordova8-gitee.png)
	![](hybrid简易开发环境搭建/2018-07-06-14-39-44.png)
	![](hybrid简易开发环境搭建/2018-07-06-14-40-10.png)
	
	**remove** then **add** android platform

	https://github.com/apache/cordova-ios/pull/132#issuecomment-135665090

	![](hybrid简易开发环境搭建/2018-07-06-14-41-58.png)
	build successful
	![](hybrid简易开发环境搭建/2018-07-06-14-42-36.png)
	launch success
	![](hybrid简易开发环境搭建/2018-07-06-14-53-04.png)

	```bash
	git clone https://gitee.com/boston/cordova8.git
	cd cordova8
	npm i
	cordova platform ls
	cordova requirements
	cordova platform remove android
	cordova platform add android
	cordova platform ls
	cordova requirements
	cordova run android
	```
---

