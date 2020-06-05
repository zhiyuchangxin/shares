title: 骨骼动画——DragonBones
speaker: zhiyuchangxin
utl: https://github.com/zhiyuchangxin/shares
transition: slide2
files: /css/skeleton.css
theme: dark
date: 2020-06-05


[slide style="background-image: url('/img/bg23.png')"]
# 骨骼动画——DragonBones
----
<img src="/img/dragonbones.png" class="index-img">
<p style="color:#111;font-weight:600;">@织语长心&nbsp;&nbsp;2020-06-05</p>


[slide style="background-image: url('/img/bg24.png')"]
## 知识点
----
- 骨骼动画的原理 {:&.moveIn}
    - 骨骼动画的概念 {:&.fadeIn}
    - 骨骼动画的组成
    - 骨骼动画的优缺点
- CSS 实现骨骼动画
- DragonBones 实现骨骼动画
    - DragonBones 简介 {:&.fadeIn}
    - 选择 DragonBones 的原因
    - H5 游戏引擎深度测评
    - DragonBones 实现动画
- 骨骼动画的应用


[slide style="background-image: url('/img/bg24.png')"]
<span class="theme-tag">&middot;骨骼动画原理</span>
## 骨骼动画的概念
----
- 「骨骼动画」就是模拟**骨骼运动**机制而制作的动画 {:&.moveIn}
- 「骨骼动画」不是一种动画制作形式，而是一种制作**手段**
    - “帧动画”和“Tween动画”是动画制作形式
    - “骨骼动画”是动画制作手段
- 「骨骼动画」是一种通过**控制骨骼参数**来实现多帧动画的方式
<br>
<br>
> 1.当一些动画的构成和变形非常复杂时，尽管动画本质上是这些点在空间内做位移构成的，但直接驱动这些点非人力能为；
> 2.因此我们把运动简化成骨骼来代表，并把点一一映射到骨骼上；


[slide style="background-image: url('/img/bg24.png')"]
<span class="theme-tag">&middot;骨骼动画原理</span>
## 骨骼的组装结构
----
- 骨骼是以**树**状结构组织起来 {:&.moveIn}
<img src="http://img.alicdn.com/tps/TB17XvsKFXXXXXoXXXXXXXXXXXX-500-400.png" class="skeleton-tree">
- 每片骨骼都需要描述自身的变换参数：
    - 位移（x，y）
    - 旋转角度（θ）
    - 骨骼的位移和角度是「相对父骨骼坐标系」而非「全局」而言的 


[slide style="background-image: url('/img/bg24.png')"]
<span class="theme-tag">&middot;骨骼动画原理</span>
## 骨骼动画的元素
----
- 骨架（Armature）：骨骼的集合（骨架中至少包含一个骨骼） {:&.moveIn}
- 骨骼（Bone）：骨骼动画的基本组成部分
    - 骨骼之间存在父子关系，父亲的变换会影响到孩子 {:&.fadeIn}
    - 一般通过骨骼的旋转、缩放、平移等变换即可形成动画
- 插槽（Slot）：图片的容器，是骨骼和图片的桥梁
    - 一根骨骼可以挂载多个插槽 {:&.fadeIn}
    - 骨骼可被视作插槽的父节点，骨骼的变换会影响插槽
- 显示对象（DisplayData）：显示对象通常为图片
    - 一个插槽中可以有多个显示对象，但同时只会有一个被显示 {:&.fadeIn}
    - 通过修改当前显示的对象可以形成帧动画
- 装配（Rigging）：构成骨骼的过程
- 蒙皮（Skinning）：把点映射到骨骼上的过程


[slide style="background-image: url('/img/bg24.png')"]
<span class="theme-tag">&middot;骨骼动画原理</span>
## 骨骼动画的优缺点
----
- 优点 {:&.moveIn}
    - 区别于 GIF 的不连贯和序列帧的体积大，骨骼动画有较好的**灵活性**和**流畅性**，动画更加生动逼真 {:&.fadeIn}
    - 图片资源占最**小**的存储空间，骨骼动画的图片容量可以减少90%
    - 动画切换**自动补间**，过渡更加灵动
    - **骨骼可控**（可对特定骨骼做特殊控制或监听骨骼事件帧...）
    - 动作数据继承，多角色可**共用**一套动画数据
-  缺点：比传统的逐帧动画要求**更高的处理器性能**


[slide style="background-image: url('/img/bg24.png')"]
## CSS 实现骨骼动画
----
<a href="javascript:void(0);" target="_blank" style="">DEMO:祈福牌</a>
<a href="javascript:void(0);" target="_blank" style="">DEMO:跑步</a>


[slide style="background-image: url('/img/bg24.png')"]
## DragonBones 实现骨骼动画
----


[slide style="background-image: url('/img/bg24.png')"]
<span class="theme-tag">&middot;DragonBones 实现骨骼动画</span>
## DragonBones 简介
----
- **2D**骨骼动画解决方案 {:&.moveIn}
- **开源**、**跨平台**、**免费**
- 打通游戏动画**设计**和**开发**工作流
    - 方便了设计师在软件中的操作和编辑
    - 方便开发者使用这份数据来播放精灵动画
- 支持将动画数据**导出为 JSON**格式


[slide style="background-image: url('/img/bg24.png')"]
<span class="theme-tag">&middot;DragonBones 实现骨骼动画</span>
## 选择 DragonBones 的原因
----

|  名称   | 介绍 | 导出格式 | 收费情况 | 其他 |
|  ----  | ----  |  ----  | ----  | ----  | 
| DragonBones | 白鹭时代推出的2D骨骼动画解决方案 | 支持JSON  | 免费 | - |
| Spine | 针对游戏开发的2D骨骼动画编辑工具 | 支持JSON | 收费 | - |
| 万彩骨骼大师 | 专门制作2D动画人物/角色的软件 | 不支持JSON | 免费 | 限windows系统 |

<br>
- 免费的才是最受欢迎的（虽然据说 Spine 比 dragonBones 更强大） {:&.moveIn}
- 支持 JSON 格式提高动画的还原度（消除买家秀与卖家秀落差）


[slide style="background-image: url('/img/bg24.png')"]
[note]
测评结果:
1. Three.js 定位：JS 语言的 **3D库** 
2. Pixi.js 定位：依赖于 canvas 的 WebGL **2D渲染器**
    - 把渲染性能做到极致，成为其他引擎的渲染内核
    - API设计上更加参考非常成熟的2D渲染架构 —— Flash，并且提供的API也尽量参考了AS
3. Phaser 定位：桌面与移动端的 H5 游戏**框架**
    - Phaser并没有自己的渲染内核，而是直接引用了 Pixi.js
4. Egret 定位：游戏解决方案

[/note]
<span class="theme-tag">&middot;DragonBones 实现骨骼动画</span>
## H5 游戏引擎深度测评
----
<img src="/img/h5-compare.png" class="h5-compare">


[slide style="background-image: url('/img/bg24.png')"]
<span class="theme-tag">&middot;DragonBones 实现骨骼动画</span>
## DragonBones 使用
----
<p style="text-align:left;">主要分为两大阶段：</p>
- 资源创作阶段：生成程序可以使用的 DragonBones 资源 {:&.moveIn}
- 程序使用阶段：对骨骼动画库进行各种调用及组合，产生丰富而生动的游戏动作画面


[slide style="background-image: url('/img/bg24.png')"]
<span class="theme-tag">&middot;DragonBones 实现骨骼动画</span>
## DragonBones 实现动画——JSON数据分析
----
了解导出JSON数据的内容：[数据格式说明](http://developer.egret.com/cn/github/egret-docs/DB/dbLibs/5foramt/index.html)


[slide style="background-image: url('/img/bg24.png')"]
<span class="theme-tag">&middot;DragonBones 实现骨骼动画</span>
## DragonBones 实现动画——创建骨骼动画
----
- 载入数据 {:&.moveIn}
- 解析数据：parseDragonBonesData、parseTextureAtlasData
- 提取骨架系统：armatureDisplay = factory.buildArmatureDisplay('armatureName');
- 播放动画：armatureDisplay.animation.play('animationName');
- 将骨架添加到舞台：addChild(armatureDisplay);

<a href="javascript:void(0);" target="_blank" style="">DEMO:傲娇公鸡</a> {:&.moveIn}

[slide style="background-image: url('/img/bg24.png')"]
<span class="theme-tag">&middot;DragonBones 实现骨骼动画</span>
## DragonBones 实现动画——创建骨骼动画code
----
<img src="/img/skeleton-code1.png" class="h5-compare">


[slide style="background-image: url('/img/bg24.png')"]
<span class="theme-tag">&middot;DragonBones 实现骨骼动画</span>
## DragonBones 实现动画——多角色动画
----
- DragonBones 系统允许创建多个骨骼动画 {:&.moveIn}
- 可以创建多个 Factory 来管理不同的骨骼动画
- 也可使用同一个 Factory 来管理多个骨骼动画
- 当使用一个 Factory 时，需注意避免龙骨数据/骨架数据重名
- 如没有特殊需求，建议使用一个 Factory 实例

<a href="javascript:void(0);" target="_blank" style="">DEMO:2只傲娇公鸡</a> {:&.moveIn}


[slide style="background-image: url('/img/bg24.png')"]
<span class="theme-tag">&middot;DragonBones 实现骨骼动画</span>
## DragonBones 实现动画——多角色动画code
----
<img src="/img/skeleton-code2.png" class="h5-compare">


[slide style="background-image: url('/img/bg24.png')"]
<span class="theme-tag">&middot;DragonBones 实现骨骼动画</span>
## DragonBones 实现动画——其他常用
----
- 控制骨骼运动：getBone() 获取骨骼后变换 {:&.moveIn}
- 改变动画速度：timeScale
- 动画混合：fadeIn
    - 一个骨架同时可以播放多个动画（eg：角色同时播放跑步和开火的动画）
- 动画遮罩：addBoneMask
    - 只将动画的一部分呈现出来（eg：只播放head和body两个骨头的动画，其他不动）

<a href="javascript:void(0);" target="_blank" style="">DEMO:控制公鸡动画</a>
<a href="javascript:void(0);" target="_blank" style="">DEMO:公鸡换装备</a>


[slide style="background-image: url('/img/bg24.png')"]
<span class="theme-tag">&middot;DragonBones 实现骨骼动画</span>
## DragonBones 实现动画——骨骼动画事件监听code
----
<img src="/img/skeleton-code3.png" class="h5-compare">


[slide style="background-image: url('/img/bg24.png')"]
<span class="theme-tag">&middot;DragonBones 实现骨骼动画</span>
## DragonBones 实现动画——骨骼动画事件交互code
----
<img src="/img/skeleton-code4.png" class="h5-compare">


[slide style="background-image: url('/img/bg24.png')"]
<span class="theme-tag">&middot;DragonBones 实现骨骼动画</span>
## DragonBones 实现动画——骨骼动画换装code
----
<img src="/img/skeleton-code5.png" class="h5-compare">


[slide style="background-image: url('/img/bg24.png')"]
<span class="theme-tag">&middot;DragonBones 实现骨骼动画</span>
## 骨骼动画的应用
----
- 目前骨骼动画已经被大规模地使用在游戏和动画中，大有一种**取代帧动画**的趋势
- 骨骼动画主要被用**游戏场景**中，做**Logo**、**彩蛋**也不错


[slide]
## 参考文献
----
- [骨骼动画原理与前端实现浅谈](https://blog.csdn.net/linuxheik/article/details/81838031)
- [DragonBones 官网](http://dragonbones.com/cn/index.html)
- [2D骨骼动画工具DragonBones的使用教程](https://blog.csdn.net/weixin_33935777/article/details/93012239?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-5.nonecase&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-5.nonecase)
- [前端动画渲染引擎pixi.js系列（10）骨骼动画实现之DragonBones](https://blog.csdn.net/zeping891103/article/details/72529122)
- [骨骼动画在H5使用攻略](https://gameinstitute.qq.com/community/detail/111189)
- [HTML5 游戏引擎深度测评](https://cloud.tencent.com/developer/article/1069581)
- [Pixi.js 官网](http://pixijs.com)
- [Pixi.js源码分析](https://blog.csdn.net/o83290102o5/category_9281258.html)
- [浅析 Pixi.js 渲染流程](https://blog.mutoo.im/2015/02/understand-pixi-js-rendering/)
- [Laya 动画系列三 骨骼动画](https://www.jianshu.com/p/2aac3971368a)


[slide style="background-image: url('/img/bg23.png')" data-transition="cover-circle"]
# Thank you
