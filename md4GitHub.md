![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-ed5f3ea5b4503c6af2ea19a75dba2db9.jpg)

禁止转载。

禁止转载是指“禁止转载本文内容”，可以通过超链接的方式分享本文。

<br/>

本文章内容由我的这个回答处理而来：

[https://www.zhihu.com/question/58159898/answer/167682476](https://www.zhihu.com/question/58159898/answer/167682476)

本文章也存在于GitHub仓库：

[https://github.com/pzhlkj6612/ZhihuPost-31568576](https://github.com/pzhlkj6612/ZhihuPost-31568576)

<br/>

注意：

* 本文可能不会持续更新；
* 我仅在`Windows 10`下的`Adobe After Effects CC2015.3/CC2017`对本文内容做了简要测试；
* 所有方法均由我从各个地方习得并测试，仅供参考，并不一定是最佳选择；
* 本文并不适合在小屏幕终端上阅读；
* 以下内容有难度，请你务必耐心；
* 有问题请及时指出。

----

# 目录

* [概述](#%E6%A6%82%E8%BF%B0)
* [可以用循环做什么](#%E5%8F%AF%E4%BB%A5%E7%94%A8%E5%BE%AA%E7%8E%AF%E5%81%9A%E4%BB%80%E4%B9%88)
* 先看教程
* [在Ae里循环](#%E5%9C%A8ae%E9%87%8C%E5%BE%AA%E7%8E%AF)
* [导出](#%E5%AF%BC%E5%87%BA)
* [异常处理](#%E5%BC%82%E5%B8%B8%E5%A4%84%E7%90%86)
* [注意事项](#%E6%B3%A8%E6%84%8F%E4%BA%8B%E9%A1%B9)
* [未解决的问题](#%E6%9C%AA%E8%A7%A3%E5%86%B3%E7%9A%84%E9%97%AE%E9%A2%98)
* [推荐](#%E6%8E%A8%E8%8D%90)
* [结尾](#%E7%BB%93%E5%B0%BE)

----

# 概述

写这篇文章的原因是，我之前答题跑偏了。

我发现：要导出无限循环的动画，最终想得到的极大可能会是GIF动画；但如果仅仅是想让一段素材在另一段素材里循环播放个几百来次，又几乎不需要琢磨GIF相关的东西，于是把内容拆开了，写一写，试试看。

其实，网络上已经有许多关于“Ae 循环”的内容了，所以我会引用前辈们的各种教程，省下篇幅，讲清原理。

<br/>

文中用到的视频素材来自：《[【大花豹】极乐净土](https://www.bilibili.com/video/av10397269/)》《[50帧又何妨（25FPS已重传）](https://www.bilibili.com/video/av9198307/)》

----

# 可以用循环做什么

比如：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-785b9198f9bc33fa7f569b1df1ab756c.jpg)

《[【雷军/初音】New Friend\_鬼畜调教\_鬼畜\_bilibili\_哔哩哔哩](https://www.bilibili.com/video/av8530045/)》

其中的：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-1c9f49b2bbdba79183268c792aeabd09.gif)

<br/>

再比如：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-f03e4fad7249035dc2410a6a89630267.gif)

这段动画，在制作时使用了[PluginEverything](https://videohive.net/user/plugineverything)出品的[Deep Glow](https://videohive.net/item/deep-glow/11008714)和[aescripts](https://aescripts.com/)出品的[AutoCircularMotion](https://aescripts.com/autocircularmotion/)；

经过调整，这段动画被制成了循环播放的GIF动图，但要注意，该动画的“循环”的实现，与接下来要介绍的方法关系不大。不过，它们之间所共有的思想，能指导你做出较高质量的循环动画。

----

# 先看教程

写了好一会儿，我发现用文字、图片、动画都不能将“循环”讲清楚，于是先来看教程：

* 通过剪辑与合成，做出循环播放的GIF动画

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-3919ed6694523337330ae4d95417fe74.jpg)

《[【中级】和我一起学AE 10\_野生技术协会\_科技\_bilibili\_哔哩哔哩](https://www.bilibili.com/video/av11696223/)》，来自[@龙子潇](http://www.zhihu.com/people/4a6f21a3bd3a67aa4594810cfaf3212e)。

注意，这个教程在“导出GIF”那一块略过了一些要点，也有一些不正确的地方。关于导出GIF，可以查看我的文章《[知乎文章31567795《从Ae导出GIF的一些方法》](https://github.com/pzhlkj6612/ZhihuPost-31567795)》。

<br/>

* 使用表达式让元素的属性循环变化

在这里，属性指某个元素的“位置”、“缩放”、“不透明度”等等。

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-5f3eb9884b90c5ae578a27bda9d7bad2.gif)

首先可以看《[实用AE表达式推荐（二） - 知乎](https://zhuanlan.zhihu.com/p/27601294)》的“六、LOOPIN&LOOPOUT”节，做一个简单了解；

<br/>

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-c6ca6839b3118279cea793169862bf99.gif)

接着，《[MG实用技巧：Loop循环表达式运用|平面|教程|D27\_ - 原创文章 - 站酷 (ZCOOL)](http://www.ui.cn/detail/163636.html)》。这个教程如果最终能够循环起来（一点点调整）就很好看了；

<br/>

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-750dfafa2ad5253c04472bce903110a5.gif)

如果前边的你都跟着做了，那么这里还有一个更高级的教程：《[AE 表达式应用——萤火虫-UI中国-专业用户体验设计平台](http://www.ui.cn/detail/163636.html)》。

----

# 在Ae里循环

* 时间重映射+表达式 让一段素材在合成里循环





----

# 导出

----

# 异常处理

<br/>

# 注意事项

<br/>

# 未解决的问题

----

# 推荐

----

# 结尾

* 待更新的

<br/>

* 参考

[关于AE中进行循环动画的几种方法_百度文库](https://wenku.baidu.com/view/d31d656daf1ffc4ffe47ac2e.html)

[How To Loop A Video In Adobe After Effects](https://www.surfacedstudio.com/blog/after-effects-how-to-loop-a-video)

[MG实用技巧：Loop循环表达式运用|平面|教程|D27\_ - 原创文章 - 站酷 \(ZCOOL\)](http://www.zcool.com.cn/article/ZMzk3OTM2.html)

[实用AE表达式推荐（二） - 知乎](https://zhuanlan.zhihu.com/p/27601294)

[AE循环的表达式是什么_百度知道](https://zhidao.baidu.com/question/300528586.html)

[求助 怎样让AE里的一个合成无限循环_百度知道](https://zhidao.baidu.com/question/557190200523865692.html)

[After Effects 有什么技巧让你相见恨晚？ - 知乎](https://www.zhihu.com/question/28137864)

----

原答案发布于：2017.05.11

原答案修改于：2017.11.30

<br/>

修改于：24:68 2018/13/57

禁止转载。
