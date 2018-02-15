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
* [先看教程](#%E5%85%88%E7%9C%8B%E6%95%99%E7%A8%8B)
* [复习与补充](#%E5%A4%8D%E4%B9%A0%E4%B8%8E%E8%A1%A5%E5%85%85)
* [导出无限循环的动画](#%E5%AF%BC%E5%87%BA%E6%97%A0%E9%99%90%E5%BE%AA%E7%8E%AF%E7%9A%84%E5%8A%A8%E7%94%BB)
* [你还可以尝试...](#%E4%BD%A0%E8%BF%98%E5%8F%AF%E4%BB%A5%E5%B0%9D%E8%AF%95)
* [异常处理](#%E5%BC%82%E5%B8%B8%E5%A4%84%E7%90%86)
* [注意事项](#%E6%B3%A8%E6%84%8F%E4%BA%8B%E9%A1%B9)
* [未解决的问题](#%E6%9C%AA%E8%A7%A3%E5%86%B3%E7%9A%84%E9%97%AE%E9%A2%98)
* [推荐](#%E6%8E%A8%E8%8D%90)
* [结尾](#%E7%BB%93%E5%B0%BE)

----

# 概述

写这篇文章的原因是，我之前答题跑偏了。

要导出无限循环的动画，一般来说都是想得到GIF动画；但如果仅仅是想让一段视频在另一段视频里循环播放个几百来次，就几乎不需要琢磨GIF那些东西，于是我把内容拆开了，写一写，试试看。

其实，网络上已经有许多关于“Ae 循环”的内容了，所以我会引用前辈们的各种教程，省下篇幅，再做补充说明。

<br/>

文中用到的视频素材来自：《[50帧又何妨（25FPS已重传）](https://www.bilibili.com/video/av9198307/)》

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

制作这段动画，我使用了[PluginEverything](https://videohive.net/user/plugineverything)出品的[Deep Glow](https://videohive.net/item/deep-glow/11008714)和[aescripts](https://aescripts.com/)出品的[AutoCircularMotion](https://aescripts.com/autocircularmotion/)；

经过调整，这段动画被制成了能够循环播放的GIF动图，但要注意，该动画的“循环”的实现，与接下来要介绍的方法关系不大。不过，它们所共有的思想，能指导你做出较高质量的循环动画。

----

# 先看教程

写了好一会儿，我发现用文字、图片、动画都不能将“循环”讲清楚，于是先来看教程：

* 通过剪辑与合成，做出循环播放的GIF动画

《[【中级】和我一起学AE 10\_野生技术协会\_科技\_bilibili\_哔哩哔哩](https://www.bilibili.com/video/av11696223/)》，来自[@龙子潇](http://www.zhihu.com/people/4a6f21a3bd3a67aa4594810cfaf3212e)：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-3919ed6694523337330ae4d95417fe74.jpg)

注意，这个教程在“导出GIF”那一块略过了一些要点，也有一些不正确的地方。关于导出GIF，可以查看我的文章《[知乎文章31567795《从Ae导出GIF的一些方法》](https://github.com/pzhlkj6612/ZhihuPost-31567795)》。

<br/>

* 使用表达式让元素的属性循环变化

在这里，“属性”指某个元素的`位置`、`缩放`、`不透明度`等等。

<br/>

首先可以看《[实用AE表达式推荐（二） - 知乎](https://zhuanlan.zhihu.com/p/27601294)》的“**六、LOOPIN&LOOPOUT**”节，做一个简单了解：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-5f3eb9884b90c5ae578a27bda9d7bad2.gif)

<br/>

接着，《[MG实用技巧：Loop循环表达式运用|平面|教程|D27\_ - 原创文章 - 站酷 (ZCOOL)](http://www.ui.cn/detail/163636.html)》：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-c6ca6839b3118279cea793169862bf99.gif)

顺便说一句，这个教程如果最终能够循环起来（一点点调整）就很好看了；

<br/>

如果前边的你都跟着做了，那么这里还有一个更高级的教程：《[AE 表达式应用——萤火虫-UI中国-专业用户体验设计平台](http://www.ui.cn/detail/163636.html)》：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-750dfafa2ad5253c04472bce903110a5.gif)

----

# 复习与补充

教程看完了，我来做一些补充。

<br/>

在上述的有关“表达式”的教程里，都是在对某些个很“具象”的属性的值（的关键帧）进行循环。那么时间呢？

就像文章概述里所说，你可能有这样的需求：“想让一段视频在另一段视频里循环播放个几百来次”，那么你就需要接触到“**[时间重映射](https://helpx.adobe.com/cn/after-effects/using/time-stretching-time-remapping.html#time_remapping)**”。

接下来，介绍两种“循环素材”和一种“循环合成”的方法：

* 对于素材的循环 - 解释素材

这是最简单的办法。先准备一段素材，不用创建合成，直接右键素材-`解释素材`-`主要`：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-c565a3b5271400dfaf56f6d02f3e197b.jpg)

在打开的`解释素材`对话框中，找到`其他选项`区域-`循环`，设置一个循环次数（1~9999），并单击`确定`：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-baa402e4fba36b0d0ae7b0f91549509e.jpg)

现在，你的素材的持续时间已经发生了变化。试着用调整过的素材创建合成并预览画面，就能发现已经有了循环的效果：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-66aaf9eedda33ba07e2f43ce6f0431be.jpg)

注意，图中的合成只有3小时长，因为[Ae最高只支持3小时长度的合成](https://helpx.adobe.com/cn/after-effects/using/composition-basics.html#composition_settings)，如果你需要更长时间的循环，就将合成裁剪好，导出Ae后再导入Pr，就可以从Pr里得到大于3小时的视频了。

<br/>

* 对于素材的循环 - 表达式

准备一段欲做循环效果的素材，将它放入一个合成中：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-727d2731f1910caf235a4355bcd876c7.jpg)

接着，右击代表那段素材的图层-`时间`-`启用时间重映射`（Ctrl+Alt+T），能看到该图层下方出现了属性`时间重映射`的两个关键帧，头尾各一个；而且图层的“时间范围”变为无限远：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-a294897861d6d8caede21452f6aa1cf1.jpg)

现在按住**Alt**，单击`时间重映射`前的秒表，调出表达式编辑器：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-3980046a8df79964374f86b4192c3bca.jpg)

单击“表达式语言菜单”（`表达式: 时间重映射`右侧的圆形白底指向右侧的黑色箭头）-`Property`-`LoopOut(Type = "cycle", numKeyframes = 0)`，
或者直接输入：
``` JavaScript
value = loopOut(Type = "cycle", numKeyframes = 0);
```

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-5773844420ff7dfef90cbea647340cbf.jpg)

现在，任意改变图层的持续时间并预览，就能够发现已经有循环播放的效果了：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-4a0b5a81771687c55cce66f37eba44ff.jpg)

最后，改变合成的工作区域，导出视频即可。

<br/>

* 对于合成的循环

循环合成的话，与循环素材的大体方法是一致的，但需要一些额外的操作。

先来看问题，你按照循环素材的方式去循环合成，可能会遇到：[循环空了一帧怎么消除【ae吧】\_百度贴吧](http://tieba.baidu.com/p/5307108102)，然后你再去找方法，可能会看到这样的说法：

> 先把他预合成!然后在添加时间重映射(在层菜单下的时间的第一个),再在动画结束处设置关键帧,把后面的关键帧删了,再按住AIT单击小马表图表添加关键帧在时间线窗口输入loop_out("cycle",0)这样就好了!

这是[求助 怎样让AE里的一个合成无限循环\_百度知道](https://zhidao.baidu.com/question/557190200523865692.html)里的一个回答，说得没错但是不那么具体，所以我在这里试着把它讲明白。

<br/>

拖一个合成到另一个更长的合成里，然后右击代表那段合成的图层-`时间`-`启用时间重映射`（Ctrl+Alt+T）：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-e686b88be0c84cac3939c28cf1cb3c3a.jpg)

现在你可以去看看尾部关键帧处的画面是什么：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-bc0a3a181240eeae764274eabe5f6a43.jpg)

空的？！往前一帧呢：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-d1e4504d3643f492d767077506fb9d4f.jpg)

如果你不管它，继续添加表达式，延长持续时间，你就会发现每到结尾时画面都会闪一下（空一帧），类似这样：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-0974ae16f5d5368d8ecb4ddff52898d8.gif)

<br/>

这种现象的原因我还不太清楚，但有规避问题的方法：

添加时间重映射后，你需要手动寻找你想循环的时间范围的出点，也就是循环里的结尾。一般情况下，你是想让那个合成整个循环起来，所以找到有画面的最后一帧（也就是有关键帧的前一帧）。然后，给这一帧打上关键帧（用秒表图标左侧那个“在当前时间添加或移除关键帧”），

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-92e3355ec94ee5aa13a794ec9307cc77.jpg)

再将后一帧的关键帧删掉，现在`时间重映射`属性仅有两个关键帧：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-344ef09abbe7077ecbb1b8cd0bbe9926.jpg)

现在按住**Alt**，单击`时间重映射`前的秒表，调出表达式编辑器，像之前那样添加`LoopOut`表达式，再延长图层持续时间，搞定。

----

# 导出无限循环的动画

如果你想导出GIF动画，就直接看我的[知乎文章31567795《从Ae导出GIF的一些方法》](https://github.com/pzhlkj6612/ZhihuPost-31567795)。

如果只是导出为一段视频，那就要记得Alpha通道的事情。因为你有可能需要有着透明背景的视频，所以需要使用支持RGB+Alpha的格式与编码器。

----

# 你还可以尝试...

* 将下边这两个教程里所做的东西制成流畅的、能够循环播放的GIF动画：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-9cf6b4e2915e592e8e0ac5f5f84cf332.jpg)

[【After Effects教程】干货实用AE实例教程合集【doyoudo出品】\(20\)\_野生技术协会\_科技\_bilibili\_哔哩哔哩](https://www.bilibili.com/video/av4612737/index_20.html#page=20)

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31568576/master/pic_zhimg_com/v2-2027ac109d1d600f8fba953c27e77921.jpg)

[【小莫讲AE】根本停不下来的旋转背景\_野生技术协会\_科技\_bilibili\_哔哩哔哩](https://www.bilibili.com/video/av12351097/)

----

# 异常处理

当出现“表达式错误”的提示时，请检查你所编写的代码：

* 是否错误地使用了全角符号；
* 是否少写了`.`、`""`、`()`、`[]`、`{}`等符号；

更多的还是请你去参考官方文档以及JS标准语法。

<br/>

# 注意事项

* Ae中的表达式并不是标准的JS，而是**J**ava**S**cript e**X**tension(JSX)，语法较为“宽松”，有一些代码可以省略不写；
* 但作为学习者，尽量还是完整地去写每一行代码。比如语句结束记得加分号；给属性赋值时带上`value =`。这些都是好习惯；
* 有了好习惯，一旦你要开始查错（Debug），或者读别人的代码，效率就会比较高了；
* 最后，学习英语、编程，益处很大。

<br/>

# 未解决的问题

* [The LoopMaker  - aescripts.com](https://aescripts.com/the-loopmaker/)是否好用？
* Ae中图层在时间轴内的“时间范围”角标，学名叫什么？
* [用AE做gif，粒子效果该怎么循环？ - 知乎](https://www.zhihu.com/question/60129024)
* 合成里的合成，为何时间重映射会空一帧出来？
* [`时间重映射`的快捷键是RR，添加或删除关键帧的快捷键是Alt+Shift+RR，这怎么按？](https://helpx.adobe.com/cn/after-effects/using/keyboard-shortcuts-reference.html#showing_properties_and_groups_in_the_timeline_panel_keyboard_shortcuts#showing_properties_and_groups_in_the_timeline_panel_keyboard_shortcuts)

----

# 推荐

* Ae表达式官方文档：[Expression language in After Effects](https://helpx.adobe.com/after-effects/using/expression-language-reference.html)
* 专栏推荐：[AE高手秘籍 - After Effects经验技巧干货汇总 - 知乎专栏](https://zhuanlan.zhihu.com/chuangying)
* 专栏推荐：[Motion Fun - 动效设计，AE脚本，Sketch插件 - 知乎专栏](https://zhuanlan.zhihu.com/motiondesigner)

<br/>

* JvanX的Duik骨骼绑定+GIF动画教程：《[\[MG动画教程\]财神循环动画制作\_野生技术协会\_科技_bilibili\_哔哩哔哩](https://www.bilibili.com/video/av3732099/)》
* 老鹰的MG教程：《[01【MG系列教学】MG动画一定要学的AE脚本-1\_野生技术协会\_科技\_bilibili\_哔哩哔哩](https://www.bilibili.com/video/av3386824/)》

<br/>

* 这里“有好多好多教程”：[doyoudo](http://doyoudo.com/)

<br/>

* JS入门教程：[JavaScript 教程 | 菜鸟教程](http://www.runoob.com/js/js-tutorial.html)
* 给Ae和C4D写脚本和插件的公司：[aescripts](https://aescripts.com/)
* 代码编辑器：[Sublime Text - A sophisticated text editor for code, markup and prose](https://www.sublimetext.com/)
* 开源社区：[GitHub](https://github.com/)

----

# 结尾

* 待更新的

暂无

<br/>

* 参考

[关于AE中进行循环动画的几种方法\_百度文库](https://wenku.baidu.com/view/d31d656daf1ffc4ffe47ac2e.html)

[How To Loop A Video In Adobe After Effects](https://www.surfacedstudio.com/blog/after-effects-how-to-loop-a-video)

[MG实用技巧：Loop循环表达式运用|平面|教程|D27\_ - 原创文章 - 站酷 \(ZCOOL\)](http://www.zcool.com.cn/article/ZMzk3OTM2.html)

[实用AE表达式推荐（二） - 知乎](https://zhuanlan.zhihu.com/p/27601294)

[AE循环的表达式是什么\_百度知道](https://zhidao.baidu.com/question/300528586.html)

[循环素材项目 - 在 After Effects 中使用素材项目](https://helpx.adobe.com/cn/after-effects/using/footage-items.html#loop_a_footage_item)

[求助 怎样让AE里的一个合成无限循环\_百度知道](https://zhidao.baidu.com/question/557190200523865692.html)

[After Effects 有什么技巧让你相见恨晚？ - 知乎](https://www.zhihu.com/question/28137864)

----

原答案发布于：2017.05.11

原答案修改于：2017.11.30

<br/>

修改于：24:68 2018/13/57

禁止转载。
