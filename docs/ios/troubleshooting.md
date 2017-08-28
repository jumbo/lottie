# 解决问题
有时Lottie并不能正确渲染动画，这是因为After Effects有许多的特性，而这些特性并未被Lottie完整支持。当动画播放不正常时，请按照以下步骤检查。

## 查看特性支持页面
查看 [特性支持页面](/supported-features.md) 是否用了尚未支持的特性。

## 调试日志
LOTHelpers.h 中有两个调试标记，ENABLE\_DEBUG\_LOGGING 和 ENABLE\_DEBUG\_SHAPES。ENABLE\_DEBUG\_LOGGING 是加强的Lottie日志，包含动画过程中动画节点被设置的任意时间点。如果动画工作不正常，请打开该功能播放动画，控制台日志将告诉你发生了什么。

ENABLE\_DEBUG\_SHAPES 为每个图层和形状绘制带有颜色的方形区域，这将有助于查找问题。

## 找到根本问题
尝试渲染动画中的独立部件，看看是否正常运行。这样可以将问题缩减到一些特定形状，而不只是“看起来不对”。如果某些特性本应支持却出了问题，请提交issue给项目成员，顺带 aep 项目文件。
