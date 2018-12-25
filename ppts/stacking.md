title: 你的 Stacking Context
speaker: zhiyuchangxin
utl: https://github.com/zhiyuchangxin/shares
transition: slide2
files: /css/index.css
theme: moon
date: 2018-11-09

[slide style="background-image: url('/img/bg22.png')"]
# 你的 Stacking Context
----
<br/>
<img src="/img/high.png" class="index-img">
@织语长心&nbsp;&nbsp;2018-11-09


[slide style="background-image: url('/img/bg22.png')"]
## 知识点（***7***）
----
<!-- <img src="/img/module.png" class="seven-module"> {:&.fadeIn} -->
* 层叠界的术语 {:&.moveIn}
* 层叠准则
* 层叠上下文的特性
* 层叠上下文的创建 ***✔️***
* 层叠顺序 ***✔️***
* 控制层叠顺序
* 代码中的层叠应用


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;层叠界的术语</span>
## 一、层叠界的术语
----
1. **z轴**：眼睛垂直于屏幕的一条虚拟的轴线 {:&.moveIn}
2. **层叠上下文(Stacking Context)**：表示元素在z轴上的层叠水平.(html 的三维概念)
3. **层叠顺序(Stacking Order)**：表示同一层叠上下文中的元素在z轴上的显示顺序


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;层叠准则</span>
## 二、层叠准则
----
前提条件：同一层叠上下文中： {:&.flexbox.vleft.moveIn}
* **谁大谁上**：非同一层叠水平时，水平高的在上面 {:&.flexbox.vleft.moveIn}
* **后来居上**：同一层叠水平时，后出现的在上面


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;层叠上下文的特性</span>
## 三、层叠上下文的特性
----
1. ***层叠上下文***的层叠水平要比***普通元素***高 {:&.moveIn}
2. 层叠上下文可以***嵌套***：内部层叠上下文及其所有子元素均受制于外部的层叠上下文
3. 每个层叠上下文和兄弟元素***独立***：当进行层叠变化或渲染的时候，只需考虑后代元素
4. 每个层叠上下文***自成体系***：当元素发生层叠的时候，整个元素被认为在**父层叠上下文的层叠顺序中**
5. 层叠上下文可以***阻断***元素的混合模式


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;层叠上下文的创建</span>
## 四、层叠上下文的创建
----
1. **天生派(根元素)**：页面的根元素`<html>`天生具有层叠上下文 {:&.moveIn}
2. **正统派(传统)**：z-index为**数值**的**定位元素**（除 IE6、7 外）
  - z-index: auto 在 IE6、7 上也会创建层叠上下文 {:&.fadeIn}
3. **扩招派(新秀)**：**CSS3** 属性产生的层叠上下文


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;层叠上下文的创建</span>
## 正统派层叠上下文创建
----
* ***position: relative/absolute***定位： {:&.moveIn}
  - z-index: !auto 创建 {:&.fadeIn}
* ***position: fixed***定位：
  - z-index: !auto 创建「非 chrome 等 Webkit 内核浏览器」<a href="https://codepen.io/zhiyuchangxin/pen/vQGZVj" target="_blank">DEMO:(oldCreate1)</a> {:&.fadeIn}
  - 直接创建「chrome 等 Webkit 内核浏览器」<a href="https://codepen.io/zhiyuchangxin/pen/LXNLRb" target="_blank">DEMO:(oldCreate2)</a>
  - 以上两种情况导致其内部创建的层叠上下文总受外层影响！！!
* ***position: sticky***定位时 ？？？


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;层叠上下文的创建</span>
## 扩招派层叠上下文创建
----
```
1. display:flex|inline-flex 弹性布局：z-index != auto 创建
2. 元素的 opacity: !1
3. 元素的 transform: !none
4. 元素的 filter: !none
5. 元素的 mix-blend-mode: !normal // 元素和白色背景混合，IE 不支持
6. 元素的 isolation: isolate // 阻隔混合模式
7. 元素的 will-change 属性值为 transform... // 增强页面渲染性能
8. 元素的 -webkit-overflow-scrolling: touch
```
<br/>
<a href="https://codepen.io/zhiyuchangxin/pen/YRqxXO" target="_blank">DEMO:(newCreate)</a>


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;层叠顺序</span>
## 五、层叠顺序（Stacking Order）
----
<p style="margin-bottom:10px;font-size:20px;font-weight:600;">
一旦普通元素具有了层叠上下文，其层叠顺序就会变高，具体定位具体分析：
</p>
<img src="/img/stacking-order.png" class="indstacking-order">
<a href="https://codepen.io/zhiyuchangxin/pen/RqarRv" target="_blank"style="position: absolute;right:-200px;bottom:28px;text-align:left;">DEMO:<br/>(StackingOrder)</a>


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;层叠顺序</span>
### 思考
----
<img src="/img/question.png" class="sc-question">
1. 为什么内联元素的层叠顺序比浮动元素和块状元素高
2. 为什么定位元素会在普通元素之上展示


[slide style="background-image: url('/img/bg22.png')"]
[note]
translateZ 注意:
1. 祖先元素需要设置 transform-style: preserve-3d
2. translateZ 属于 GPU hack 属性， 可以使用 GPU 加速；耗电！！！
3. 非 body 的祖先级元素添加 overflow: hidden 后会使其失去优越高，恢复到 z-index: auto/0 的水平
[/note]
<span class="theme-tag">&middot;改变层叠顺序</span>
## 六、改变层叠顺序
----
1. ***不产生***层叠上下文的前提下： {:&.moveIn}
  - 调整**DOM**结构（后来居上准则） {:&.fadeIn}
  - 添加**非z-index**相关的属性（block、float、inline、inline-block、定位...）
2. ***产生***层叠上下文的前提下：
  - **z-index**问鼎天下 {:&.fadeIn}
  - **translateZ**逐鹿中原
  - **z-index**与**translateZ**冲突：双剑合璧？？？


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;改变层叠顺序</span>
## 七、代码中的应用
----
* z-index 负值深入 {:&.moveIn}
  - z-index 负值渲染的过程：实际是一个寻找第一个层叠上下文元素的过程（永远逃不脱的结界） {:&.fadeIn}
  - （1）实现可访问性隐藏<a href="https://codepen.io/zhiyuchangxin/pen/RqarRv" target="_blank">DEMO:(StackingOrder)</a>
  - （2）实现定位在元素的后面<a href="https://codepen.io/zhiyuchangxin/pen/wQGrgd" target="_blank">DEMO:(MinusZindex)</a>
* 非浮动元素：z-index “不犯2”准则
* 浮层元素：z-index “层级计数器”
  - 获取 z-index 最大值 / z-index 默认值（习惯设置为9） {:&.fadeIn}


[slide style="background-image: url('/img/bg22.png')"]
## 参考文献
----

* <a href="https://www.zhangxinxu.com/wordpress/2016/01/understand-css-stacking-context-order-z-index/" target="_blank">深入理解CSS中的层叠上下文和层叠顺序</a>
* &nbsp;张鑫旭新出的书：《CSS 世界》


[slide style="background-image: url('/img/bg13.png')"  data-transition="cover-circle"]
# Thank you
