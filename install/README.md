# 在 Mac 系统下安装

## iPhone 环境设置与运行

### 安装运行

* 首先安装 Homebrew http://brew.sh/index_zh-cn.html
* 通过 brew update 升级 brew，通过brew upgrade nvm（等）可以升级安装的包
* 安装 nvm 可以通过官网，也可以利用 brew install nvm 安装好后执行 `nvm install node && nvm alias default node` 来安装 node
* 安装 watchman，用来检测文件变化的工具  brew install watchman
* 安装 flow brew install flow 用来检测 jsx 语法的工具
* 安装 react-native-cli  sudo npm install -g react-native-cli
* react-native init HelloWorld，初始慢的话设置镜像 `npm config set registry https://registry.npm.taobao.org` ，或者 vpn
* 到 app 商店安装 Xcode
* cd HelloWorld 并且 open ios/HelloWorld.xcodeproj/
* 看说明运行

    ```
    To run your app on iOS:

       Open HelloWorld.xcodeproj in Xcode, Hit the Run button

       Or   react-native  run-ios

    To run your app on Android:

       Have an Android emulator running (quickest way to get started), or a device connected

       cd /Users/wangyanjun/gitworkspace/Hello

       react-native run-android
    ```

### 安装运行问题解决

安装和运行过程中可能会有些坑，以下是参考链接

http://facebook.github.io/react-native/docs/getting-started.html#content

https://github.com/facebook/react-native/issues/5393#issuecomment-174319207

http://www.tuicool.com/articles/2U7FR3z

主要是一些依赖，解决的办法可以重新安装了 brew 和相关组件，并更新到最新版本

另外就是 babel 的问题，需要安装完 node_modules 后在 package.json 中添加以下脚本

```
"scripts": {

    "start": "node node_modules/react-native/local-cli/cli.js start",

    "clean:babelrc": "find ./node_modules -name react-packager -prune -o -name '.babelrc' -print | xargs rm -f",

    "postinstall": "npm run clean:babelrc"

  },
```

添加后在命令行运行 npm run pastinstall 删除babelrc

不过应该在随后的第三方 npm 包升级后会解决该问题，期待中

### 修改文件后刷新 app
修改文件后切换到模拟器，然后按 command + R 即可刷新页面，或者按 command + D 调出菜单来刷新或调试页面

### 修改指定的 js 主文件以及服务端口
在 AppDelegate.m 中修改
` jsCodeLocation = [NSURL URLWithString:@"http://localhost:8081/index.ios.bundle?platform=ios&dev=true"];`

## Android 环境设置与运行

* [安装最新版的JDK](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
* 安装Android SDK  ```brew install android-sdk```  下载有点慢，请耐心等待
* 设置环境变量，打开或创建 ~/.bashrc 新增 `export ANDROID_HOME=/usr/local/opt/android-sdk`
  在命令窗口执行 vim ~/.bashrc  添加 `export ANDROID_HOME=/usr/local/opt/android-sdk`
  对 vi 或 vim 命令不是很清楚的可以查看[这里](http://www.eepw.com.cn/article/48018.htm)
* 开启gradle daemon（待开启）
* 设置SDK
  在命令行运行 android 打开 SDK 管理，下载需要的相关 sdk，具体下载那些，参看[官网截图](https://facebook.github.io/react-native/docs/android-setup.html)，
  需要说明的是，国内用户推荐使用[腾讯Bugly的镜像](http://android-mirror.bugly.qq.com:8080/include/usage.html)来加速下载。
  **注意：Android SDK Build-tools 版本要与当前版本一致，否则会报错**
* 安装Genymotion
    - 下载并安装 [Genymotion](https://www.genymotion.com/)。
    - 打开 Genymotion。如果你尚未安装VirtualBox，他会提示你安装，安装下载地址：https://www.virtualbox.org/wiki/Downloads
    - 创建一个模拟器并启动（需要登录并安装一个模拟器 virtual device，然后点击 start 按钮）
* 执行命令 react-native run-android 运行 Android App

# 参考
* https://facebook.github.io/react-native/docs/getting-started.html
* https://facebook.github.io/react-native/docs/android-setup.html
* http://reactnative.cn/docs/getting-started.html
* http://reactnative.cn/docs/android-setup.html
