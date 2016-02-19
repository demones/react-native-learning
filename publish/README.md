# 调试与发布

## iphone 环境下

### xcode 7 真机调试

前面已经介绍了在 Mac 电脑中通过模拟器来运行 react-native app。这里主要说一下在 iPhone 怎么运行，
xcode 7 提供了免费直接在 iPhone 中运行，下面把主要的步骤说说

* 添加 Apple ID
* 选择在真机上运行
* 提示 Could not launch "My App" process launch failed: Security ，表示需要在手机端信任该软件
  参见 http://www.jianshu.com/p/269b0db55390，对于 iPhone 9.2 以上版本，在 `设置 -> 通用 -> 设备管理 -> "你的AppleID" 选择信任`

具体怎样在真机上调试，以下两篇文章讲的 很详细，这里就不罗嗦了

http://www.cnblogs.com/dssf/p/4747358.html

http://www.cnblogs.com/tandaxia/p/4839997.html

**注意**
* 在真机上调试需要修改web服务 ip
  打开文件`AppDelegate.h` ，把 `jsCodeLocation = [NSURL URLWithString:@"http://localhost:8081/index.ios.bundle?platform=ios&dev=true"];` 中的 `localhost` 改成实际的 IP
* 需要修改 Bundle identifier，改成自己的，不能用 facebook 的

### 在 Chrome 中调试

在 Chrome 中调试参见官网 https://facebook.github.io/react-native/docs/debugging.html#content

中文地址为 http://reactnative.cn/docs/debugging.html#content

### 在 APP Store 中发布

发布的时候应该把 `jsCodeLocation = [NSURL URLWithString:@"http://localhost:8081/index.ios.bundle?platform=ios&dev=true"];`
注释掉，还要记得选择release版本，这样调试菜单就不会出现。
