---
title: Google Cardboard for iOS 10分钟入门
date: 2017-05-05 14:40:46
tags: VR Cardboard iOS 
---
闲话不多说 直入正题 本文主要介绍的是Google Cardboard的sdk，最后你会完成一个可以观看360°照片和视频的简单应用。。我们暂且称它为Vacation 360.。

## 第一步准备工作
你可以从[这里下载](https://koenig-media.raywenderlich.com/uploads/2016/08/Vacation_360.zip)我已经为你们准备好的工程，打开Vacation 360.xcodeproj。在 **360 images** 文件夹下你会看到3张360°的全景图片。在 **Main.storyboard** 里，你会找到一个 **VacationViewController** 里面有一些label，两个空**UIView** 和 一些约束。
## 安装Google Cardboard VR SDK
如果你之前没用过 **cocoaPods** 的话，自行解决安装吧。。本文不在介绍，然后就是用cocoaPods 安装 Google Cardboard VR

打开**终端**进入你的工程Vacation_360目录下
`cd ~/ComputerLocation/Vaction_360`

然后，为你的工程创建一个 **Podfile** 文件
`pod init`

之后用文本编辑器或者vi打开刚刚创建的 **Podfile** 最后你的 **Podfile** 应该是这样的

```
target 'Vacation 360' do
  use_frameworks!
    pod 'GVRSDK'
end 
```
还差最后一步在 **Podfile** 这个目录下在 **终端** 执行
`pod install`

好了！这样你就完成了安装Google’s VR SDK。安装成功时你会看到终端日志里会输出这样一句话
“Please close any current Xcode sessions and use `Vacation 360.xcworkspace` for this project from now on.”
（！！！注意这一步也有可能安装不成功，原因就是请科学上网）

以后就应该打开 **.xcworkspace** 文件而不是 **.xcodeproj**了

因为 Google VR SDK 是一个用 Objective-C 写的 framework，而我们这个工程将会用最新版的 swift 来编写，所以我们需要一个 **Objective-C bridging header** 来让swift可以访问它。在菜单栏 **File\New\File...**, 选择 **iOS\Source\Header File** 之后点击 **Next**. 文件名为 **Vacation 360-Bridging-Header**，Group选择 **Vacation 360** 之后点击 **Create**

然后, 选择 **Vacation 360** 工程 在 **Project Navigator**, 选择在 **TARGETS** 下的 **Vacation 360**. 选择 **Build Settings**, 搜索 **Objective-C Bridging Header**  – 在后面的空白区域双击然后输入 **Vacation 360/Vacation 360-Bridging-Header.h**.

用下面的内容替换你的 **Vacation 360-Bridging-Header.h** 里的内容

```
#import "GVRPanoramaView.h"
#import "GVRWidgetView.h"
#import "GVRVideoView.h"
```
现在你就可以访问之后在工程里会用到的这三个 Google Cardboard VR SDK 类 .

## 接下来就是真正的coding了

```
enum Media {
  static var photoArray = ["sindhu_beach.jpg", "grand_canyon.jpg", "underwater.jpg"]
  static let videoURL = "https://s3.amazonaws.com/ray.wenderlich/elephant_safari.mp4"
}
```

设置初始的图片的视频在 **viewDidLoad()** 里添加如下代码 

```
imageVRView.load(UIImage(named: Media.photoArray.first!),
                            of: GVRPanoramaImageType.mono)
videoVRView.load(from: URL(string: Media.videoURL))
```


