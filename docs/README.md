# Lottie for [Android](https://github.com/airbnb/lottie-android), [iOS](https://github.com/airbnb/lottie-ios), and [React Native](https://github.com/airbnb/lottie-react-native)

Lottie 是将[Adobe After Effects](http://www.adobe.com/products/aftereffects.html) 插件 [Bodymovin](https://github.com/bodymovin/bodymovin) 所导出的json 解析为 Android和iOS动画的移动端框架。

设计师第一次可以创造并输出完美的动画，无需工程师手动调整代码，一图胜千言：

![Lottie Logo animation](images/Introduction_00_sm.gif)

![Example1](images/Introduction_01_sm.gif)


![Example2](images/Introduction_02_sm.gif)


![Example3](images/Introduction_03_sm.gif)


![Example4](images/Introduction_04_sm.gif)


以上所有动画都是 After Effects 创作，并由 Bodymovin 导出，而后直接运行于手机App，无需工程师的付出太多。

Bodymovin 是由 Hernan Torrisi 创作的AE插件，用来将 AE 文件导出为 json 和一个javascript web player。Lottie 是基于该实现并拓展到 Android，iOS和 React Native。

更多信息参阅 [博客文章](http://airbnb.design/introducing-lottie/)

## 其他平台
 * [Xamarin](https://github.com/martijn00/LottieXamarin)
 * [NativeScript](https://github.com/bradmartin/nativescript-lottie)
 * [Appcelerator Titanium](https://github.com/m1ga/ti.animation)

## 示例 App

自行编译示例 App 或者从 [Play Store](https://play.google.com/store/apps/details?id=com.airbnb.lottie) 下载，App 中内置了一些动画，也可以打包新动画或者从URL加载。

## 其他替代方案
1. 手工编写动画代码。 同时为 Android 和 iOS 平台编写动画代码将会耗费巨大的难以预估的设计和开发时间。甚至在花费了如此多时间后仍无法保证可以完美还原动画。
2. [Facebook Keyframes](https://github.com/facebookincubator/Keyframes)
   . Keyframes 是 Facebook 出品的一个优秀的动画代码库。然而, Keyframes 支持的 AE 动画特性较少，例如 Lottie 所支持的遮罩、蒙版、路径修建、虚线等等它都没有提供支持。
2. Gifs 动画。 Gifs 占用了数倍于 bodymovin 导出的 JSON 文件的大小，而且只能在一个固定的尺寸渲染无法放大适配高分辨率屏幕。（译者注： gif 的问题还有颜色数最高只有 256 色导致的画质不高，画面中的渐变容易出现断层，如果是带透明通道的 gif 几乎都会产出毛边。）
3. Png 图像序列。 Png 图像序列的效果甚至比 gif 还要糟糕，因为它的体积可能达到 json 的几十倍而且同样无法放大。
4. Animated Vector Drawable \(Android only\). 性能更好的方案，因为运行于 RenderThread 而非 main thread. 仅支持优先的效果。 无法调整进度，不支持动态颜色，不支持网络加载动画。

## 为什么称作 Lottie?
Lottie 是以德国剪影动画先驱 Lotte Reiniger （洛特·雷妮格）的名字命名的。 她最出名的作品是《阿基米德王子历险记》 (1926) – 世界上第一部长篇动画电影。 比华尔特·迪士尼的长篇动画电影——《白雪公主与七个小矮人》 (1937) 还要早了 10 年。[洛特·雷妮格的艺术](https://www.youtube.com/watch?v=LvU55CUw5Ck&feature=youtu.be)

## Contributing
Contributors are more than welcome. Just upload a PR with a description of your changes.

If you would like to add more JSON files feel free to do so!

## Issues or feature requests?
File github issues for anything that is unexpectedly broken. If an After Effects file is not working, please attach it to your issue. Debugging without the original file is much more difficult.

## 文章, 采访 & 播客

Here are some articles and podcasts from the Lottie team @ Airbnb

[Behind the scenes: Why we built Lottie, our new open-source animation tool here.](https://airbnb.design/introducing-lottie/)

[Dig into the details and back story with Brandon Withrow and Salih Abdul-Karim on the School of motion podcast](https://www.schoolofmotion.com/blog/after-effects-to-code-lottie-from-airbnb)

[Learn more about Lottie from Gabriel Peal on the Fragmented Podcast](http://fragmentedpodcast.com/episodes/82/)

[Lottie Animation with Brandon Withrow and Gabriel Peal on Software engineering daily podcast](https://softwareengineeringdaily.com/2017/08/10/lottie-animation-with-brandon-withrow-and-gabriel-peal/)


## 社区文章和视频

一些来自社区的文章和视频：

[A Lottie to Like](https://t.co/dadjvgv9vk) by Nick Butcher

[Creating better user experiences with animations and Lottie](https://pspdfkit.com/blog/2017/creating-better-user-experiences-with-animations-and-lottie/)by Samo Korosec and Stefan Keileithner

[How to use Lottie \(In Chinese\)](https://goo.gl/e7BkND) by PattyDraw

[A Beginning’s Guide to Lottie: Creating Amazing Animations in iOS Apps](https://www.appcoda.com/lottie-beginner-guide/#) by Simon NG

[Take your animations to the next level with Airbnb framework, Lottie](https://medium.com/@jamesrochabrun/take-your-animations-to-the-next-level-with-airbnb-framework-lottie-ab6c6152acba) by James Rochabrun

[iOS Swift Tutorial: Animations with After Effects and Lottie](https://www.youtube.com/watch?v=ESjFEaZx7UI) by Brian Advent

[iOS Swift Tutorial: Interactive Animations with After Effects and Lottie](https://www.youtube.com/watch?v=QyL-jp9bFdM) by Brian Advent

[After Effects for wiOS Developers: Dynamic Content in Animations](https://youtu.be/2HhgLir6Jz0?list=PLUDTy1CWIw-qu2EuzNVFQawyW5jmC5W7G) by Brian Advent

[Creating cool animations in android using Lottie](https://www.youtube.com/watch?v=T4v72xJqNpQ)[Chetan Sachdeva](https://www.youtube.com/channel/UC_4TBWZcI-tdZ02wESTRVNw) by Chetan Sachdeva
