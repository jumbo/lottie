# 开始
Lottie 使用 Cocoapods, Carthage, Static 和 Dynamic modules，
Lottie 支持iOS8+ 和 MacOS 10.10+


# 安装

## Github Repo
从 [Lottie Github Repo](https://github.com/airbnb/lottie-ios/) 拉取代码，引入 Lottie.xcodeproj 编译动态或静态库.

## Cocoapods
获取[Cocoapods](https://cocoapods.org/)
为podfile添加如下信息：

```
pod 'lottie-ios'
```
run
```
pod install
```

安装之后引入Lottie
Objective C
`#import <Lottie/Lottie.h>`
Swift
`import Lottie`

## Carthage
获取 [Carthage](https://github.com/Carthage/Carthage)

为 Cartfile 添加 Lottie：
```
github "airbnb/lottie-ios" "master"
```
运行
```
carthage update
```

在应用 targets 的 “General” 标签内，找到 “Linked Frameworks and Libraries”，并将 `carthage update` 生成的 lottie-ios.framework (位置：Carthage/Build/iOS) 拖入该处。

# iOS 示例 App

克隆并运行 [示例 App](https://github.com/airbnb/lottie-ios/tree/master/Example)
该项目包含了 iOS App 和 MacOS App。

iOS App 演示了许多 Lottie 目前支持的特性。

![Example 1](/images/iosexample1.png)![Example 2](/images/iosexample2.png)
![Example 3](/images/iosexample3.png)

动画浏览器可以让你查找，播放，循环和修改动画大小。可从app包中加载，也可以用内建的二维码扫描[Lottie Files](http://www.lottiefiles.com/)获去动画。

## MacOS 示例 App

克隆并编译 [the Sample App](https://github.com/airbnb/lottie-ios/tree/master/Example)
包含了 iOS App 和 MacOS App。

![Lottie Viewer](/images/macexample.png)

MacOS 版的Lottie预览程序支持拖放JSON文件来打开，播放，循环动画。其动画执行代码与iOS版共享，所以你可以更快展示动画效果。

## Objective C 示例

Lottie 动画支持打包的JSON文件或从URL加载JSON
打包时只需将JSON和相关的图片一并加入xcode的target中。

```
LOTAnimationView *animation = [LOTAnimationView animationNamed:@"Lottie"];
[self.view addSubview:animation];
[animation playWithCompletion:^(BOOL animationFinished) {
  // Do Something
}];
```
使用多个来自多个bundle的动画：

```
LOTAnimationView *animation = [LOTAnimationView animationNamed:@"Lottie" inBundle:[NSBundle YOUR_BUNDLE]];
[self.view addSubview:animation];
[animation playWithCompletion:^(BOOL animationFinished) {
  // Do Something
}];
```

使用NSURL 异步加载：
```
LOTAnimationView *animation = [[LOTAnimationView alloc] initWithContentsOfURL:[NSURL URLWithString:URL]];
[self.view addSubview:animation];
```

Lottie 支持iOS的`UIViewContentModes`：aspectFit, aspectFill and scaleFill

交互式的改变动画播放进程：
```
CGPoint translation = [gesture getTranslationInView:self.view];
CGFloat progress = translation.y / self.view.bounds.size.height;
animationView.animationProgress = progress;
```

播放片段：
```
[lottieAnimation playFromProgress:0.25 toProgress:0.5 withCompletion:^(BOOL animationFinished) {
// Do Something
}];
```
## Swift 示例

Lottie 动画支持打包的JSON文件或从URL加载JSON
打包时只需将JSON和相关的图片一并加入xcode的target中。

```swift
let animationView = LOTAnimationView(name: "LottieLogo")
self.view.addSubview(animationView)
animationView.play()
```

使用多个来自多个bundle的动画：
```swift
let animationView = LOTAnimationView(name: "LottieLogo" bundle:yourBundle)
self.view.addSubview(animationView)
animationView.play()
```

使用NSURL 异步加载：
```swift
let animationView = LOTAnimationView(contentsOf: WebURL)
self.view.addSubview(animationView)
animationView.play()
```

交互式的改变动画播放进程：
```swift
let translation = gesture.getTranslationInView(self.view)
let progress = translation.y / self.view.bounds.size.height;
animationView.animationProgress = progress
```

播放片段：
```swift
animationView.play(fromProgress: 0.25, toProgress: 0.5, withCompletion: nil)
```
