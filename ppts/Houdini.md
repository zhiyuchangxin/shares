title: Houdini：CSS 领域最令人振奋的革新
speaker: zhiyuchangxin
utl: https://github.com/zhiyuchangxin/shares
transition: slide2
files: /css/index.css
theme: moon
date: 2018-05-18

[slide]

<img src="/img/houdini.jpg" class="no-screenfull">

> Maybe The Most Exciting Development In CSS You've Never Heard Of

<br/>
@织语长心&nbsp;&nbsp;2018-05-18


[slide]

## 目&nbsp;&nbsp;&nbsp;录
----
* 初识 Houdini —— 新的希望将至 {:&.moveIn}
* 选择 Houdini
  - 放弃 css polyfill {:&.fadeIn}
  - 比较 CSS Preprocessors
* ***Houdini API 介绍***
  - CSS Typed OM {:&.fadeIn}
  - CSS Properties and Values API
  - CSS Worklets API
  - CSS Painting API
  - CSS Layout API
* 总结
* 参考文献

<img src="/img/lm.gif" class="no-screenfull lm-rool">


[slide style="background-image: url('/img/bg.jpg');" data-transition="cover-circle"]
# 初识 Houdini
##（胡迪尼）


[slide]

[note]
<div class="pic-note">
  <img src="/img/js-time.jpg" class="no-screenfull first">
  <p>从上图可以看到，从想到一个新的 js 特性到运用在生产环境，大概只需要几天时间</p>
  <br/><br/>
  <img src="/img/css-time.jpg" class="no-screenfull">
  <p>而要允许一个新特性被写入 CSS 标准需要经过一整套标准制定流程；</p>
  <p>对于这个标准制定的流程肯定是毫无异议的，但我们必须承认，走完整个流程花儿都谢了。</p>
</div>
<p class="houdini-welcome">Houdini 闪亮登场啦！</p>
<img src="/img/qb.jpg" class="no-screenfull qb-icon">
[/note]

## 千呼万唤始出来
----
* css 社区 VS js 社区： {:&.moveIn}
  - 在 JS 社区，你总能听到人们在抱怨它一天一个样 —— 跑得太快追得太累 {:&.fadeIn}
  - 在 CSS 社区，人们却在叹息着花精力去学习新事物是件多么吃力不讨好的事儿 —— 天知道什么时候才能用上新玩意
<mark>NOTE</mark>

[slide]

## 我是 css 胡迪尼
----

* amazing {:&.moveIn}
  - 2018 最让人兴奋的 CSS 技术是什么，CSS Houdini 当之无愧
  - 甚至可以去掉 2018 这个限定，早在 **2016** 年这个技术就出来了
  - 但是在**今年3月**发布的 **Chrome 65** 才正式支持
* definition
  - Houdini 是 W3C 新成立的一个任务小组
  - Houdini 好比是一张拼图，它是一系列 API 的统称
  - Houdini 的终极目标：***实现 css 属性的完全兼容***
  - Houdini 提出的设想：***开放 CSS 的 API 给开发者***

<!-- 
1. 允许开发者直接操作浏览器的 CSS 引擎，开发者拥有极大的权限，甚至能干预浏览器原生的渲染流程；
2. 开发者可以通过这套接口自行扩展 CSS，并提供相应的工具允许开发者介入浏览器渲染引擎的样式和布局流程中；
3. 这就表示，开发者不用再等待浏览器厂商了，只要支持了 Houdini 就能用上新特性。甚至是浏览器压根不打算实现的，开发者也能自力更生传达完美的效果给用户.
-->
<br>
* （非）官方的<a href="https://googlechromelabs.github.io/houdini-samples/" target="_blank">DEMO1</a><a href="https://hello-houdini.herokuapp.com/" target="_blank">DEMO2</a> {:&.moveIn}


[slide]

## 亲们，都来支持我吧
----

<p style="font-size:20px;text-align:left;text-indent: 24px;">
  **好消息：** Apple、Google、微软、Mozilla、Opera 都是 Houdini 项目的推动者
</p>
<p style="font-size:20px;text-align:left;text-indent: 24px;">
  **坏消息：** 目前为止只有 Google Chrome 落地实施了这个计划
</p>
<br/>
<p style="font-size:20px;">
  各个浏览器厂商的实现程度如下图所示
  <a href="https://ishoudinireadyyet.com/" target="_blank">（ishoudinireadyyet）</a>
</p>

<img src="/img/support.png">


[slide style="background-image: url('/img/bg.jpg')" data-transition="cover-circle"]
# 选择 Houdini

[slide]
## 放弃 css polyfill
----

* JS 是一种动态语言，它是如此之**动态**以至于有着让人惊叹的可扩展性，所以 **JS polyfill** 可以轻松实现 {:&.moveIn}
* 鉴于 css 的**静态性**，**CSS polyfill** 做起来就相对难上很多
  - CSS polyfill 在构建过程中，可以将一种形式的 CSS 转译成另一种形式（postCSS：常用的 <code>autoprefixer</code>）
  - CSS polyfill 一旦依赖于的 DOM 结构、某一个元素的布局或定位的话，那补丁程序就需要在本地运行了
* 而且在大部分情况下，只要这么做了，性能肯定会受到影响

<img src="/img/llq-render.jpg"> {:&.moveIn}

[slide]

[note]
## 场景：现有一个页面，需要换肤功能
<!--
* 使用 scss 生成多套肤色的 css 文件，然后根据不同的场景引入相应的文件（多文件）
* 使用 css 的优先级在一个 css 文件里覆写已有样式，然后根据不同的场景给DOM添加不同的类名（有冗余代码）
* 加入能在 css 中定义变量呢，然后在 js 中直接通过暴露的 API 接口修改变量的值呢（非常完美）
-->
<img src="/img/question.png" class="no-screenfull question-icon">

[/note]

## 比较 css Preprocessors
----

* 预编译工具只有**编译时策略**，而面向未来的 CSS 既可以有编译时策略，也可以有**运行时策略** <mark>NOTE</mark>  {:&.moveIn}
* 虽然在上面强调了运行时和编译时的差别，但绝对没有谁强过谁的意思。我们一定要清楚，无论现在还是未来，CSS是**标准**，预编译工具是标准的**拓展**，两者并不冲突

[slide style="background-image: url('/img/bg.jpg')" data-transition="cover-circle"]
# Houdini API 介绍

[slide]

## 浏览器渲染过程所对应的 API
<img src="/img/llq-apis.jpg">

<p style="color:#eee;font-size:20px;">（灰色区块是还在实现中的标准，目前暂时无法使用）</p>

* Houdini 小分队为了解决这个问题引入了一些新的标准，首次给了开发者介入另外几个渲染环节的权限


[slide]
## 1. Typed OM
----

* 可以把 CSS Typed OM 视为 CSSOM 2.0
* 它的目的在于解决目前模型的一些问题，并实现 CSS **Parsing** API 和 CSS **Properties and Values** API 相关的特性
* 提升性能是 Typed OM 的另一重任
* Chrome 66+ 已默认开启该接口


[slide]

[note]
* Accessing styles
  - 值独立于单位而存在，返回一个包含值与单位的 CSSUnitValue 对象
* Computed styles
  - 由 window 的 API 移到 el 的 computedStyleMap() 方法
* 优点
  - 数值总是作为数字返回而非字符串，不容易出错。（做运算的时候避免了字符串的拼接）
  - 更好的性能（减少了浏览器对字符串值的序列化和反序列化工作）
  - 新的解析方式为 css 的世界带来了错误处理
  <pre>
  <code>
    try {
      const css = CSSStyleValue.parse('transform', 'translate4d(bogus value)');
      // use css
    } catch (err) {
      console.err(err);
    }
  </code>
  </pre>
[/note]

<div>
  <pre>
    <span style="font-size:28px;">Old CSSOM</span>
    <code class="javascript">
      el.style.width = '100px';
      typeof el.style.width;  // 始终输出 string<br>
      window.getComputedStyle(el).width === '100px'
    </code>
  </pre>
  <pre>
    <span style="font-size:28px;">CSS Typed OM<mark style="margin-left:60px;">NOTE</mark></span>
    <code class="javascript">
      el.attributeStyleMap.set('width', '100px'); // 或 CSS.px(100)
      typeof el.attributeStyleMap.get('width'); // 输出 CSSUnitValue object
      el.attributeStyleMap.get('width').value; // 100
      el.attributeStyleMap.get('width').unit; // px<br>
      el.attributeStyleMap.has('width'); // true
      el.attributeStyleMap.delete('width'); // remove width
      el.attributeStyleMap.clear(); // remove all styles<br>
      el.computedStyleMap().get('width').value // CSSUnitValue object
    </code>
  </pre>
</div>


[slide]
## 2. CSS Properties and Values API
----

#### PART1: **CSS 变量** <a href="https://caniuse.com/#search=custom%20properties" target="_blank">（caniuse）</a>
* 除 IE family 外，Chrome、Firefox、Safari 都已支持 {:&.moveIn}
* 变量定义：可以定义在 :root 下，也可以定义在 el 中
  - 变量名：使用 --* 的形式，大小写敏感
  - 变量值：可以为颜色、字符串、多和值的组合等
* 变量用法：使用 var()
<pre>
  <code class="css">
    :root {
      --main-color: #f00;
      --main-bg: rgb(255, 255, 255);
      --main-text: 'Hello World'
      --margin-top: calc(2vh + 20px);
      }
    div {
      background: var(--main-color);
    }
  </code>
</pre>

* <a href="https://codepen.io/zhiyuchangxin/pen/KRebge" target="_blank">Demo(Heart)</a>、<a href="https://codepen.io/zhiyuchangxin/pen/oddKdB" target="_blank">Demo(Ranges)</a>

[slide]

#### PART2: **CSS Properties and Values API**
* CSS Properties and Values API 的出现进一步推动了自定义属性 {:&.moveIn}
* 允许自定义属性添加不同的类型，大大增强了自定义属性的能力
<pre>
  <code class="javascript">
    CSS.registerProperty({
      name: '--*',
      syntax: '<color>', // length、number、percentage、color、image、url、angle...
      inherits: false,
      initialValue: 'rgba(0,0,0,0)'
    })
  </code>
</pre>
* 最大的的卖点是开发者可以在自定义属性上***做动画***
  - 注意 demo 中的 <code>transition: --my-size .2s ease;</code>
* <a href="https://codepen.io/zhiyuchangxin/pen/MGqEwx" target="_blank">Demo(Variable Demo__beautifulBtn)</a>


[slide]
## Worklets
----

* Worklets 允许引入脚本文件并执行特定的 JS 代码 {:&.moveIn}
  - 脚本文件的引入：<code>CSS.xxWorklet.addModule('xx.js')</code> {:&.fadeIn}
  - 脚本文件的执行（满足两个条件）：可以在渲染流程中调用；独立于主线程
<pre>
  <code class="javascript">
    if ('paintWorklet' in CSS) {
      CSS.paintWorklet.addModule('placeholder-box.js');
    } else {
      document.body.innerHTML = 'Not support :(';
    }
    if ('layoutWorklet' in CSS) {
      CSS.layoutWorklet.addModule('masonry.js');
    } else {
      document.body.innerHTML = 'Not support :(';
    }
  </code>
</pre>
> 注：无法在 worklets 中打断点或者插入 debugger ，只能用 console.log

[slide]

## CSS Paint API
----

* 通过 CSS Paint API 开发者可以画出图像，然后把这些图像运用到合适的 CSS 属性上 {:&.moveIn}
* CSS Paint API 暴露了一个 <code>registerPaint()</code> 方法给开发者
  - 接收一个**布局名（paint name）**作为后续 CSS 中的属性值 {:&.fadeIn}
  - 包含一个 paint 逻辑的 **JS 类**
* 构建一个 CSS 图像时（重绘元素被触发时），调用 <code>paint()</code> 函数
  - ctx: 将被绘制的对象，和 <code>CanvasRenderingContext2D</code> 对象差不多，不过多了些限制 {:&.fadeIn}
  <!-- （比如无法绘制文字） -->
  - geom: 包含绘制元素宽和高的对象（数值型）
  - props: 接收的属性（可接收已有属性，也可以接收自定义属性）
  - 绘制时使用 canvas API
  - 调用时使用 <code>background-image: paint(xxx)</code>

[slide]

## 代码风格
----
<pre>
  <code class="javascript">
    // 绘制一个圆
    registerPaint('circle', class {
      static get inputProperties() { return ['background-color', '--test-color']; }
      paint(ctx, geom, props) {
        // Change the fill color.
        const color = props.get('--test-color').toString();
        ctx.fillStyle = color;
        // Determine the center point and radius.
        const x = geom.width / 2;
        const y = geom.height / 2;
        const radius = Math.min(x, y);
        // Draw the circle
        ctx.beginPath();
        ctx.arc(x, y, radius, 0, 2 * Math.PI);
        ctx.fill();
      }
    });

    // 调用
    div { background-image: paint(circle); }
  </code>
</pre>

<a href="https://codepen.io/zhiyuchangxin/pen/aGQWmr" target="_blank">Demo(Paint API Demo__beautifulBtn)</a>

[slide]

## CSS Layput API
----

* 通过 CSS Layout API 实现自己的布局模块（layout module）
  - 这里的“布局模块”指的是display 的属性值
  - API 实现以后，开发者首次拥有了像 CSS 原生代码那样的布局能力（eg: <code>display:flex</code>、<code>display:table</code>...）

[slide]

## 代码风格
----
<pre>
  <code class="javascript">
    registerLayout('masonry', class {
      static get inputProperties() {
        return ['width', 'height']
      }
      static get childrenInputProperties() {
        return ['x', 'y', 'position']
      }
      layout(children, constraintSpace, styleMap, breakToken) {
        // Layout logic goes here.
      }
    }

    // 调用
    div { display: layout(masonry); }
  </code>
</pre>

[slide style="background-image: url('/img/bg.jpg')" data-transition="cover-circle"]
# 总结

[slide]
## 重点：Houdini API
----

* CSS Typed OM {:&.fadeIn}
* **CSS Properties and Values API**
* CSS Worklets API
* **CSS Painting API**
* CSS Layout API

[slide]
## 技术提示
----

* 以上这些暂时还只能在 Chrome 上做试验 {:&.moveIn}
  - Chrome 65+ 已默认开启接口
  - Chrome 65 以下版本需要通过访问 chrome://flags 开启 Experimental Web Platform features.（chrome://flags/#enable-experimental-web-platform-features）
* CSS Paint API 必须要在支持 https 服务器上或者本地 localhost 上才能使用（本地开发可通过 http-server）
* 目前无法在 worklets 中打断点或者插入 debugger ，只能使用 console.log 帮忙啦

[slide]
## 优缺点——优点
----

* 不受限制，开发者能创造各种各样的视觉效果
* 不需要新增 DOM 节点
* 在浏览器渲染管道中执行，效率高
* 比起 polyfill，更加性能友好，也更健壮
* 浏览器原生支持的接口，开发者有了不用 hack 的选择
* 可以用 paint worklet 编写视觉效果上的逻辑了。（用于实现视觉效果的 CSS 常常被诟病不像一门编程语言，几乎无法表达完整的逻辑）
* 动画革命。
* 快浏览器厂商一步实现特性，而且这些特性能实实在在地展现在用户设备上
* 五大浏览器厂商都表示支持 Houdini

[slide]
## 优缺点——缺点

* Houdini 的实现之路漫漫 {:&.moveIn}
* 虽然它可以缓解兼容问题，但首先，浏览器们得先兼容 Houdini…
* 浏览器加载 paint worklet 并执行它需要时间，这是异步的，可能导致样式上的闪动
* 开发者工具尚不支持 paint worklet 的断点调试（也不支持 debugger），暂时只能用 console.log()

[slide style="background-image: url('/img/bg.jpg')" data-transition="cover-circle"]
# 参考文献

[slide]

#### 官方文档
* <a href="https://drafts.css-houdini.org/" target="_blank">W3C: CSS-TAG Houdini Editor Drafts</a>
* <a href="https://ishoudinireadyyet.com/" target="_blank">Is Houdini ready yet?</a><br><br>

#### 阅读原文
* <a href="https://juejin.im/post/5ac033e951882555712c7e16" target="_blank">2018 CSS 大会多图见闻录</a>
* <a href="https://www.smashingmagazine.com/2016/03/houdini-maybe-the-most-exciting-development-in-css-youve-never-heard-of/" target="_blank">CSS 领域最令人振奋的革新</a>
* <a href="https://zhuanlan.zhihu.com/p/20939640" target="_blank">CSS 领域最令人振奋的革新(译)</a>
* <a href="https://juejin.im/entry/5acaa4136fb9a028c97a56a4" target="_blank">和 Houdini, CSS Paint API 打个招呼吧</a>
* <a href="https://img.w3ctech.com/slide/CSS-Houdini-gougu.pdf" target="_blank">勾股的ppt</a>
* <a href="https://www.w3cplus.com/css3/css-properties-in-depth.html" target="_blank">深入学习CSS自定义属性（CSS变量）</a>
* <a href="https://developers.google.com/web/updates/2018/03/cssom#errors" target="_blank">Working with the new CSS Typed OM</a>
* <a href="https://mp.weixin.qq.com/s/69Fg3795qhYU76eM4mxwEA" target="_blank">不断被挑战的预编译工具</a>
* <a href="https://www.w3ctech.com/topic/1979" target="_blank">CSS Polyfill的痛楚</a>

[slide]

* My Demo
  - <a href="https://codepen.io/zhiyuchangxin/pen/KRebge" target="_blank">Heart——css variable</a>
  - <a href="https://codepen.io/zhiyuchangxin/pen/oddKdB" target="_blank">Ranges——css variable</a>
  - <a href="https://codepen.io/zhiyuchangxin/pen/MGqEwx" target="_blank">beautifulBtn——Properties and Values API</a>
  - <a href="https://codepen.io/zhiyuchangxin/pen/aGQWmr" target="_blank">beautifulBtn——Paint API</a><br><br>

* Other Demo
  - <a href="https://googlechromelabs.github.io/houdini-samples/" target="_blank">houdini-samples</a>
  - <a href="https://hello-houdini.herokuapp.com/" target="_blank">Hello Houdini</a>

[slide style="background-image: url('/img/bg13.jpg')"  data-transition="cover-circle"]
# Thank you, Thank noteppt
