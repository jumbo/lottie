# 为运行中的动画添加视图

Lottie 除了支持[运行中修改动画](/ios/dynamic.md)，还可以为 LOTAnimation 运行时添加自定义UI。
以下示例展示了创建一个动态图片loader

## 动态图片加载动画

![Spinner](/images/spinner.gif)

上面的示例展示的是单个加载动画，动画在异步下载图片时循环播放其一部分，当下载完成，图片被加入动画中，并连贯的播放其余部分。整个过程干净利落，最后呼叫一个动画完成脚本。

![Spinner_Alt](/images/spinner_Alternative.gif)

现在，动画被另一位设计师修改了，需要更新一下。 所需的全部工作仅仅是更新之前打包的JSON文件，其他代码完全不用修改。

![Spinner_Dark](/images/spinner_DarkMode.gif)

App 加入了一个 暗色主题，仅需修改一点代码，在动画运行时改变其颜色即可。


是不是很强大?

查看以下示例代码：
After Effects 文件 [下载](/AEP/LoadingSpinner.zip)

```swift

import UIKit
import Lottie

class ViewController: UIViewController {

  var animationView: LOTAnimationView = LOTAnimationView(name: "SpinnerSpin");

  override func viewDidLoad() {
    super.viewDidLoad()

    // Setup our animaiton view
    animationView.contentMode = .scaleAspectFill
    animationView.frame = CGRect(x: 20, y: 20, width: 200, height: 200)

    self.view.addSubview(animationView)
    // Lets change some of the properties of the animation
    // We arent going to use the MaskLayer, so lets just hide it
    animationView.setValue(0, forKeypath: "MaskLayer.Ellipse 1.Transform.Opacity", atFrame: 0)
    // All of the strokes and fills are white, lets make them DarkGrey
    animationView.setValue(UIColor.darkGray, forKeypath: "OuterRing.Stroke.Color", atFrame: 0)
    animationView.setValue(UIColor.darkGray, forKeypath: "InnerRing.Stroke.Color", atFrame: 0)
    animationView.setValue(UIColor.darkGray, forKeypath: "InnerRing.Fill.Color", atFrame: 0)

    // Lets turn looping on, since we want it to repeat while the image is 'Downloading'
    animationView.loopAnimation = true
    // Now play from 0 to 0.5 progress and loop indefinitely.
    animationView.play(fromProgress: 0, toProgress: 0.5, withCompletion: nil)

    // Lets simulate a download that finishes in 4 seconds.
    let dispatchTime = DispatchTime.now() + 4.0
    DispatchQueue.main.asyncAfter(deadline: dispatchTime) {
      self.simulateImageDownloaded()
    }
  }

  func simulateImageDownloaded() {
    // Our downloaded image
    let image = UIImage(named: "avatar.jpg")
    let imageView = UIImageView(image: image)

    // We want the image to show up centered in the animation view at 150Px150P
    // Convert that rect to the animations coordinate space
    // The origin is set to -75, -75 because the origin is centered in the animation view
    let imageRect = animationView.convert(CGRect(x: -75, y: -75, width: 150, height: 150), toLayerNamed: nil)

    // Setup our image view with the rect and add rounded corners
    imageView.frame = imageRect
    imageView.layer.masksToBounds = true
    imageView.layer.cornerRadius = imageRect.width / 2;

    // Now we set the completion block on the currently running animation
    animationView.completionBlock = { (result: Bool) in ()
      // Add the image view to the layer named "TransformLayer"
      self.animationView.addSubview(imageView, toLayerNamed: "TransformLayer", applyTransform: true)
      // Now play the last half of the animation
      self.animationView.play(fromProgress: 0.5, toProgress: 1, withCompletion: { (complete: Bool) in
        // Now the animation has finished and our image is displayed on screen
        print("Image Downloaded and Displayed")
      })
    }

    // Turn looping off. Once the current loop finishes the animation will stop
    // and the completion block will be called.
    animationView.loopAnimation = false
  }

}

```
