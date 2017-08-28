# 运行中修改动画

不仅可以播放美妙的动画，还可以让你在播放的过程中调整动画。

## 假如要创建四个 switch 控件
![Toggle](/images/switch_Normal.gif)
<br />
创建并播放四个 switch 动画：
```swift
let animationView = LOTAnimationView(name: "toggle");
self.view.addSubview(animationView)
animationView.frame.origin.x = 40
animationView.frame.origin.y = 20
animationView.autoReverseAnimation = true
animationView.loopAnimation = true
animationView.play()

let animationView2 = LOTAnimationView(name: "toggle");
self.view.addSubview(animationView2)
animationView2.frame.origin.x = 40
animationView2.frame.origin.y = animationView.frame.maxY + 4
animationView2.autoReverseAnimation = true
animationView2.loopAnimation = true
animationView2.play()

let animationView3 = LOTAnimationView(name: "toggle");
self.view.addSubview(animationView3)
animationView3.frame.origin.x = 40
animationView3.frame.origin.y = animationView2.frame.maxY + 4
animationView3.autoReverseAnimation = true
animationView3.loopAnimation = true
animationView3.play()

let animationView4 = LOTAnimationView(name: "toggle");
self.view.addSubview(animationView4)
animationView4.frame.origin.x = 40
animationView4.frame.origin.y = animationView3.frame.maxY + 4
animationView4.autoReverseAnimation = true
animationView4.loopAnimation = true
animationView4.play()

```
## 改改颜色
![Recolored Toggle](/images/switch_BgColors.gif)
```swift
animationView2.setValue(UIColor.green, forKeypath: "BG-On.Group 1.Fill 1.Color", atFrame: 0)
animationView3.setValue(UIColor.red, forKeypath: "BG-On.Group 1.Fill 1.Color", atFrame: 0)
animationView4.setValue(UIColor.orange, forKeypath: "BG-On.Group 1.Fill 1.Color", atFrame: 0)
```
The keyPath is a dot seperated path of layer and property names from After Effects.
![Key Path](/images/aftereffectskeypath.png)
"BG-On.Group 1.Fill 1.Color"

## 调整一些属性
![Multiple Colors](/images/switch_MultipleBgs.gif)
```swift
animationView2.setValue(UIColor.green, forKeypath: "BG-On.Group 1.Fill 1.Color", atFrame: 0)
animationView2.setValue(UIColor.red, forKeypath: "BG-Off.Group 1.Fill 1.Color", atFrame: 0)
```

Lottie 允许修改After Effects中任一可执行动画的属性，如果缺少关键帧，一个线性插值的关键帧将自动创建，如果关键帧已存在，则直接执行数据替换。
