## 视频PS神器！人物隐身、水印去除，简直像重拍了一遍，这项登上CVPR的研究刚刚开源了

原创： 关注前沿科技 [量子位](javascript:void(0);) *今天*

##### 鬼栗子 郭一璞 发自 凹非寺  量子位 报道 | 公众号 QbitAI

让一个人的踪影从视频中消失，总是一个难题。

毕竟，你永远不知道，录好的节目里，哪个明星艺人会突然翻车，形象大跌，后期团队被迫紧急加班，用各种方式掩盖他们的痕迹。

比如，某卫视春晚，强行让一位背上骂名的主持人消失：

![img](https://mmbiz.qpic.cn/mmbiz_jpg/YicUhk5aAGtAjFCRqqjVo7YVQ2oFibGI3Fqt1ibLJra86ibzQw2HpleIJAts87FEj6gQwHiaCmFkE31tolenvsn0UPg/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

以及某综艺节目，把言行不当的艺人改成了卡通人物：

![img](https://mmbiz.qpic.cn/mmbiz_gif/YicUhk5aAGtAjFCRqqjVo7YVQ2oFibGI3F3WCvodTQ6k3jH1jhz8chiaoNmia4ScUcs1z7O8gXPIbV0u4tTMqyBiaXQ/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

要是有个AI，能一键把这些人物都删掉，还让观众看不出纰漏就好了。

现在，一项CVPR 2019上的研究，让这个需求变成了现实。

拿**美队3**举个例子，机场大战中，飞舞的红色小人就是被标记出来的蜘蛛侠，他正在用蜘蛛丝把蚁人绑起来。

![img](https://mmbiz.qpic.cn/mmbiz_gif/YicUhk5aAGtAYhdO7PS1DCFRc4ibic7sicPHkqcS5D9ib1kg3TrxOIialRdZ6XSMTq9ON7zdIQS6icDdkue5uEEWZ7AFQ/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

现在，AI出马，蜘蛛侠不见了，留下蚁人独自被被蜘蛛丝捆绑纠缠，仿佛这些蜘蛛丝拥有了自动捆绑功能。

![img](https://mmbiz.qpic.cn/mmbiz_gif/YicUhk5aAGtAYhdO7PS1DCFRc4ibic7sicPH8gw681VeFne3QXUULtoce17aU7NiaibA8tVoCYibAdU8NaeHAYcAibHQWg/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

再比如，《疯狂动物城》里的兔兔朱迪，也被用红色标注了。它本来在冰面上奔跑，爬上冰山，耐不住滑溜溜的冰面，掉进了水里。

![img](https://mmbiz.qpic.cn/mmbiz_gif/YicUhk5aAGtAYhdO7PS1DCFRc4ibic7sicPHVuo19vnGYE4zD9wPvTyib4sEuiceFYUedAFkibrFjIoeB6fao7PMZYnlQ/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

在AI出手之后，朱迪就免去了爬冰之苦，镜头里只有他留在冰面上的影子。

原本人物的位置，被修复的非常完美，压根看不出来曾经有只兔兔被抠了出去，就好像电影的动画团队把这个镜头重新做了一遍。

![img](https://mmbiz.qpic.cn/mmbiz_gif/YicUhk5aAGtAYhdO7PS1DCFRc4ibic7sicPHicBFdkpH00gUazkfOYDxtibhBRx61yEH2rDAicELSK5HYBQvJfdYRJbDg/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

看到这样的效果，不知道上面那两部节目的后期会不会哭晕：长期加班搞出来的效果，别人家的AI就自动完成了，而且毫无违和感，让人物消失的无影无踪。

另外，估计拍vlog的视频播主们也会开心的不行：再也不担心网红打卡地遍地都是人了，直接用AI删掉多方便！

###### 

背后的AI，是名叫**光流引导** (Flow-Guided) 的视频修复算法。它主要来自商汤港中大联合实验室和商汤南洋理工联合实验室，有周博磊大神参与，中选了**CVPR 2019**。

GitHub预告链接放出许久之后，这项研究的代码，**刚刚开源**。

而在放出之前，也已经有245位GitHub用户标了星，翘首以待。

![img](https://mmbiz.qpic.cn/mmbiz_jpg/YicUhk5aAGtAYhdO7PS1DCFRc4ibic7sicPHxzj5Io5pOYsn3vYVAMXoABGHchsKFqIha7nFGvnDkbIW8gjiaEst5Ww/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

那么问题来了，在一片热闹的景象里，抹掉一个剧烈运动的人物，怎么会这般轻松自如？

## 追光者

就像开头提到的那样，隐身术是用**光流** (Optical Flow) 炼成的。

所谓光流，视觉上长这样：

![img](https://mmbiz.qpic.cn/mmbiz_gif/YicUhk5aAGtAYhdO7PS1DCFRc4ibic7sicPHECzROKSNpbTKL9Nq0qgmbP7rgIWuL9PzBnXicX0bJibrMBm7aCy39dQA/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

###### **△** 左边是遮挡版，右边是AI补全版

事实上，它是描述物体运动情况的一个概念，James Gibson在1950年就提出了：

指的是空间运动的物体在观察平面上，像素运动的**瞬时速度**。观察者嘛，可以是人类的肉眼，也可以是摄像机。

在摄像机拍下的视频里，帧与帧之间是有时间顺序的，这样就可以从相邻两帧之间算出光流，那就是物体的运动信息。

学到这样的信息，可以用来做目标检测，也可以用来修改视频。

团队开发了一个两步的算法：

**第一步，估计光流。第二步，用光流来指导修复。**

![img](https://mmbiz.qpic.cn/mmbiz_png/YicUhk5aAGtAYhdO7PS1DCFRc4ibic7sicPHw7KqACPyboL0VwGBpNk7KZyg9a0jTwzX5jUmppO0PtYsxc0NvxFcbQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

###### **△** 上为第一步，下为第二步

现在，把这两步拆解一下。

**第一步**，光流估计，把视频上的某个部分挡住，AI要把这一部分的光流补充完整。

比如，下图的红色就是遮挡部分。

![img](https://mmbiz.qpic.cn/mmbiz_gif/YicUhk5aAGtAYhdO7PS1DCFRc4ibic7sicPHibB9osj0QlticZR0tHFibmHTeFib9Nv9NKLBe85690ibZAgOQvwjJnCPE8A/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

团队设计了一个叫做**DFC-Net**的网络，学着把不完整的光流补充完整。

而在AI的训练数据里，遮挡是随机生成的，对照完整的视频来学习：

![img](https://mmbiz.qpic.cn/mmbiz_jpg/YicUhk5aAGtAYhdO7PS1DCFRc4ibic7sicPH8LAPTH7STtQ0yufPUnaZbcKlJDicNfAeQ63Eje9jGD1vtxDbvm4oRBA/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

左边是随机遮挡；右边是遮挡之后 (用简单填充算法初始化得到) 的光流，等待补全；中间是标答。

DFC-Net有**三个子网络**。第一个子网络，负责在一个粗糙尺度上补全光流；把结果交给第二个子网络，细化一下。再交给第三个网络，进一步细化：

![img](https://mmbiz.qpic.cn/mmbiz_png/YicUhk5aAGtAYhdO7PS1DCFRc4ibic7sicPHU71Eag8W1U6q1ianNcHBw2ib30iavBweicSGuor3JAoMMNPTrnSu1hm3rw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

这样，就有了最终的光流补全结果。

**第二步**，就该根据光流来修复视频了。

原理是，某一帧里被遮挡的信息，在其他帧里可能是存在的。根据光流提供的运动信息，就可以用其他帧里的已知像素，来填补当前帧的未知像素了。

当然，还有一些信息，整段视频都没显示。这一部分，就要靠传统图像修复网络**Deepfill**来脑补了。

讲完原理，来全方位观察一下，算法的功效究竟如何。

## 完美消失的马术选手

新的方法怎样，要和优秀的前辈比一场才知道。

对手有两位，一是来自CVPR 2018的**Deepfill**，二是**Huang et al**出品、中选SIGGRAPH 2016的算法。

这是第一题，把马术选手和ta的马，从视频里面抹掉：

![img](https://mmbiz.qpic.cn/mmbiz_gif/YicUhk5aAGtAYhdO7PS1DCFRc4ibic7sicPHSNbj94R12N78BXDsBfh1oAEIny3mRtgBSssErQ6YADBaIgzwrFCnyA/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

Deepfill (右上) 单靠脑补，马的痕迹十分明显；Huang et al (左下) 自然了许多，但依然有些灰蒙蒙的残留；相比之下，新算法修过的视频，只留下了地上的影子。

还有第二题，把轮滑妹子面前的水印去掉：

![img](https://mmbiz.qpic.cn/mmbiz_gif/YicUhk5aAGtAYhdO7PS1DCFRc4ibic7sicPHA91cSdQGgRZ9h3WFFia68RuOcQCpBHP6yvbHYPKq6tianzHOVLvKlQkw/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

下面是**Huang et al**前辈的结果，当妹子跳过水印原本的位置，依然看得出不少灰色的污迹：

![img](https://mmbiz.qpic.cn/mmbiz_gif/YicUhk5aAGtAYhdO7PS1DCFRc4ibic7sicPH4ic5Y7iaURBlSdBwGeCEjiawulcw54GYCXia9icGNTaeGCZVarIEoLqksJw/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

而本文主角修复的结果，几乎看不出视频曾经有过水印：

![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

当然，不止是肉眼观察的结果，这只新的AI在YouTube-VOS和DAVIS两大数据集上，得分都比前辈更胜一筹：

![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

另外，研究者们还找了30名吃瓜群众，仔细测试人类的观感。

首先在**目标移除方面**，将近80%的用户认为第一名应当是这项研究 (蓝色部分) 。

![img](https://mmbiz.qpic.cn/mmbiz_png/YicUhk5aAGtDcoW5mHVI2QiajesWb2cKONqYds8lYWGAHtn2ibLibqeyQjNwWWk9a5NDTtJKhGJ3smfQ3iaHcgcXXtQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

而在**背景填充方面**，也有近七成用户认为这项研究的填充效果是最好的。

![img](https://mmbiz.qpic.cn/mmbiz_png/YicUhk5aAGtDcoW5mHVI2QiajesWb2cKONsKdICSJrZrmFC5RJKAIGUz79F5F0QZNETU0mxMZdHibf7FrGzUnwkXA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

## 港中大&商汤联合出品

研究人员中，有三位来自港中大商汤联合实验室，一位来自南洋理工大学。

一作徐瑞和二作李晓潇都是港中大商汤联合实验室的博士，李晓潇曾在分别在2017年和2018年的DAVIS Challenge on Video Object Segmentation赢得了冠军和亚军。

![img](https://mmbiz.qpic.cn/mmbiz_jpg/YicUhk5aAGtDcoW5mHVI2QiajesWb2cKONQu3WhJPlMkjaX9ltlibr9vzRJ96gePeAYdMXliaeP2bEcQjYF5a3ogBw/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

第三位作者周博磊目前是港中大信息工程系助理教授，他去年刚从MIT博士毕业，现在h-index就高达25了，曾获得MSRA和Facebook的奖金。

Places2和ADE20K两个数据集都是他参与的作品，Network Dissection和Class Activation Mapping也是他的代表作品。

![img](https://mmbiz.qpic.cn/mmbiz_jpg/YicUhk5aAGtDcoW5mHVI2QiajesWb2cKONM47TIG7ibRyMupD5RvNEU7H7rl7f2RyicSNRYr9aY4PuM8pibIrVlONUg/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

最后一位作者吕健勤（Chen Change Loy），博士毕业于伦敦玛丽女王大学，现在是南洋理工大学计算机科学与工程学院的副教授，他同时还是港中大的客座副教授，此前也一直在港中大多媒体实验室任教。

吕健勤教授带领团队进行了许多和计算机视觉、图像处理相关的研究。近两年，他还在CVPR 2019、BMVC 2019、ECCV 2018和BMVC 2018几场顶会担任区域主席，他也是IJCV杂志副主编。

## 一个彩蛋

你看，刻苦练习之后，身为一只兔子的朱迪，用优秀的弹跳能力弥补了身高劣势，反超队友：

![img](https://mmbiz.qpic.cn/mmbiz_gif/YicUhk5aAGtAYhdO7PS1DCFRc4ibic7sicPHHYdQcc1g5YRmnaOVyYaQjBGt3zoEMoIfItVZKvv4701uNibp8TYmoicg/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

但实力还是可以隐藏的，于是她又把自己融进了雪水：

![img](https://mmbiz.qpic.cn/mmbiz_gif/YicUhk5aAGtAYhdO7PS1DCFRc4ibic7sicPHGiaDibhjjic4eUxr96aicQI2CsFDHRTNppvriaNHNR9wicG5uiakZSRP3sdmA/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

论文：

**Deep Flow-Guided Video Inpainting**
Rui Xu, Xiaoxiao Li, Bolei Zhou, Chen Change Loy
https://arxiv.org/abs/1905.02884

项目主页：
https://nbei.github.io/video-inpainting.html

开源代码：
https://github.com/nbei/Deep-Flow-Guided-Video-Inpainting



— **完** —

**AI社群 | 与优秀的人交流**



![img](https://mmbiz.qpic.cn/mmbiz_png/YicUhk5aAGtCEFSVW5ubo08Zfv1qB5iaprbZUlsy5odkbQRwlnJ4gYccCB4iaR89q8zdvoc9CEDlR3ORTzdicyLI5g/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



**AI内参 | 关注行业发展**

![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)



**量子位** QbitAI · 头条号签约作者





վ'ᴗ' ի 追踪AI技术和产品新动态



喜欢就点「在看」吧 ! 













微信扫一扫
关注该公众号