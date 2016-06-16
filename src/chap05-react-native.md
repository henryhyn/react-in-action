# 搭建 React Native 开发环境

俗话说"万事开头难", 搭建开发环境往往会难道一大批童鞋,
因此, 本章将详细介绍 React Native 开发环境的搭建, 希望助各位童鞋一臂之力!
注意, 这里的操作系统为 OS X EI Capitan.

## 先决条件

安装 Homebrew, 参见[官网](http://brew.sh).
通过 Homebrew 安装 watchman 和 flow.
首先要更新 brew, 并升级安装过的组件, 执行如下语句即可.

```{.numberLines}
brew update && brew upgrade
brew install watchman flow
```

## 安装 React Native



通过 npm 全局安装 React Native 客户端, 执行如下命令.

```{.bash .numberLines}
npm install -g react-native-cli
```

## 创建项目

### 初始化项目

比如创建一个名为 `AwesomeProject` 的项目, 进入工作空间 (比如, 我的是 `~/workspace`), 执行如下命令.

```{.numberLines}
react-native init AwesomeProject
```

### 启动服务

进入项目目录 `AwesomeProject`, 执行如下命令.

```{.numberLines}
npm start
```

### 启动 React Native IOS

更新 Xcode 到最新版本, 保证 Xcode 6.3 及以上版本.
执行如下命令, 即可启动 IOS 开发

```{.bash .numberLines}
react-native run-ios
```

![React Native IOS](react-native-ios.png)

## 安装 Android Studio

安装 Java 8 JDK


进入 Android Studio [官方网站](https://developer.android.com/studio/index.html),
截止目前为止, 最新版为 `android-studio-ide-143.2915827`, 根据电脑系统下载对应的版本.

下面以 Mac 系统为例, 演示 Android Studio 的安装及配置,
下载 `android-studio-ide-143.2915827-mac.dmg` 文件, 双击打开, 根据提示完成安装.

![安装 Android Studio](android-studio-install.png)

### 配置 IDE

启动 Android Studio,

![配置](android-studio-setup1.png)

![配置](android-studio-setup2.png)

![配置](android-studio-setup3.png)

![配置](android-studio-setup4.png)

![配置](android-studio-setup5.png)



![配置](android-studio-setup6.png)

![配置](android-studio-setup7.png)

![配置](android-studio-setup8.png)

### 启动 AVD

```{.numberLines}
export ANDROID_HOME=/Users/Henry/Library/Android/sdk
export PATH=$ANDROID_HOME/tools:$ANDROID_HOME/platform-tools:$PATH
```

```{.bash .numberLines}
$ emulator -list-avds
react-native
$ emulator -avd react-native
```

```{.bash .numberLines}
$ adb devices
List of devices attached
emulator-5554   device
```

### 启动 React Native Android

```{.bash .numberLines}
react-native run-android
```

![React Native Android](react-native-android.png)

\newpage

### 创建 AVD

```{.numberLines}
Creating Android virtual device
Unable to create a virtual device: Unable to create Android virtual device
```

![AVD](avd1.png)

![AVD](avd2.png)

![AVD](avd3.png)

![AVD](avd4.png)

\newpage

### 安装 SDK

```{.numberLines}
A problem occurred configuring project ':app'.
> failed to find Build Tools revision 23.0.1
```

![安装 Android SDK Build-tools](android-sdk.png)

### 相关路径

```{.numberLines}
/Applications/Android\ Studio.app
~/Library/Application\ Support/AndroidStudio2.1
~/Library/Preferences/AndroidStudio2.1
~/Library/Caches/AndroidStudio2.1
~/Library/Logs/AndroidStudio2.1
~/.android
~/Library/Android
```

## 参考资料

-   [React Native 官方文档中文版](http://wiki.jikexueyuan.com/project/react-native/homepage.html)
-   [大姑爷博客](http://www.daguye.com)