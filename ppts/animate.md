title: 关于动画的九件小事
speaker: zhiyuchangxin
utl: https://github.com/zhiyuchangxin/shares
transition: slide2
files: /css/animate.css
theme: moon
date: 2019-04-26

[slide style="background-image: url('/img/bg1.jpg')"]
# 关于动画的九件小事
----
<br/>
<!-- <img src="/img/high.png" class="index-img"> -->
@织语长心&nbsp;&nbsp;2019-04-26


[slide style="background-image: url('/img/bg22.png')"]
## 第五届 CSS 大会
----
- 回顾：https://www.yuque.com/cssconf/5th {:&.moveIn}
- 特别想说：<span>******</span>


[slide style="background-image: url('/img/bg22.png')"]
## 特别想说“自动 margin”
----
- 垂直居中实现？那么原理呢？ {:&.moveIn}
- 我对 margin 的理解：https://blog.zhiyuchangxin.cn/articles/margin/index.html


[slide style="background-image: url('/img/bg22.png')"]
## 我能想到的动画实现方式（***12***）
----
<div style="padding-left: 150px; padding-top: 30px; text-align: left; text-shadow:1px 2px 0px #152E4F, 3px 5px 0px rgba(0,0,0,0.2);">
  <p>1. Css Feather （✔️）</p>
  <p>2. Css Transition （✔️）</p>
  <p>3. Css Animation （✔️）</p>
  <p>4. Js Animation</p>
  <p>5. Jq Animate </p>
  <p>6. 动画库</p>
  <p style="font-weight: 900;color: #16D5B5;">7. Web Animation （✔️）</p>
  <p>8. Vue Transition</p>
  <p style="opacity: 0.4;">9. Gif 图算吗</p>
  <p style="opacity: 0.4;">
    10. Canvas
    <!-- <img src="/img/.png"> -->
  </p>
  <p style="opacity: 0.4;">11. Svg</p>
  <p style="opacity: 0.4;">12. Webgl</p>
</div>


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;Css Feather</span>
## 一、Css Feather（？）
----
> “属性动画”名称是我杜撰的，我说是动画大家将就听一听吧~  {:&.moveIn}

<div style="padding-left: 120px;padding-top: 30px; text-align: left;">
  <p>Feather One：****</p>
  <p>Feather Two：****</p>
  <p>Feather Three：****</p>
</div>



[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;Css Feather</span>
## Feather One: `Sticky` 粘性定位
----
- 粘性定位可以被认为是相对定位 relative 和固定定位 fixed 的混合 {:&.fadeIn}
- 必须指定 top right bottom left 四个阈值之一，粘性定位才会生效
- 元素在跨越阈值前为相对定位，之后为固定定位


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;Css Feather</span>
----
- <a href="https://caniuse.com/#search=sticky" target="_blank">兼容性</a><img src="/img/sticky-compatibility.png" class="content-img"> {:&.moveIn}
- 适用场景：
  - 通讯录定位<a href="https://codepen.io/pen/?&editable=true" target="_blank">(MDN DEMO)</a> {:&.fadeIn}
  - Tab滚动吸顶<a href="https://juejin.im/post/5caa0c2d51882543fa41e478?utm_source=gold_browser_extension#comment" target="_blank">推荐文章：5 种滚动吸顶实现方式的比较[性能升级版]</a>
- **Tip**: sticky 在 IOS 系统上兼容良好，但在安卓上暂时还是不要使用了


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;Css Feather</span>
## Feather Two: `scroll-snap` 滚动捕捉
----
- scroll Snap 可以让网页容器滚动停止时自动平滑定位到元素的指定位置（类似幻灯片广告） {:&.fadeIn}
- 常用属性（2个就够了）
```css
/* 父容器最重要的属性 */
scroll-snap-type: none | [ x|y|block|inline|both ] [ mandatory|proximity ]
/* 子元素最重要的属性 */
scroll-snap-align: [none | start | center | end]{1,2}
```

[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;Css Feather</span>
----
- <a href="https://caniuse.com/#search=scroll-snap" target="_blank">兼容性</a><img src="/img/snap-compatibility.png" class="content-img"> {:&.moveIn}
- 适用场景： <a href="https://codepen.io/airen/full/VRgevr" target="_blank">换装DEMO</a><a href="javascript:void(0);" target="_blank">幻灯片DEMO</a>
- **Tip**: 兼容性良好，但是缺少动画结束回调，功能不够完善。
- **小事一**： 可以用 scroll-snap 捕捉滚动实现简单轮播效果


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;Css Feather</span>
## Feather Three: `resize`
----
```css
overflow: !visible
resize: none | horizontal | vertical | both ...
```
- 常用：禁止 Textarea 拉动
- Amazing: <a href="javascript:void(0);" target="_blank">实现两栏拖动(配合滚动条样式)</a>


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;Css Transition</span>
## 二、Css Transition
----


[slide style="background-image: url('/img/bg22.png')"]
[note]
<img src="/img/transition-process.png" class="content-img">
<p style="margin: 20px 0; text-align: center; font-size: 30px; color: #f00;">Js 在 painting 之后才执行</p>
[/note]
<span class="theme-tag">&middot;Css Transition</span>
## **小事二**：Transition 仅在样式发生变化时才会运行
----

- 伪元素之间的切换`:hover`、`:active` <a href="javascript:void(0);" target="_blank">（StarDemo）</a> {:&.moveIn}
- Js 实现的状态变化
<!-- - transition 可以被取消 -->
- **Tip1**：Js 创建 DOM 并直接设置过渡，是监测不到样式变化的<mark>Note</mark>
  - 执行两次 requestAnimationFrame() 向后两帧计算出样式的变化 {:&.fadeIn}
  - getComputedStyle(el)[property] 计算出样式变化
- **Tip2**：元素被移除、`display:none` 同样监测不到样式变化
- **Tip3**：`transition-timing-function` 默认值为 `ease`


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;Css Animation</span>
## 三、Css Animation
----


[slide style="background-image: url('/img/bg22.png')"]
[note]
<img src="/img/transition-process.png" class="content-img">
[/note]
<span class="theme-tag">&middot;Css Animation</span>
## Css Animation 相关 DEMO
----
- <a href="javascript:void(0);" target="_blank">遮罩层DEMO</a>
  - 主要在扇形的实现上，动画作为辅助效果
- <a href="javascript:void(0);" target="_blank">色带流动DEMO</a>
  - 传统的思路：制作背景图移动背景图位置
  - 新思路：之间动画改编色相饱和度属性
- <a href="javascript:void(0);" target="_blank">小球DEMO</a>
  - **小事三**：animation-timing-function 只在关键帧之间适用
- <a href="javascript:void(0);" target="_blank">倒计时DEMO</a>
  - **小事四**：animation-timing-function 默认值 ease，自动补间动画


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;Css Animation</span>
## 等等，还有一个 BUG
----
<div style="display:inline-block; width: 28%; vertical-align: middle;">
  <img src="/img/bug-cut.png" class="content-img">
</div>
<div style="margin-left: 50px; display:inline-block; width: 38%; vertical-align: middle;">
  <img src="/img/after-rem.png" class="content-img">
  <img src="/img/after-keyframe.png" class="content-img">
</div>

特殊的缘分：同时使用**伪元素**+**animation中含rem单位**+**小米4.4手机**，
CSS 导致 app 崩溃了

[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;Css Animation</span>
----
<div style="display:inline-block; margin-right: 50px; width: 50%; vertical-align: middle;">
  <img src="/img/el-rem.png" class="content-img">
</div>
<div style="display:inline-block; text-align: left; vertical-align: middle; font-weight: 900;">
  <p>解决方案：</p>
  <p>1. 不使用 rem</p>
  <p>2. 不使用 animation</p>
  <p>3. 不使用 伪元素 （✔️）</p>
</div>
<p style="position: absolute; right: -200px; bottom: 0; font-size: 18px; opacity: .6;">
  相同的遭遇：
  <a href="http://www.uml.org.cn/html/2017020705.asp" target="_blank">原来CSS这样写是会让app崩溃的</a>
</p>
<br>
- **小事五**：避免将动画作用于使用了 rem 的伪元素上 {:&.fadeIn}


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;Js Animation</span>
## 四、Js Animation
----
- <a href="https://v5-ui.58corp.com/demo/#/" target="_blank">DEMO：V5 组件库</a>中的按钮动画 {:&.moveIn}
  - 通过对 rippleJS 的改写，实现了水波纹动效按钮 {:&.fadeIn}
  - <a href="https://github.com/samthor/rippleJS" target="_blank">读一读 rippleJS 源码</a>
  - 其他实现思路？<a href="javascript:void(0);" target="_blank">自定义属性实现</a>


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;动画库</span>
## 五、动画库
----
- <a href="https://blog.fundebug.com/2019/01/11/10-javascript-animation-library-in-2019/" target="_blank">2019年10个最受欢迎的JavaScript动画库！</a> {:&.moveIn}
- <a href="http://velocityjs.org/" target="_blank">Velocity.js 官网</a>
  - <a href="https://github.com/julianshapiro/velocity" target="_blank">Velocity.js 源码</a>（🤩 4000+ 行啊~） {:&.fadeIn}
  - 80+ 行说一下<a href="javascript:void(0);" target="_blank">原理</a>
  - <a href="https://www.npmjs.com/package/velocity-vue" target="_blank">velocity-vue</a>?


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;Web Animation</span>
## 六、Web Animation
----


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;Web Animation</span>
## Web Animation API（简：WAAPI）
----
- WAAPI 将浏览器动画引擎向开发者打开，并由 Js 进行操作，将表现与行为分开
- <a href="https://caniuse.com/#search=web" target="_blank">兼容性</a><img src="/img/web-animation-API.png" class="content-img" style="width: 80%;">
  - Firefox 48+ 和 Chrome 36+ 中 Web Animation API
  - Webkit 和 Edge 已经将 API 移动到各自的待办事项列表中
  - 可以测试功能支持来添加 <a href="https://github.com/web-animations/web-animations-js" target="_blank">polyfill</a>
- **小事六**：现在可以开始使用 Web Animation API 啦


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;Web Animation</span>
## 如何使用 WAAPI
----
> 用过 jq 的 animate() 就方便多啦， WAAPI 的基本语法与之类似，  
不同的是，WAAPI 是浏览器原生支持的，在性能上有很大的优势。

<br>
```js
var element = document.querySelector('.animate-me');
element.animate(keyframes, 1000);
```
- DOM节点具备全新的 animate 方法 {:&.moveIn}
- animate 方法接收两个参数
  - **动画模型**keyframes：通常是一个对象数组，对应 CSS @keyframes 块的关键帧对象 {:&.fadeIn}
  - **时序模型**options：包含动画时序参数


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;Web Animation</span>
## 注意 WAAPI **VS** CSS 属性上的差异
----
<img src="/img/web-animation-compare.png" class="content-img">


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;Web Animation</span>
## 如何使用 WAAPI
----
```js
// 动画模型
var keyframes = [
  { opacity: 0 },
  { opacity: 1 }
];
// 时序模型
var options = {
  iterations: Infinity, // 对应 animation-iteration-count: infinite
  iterationStart: 0,
  delay: 0,
  endDelay: 0,
  direction: 'alternate',
  duration: 700,
  fill: 'forwards',
  easing: 'ease-out', // 对应 animation-timing-function: ease-out
}
element.animate(keyframes, options);
```


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;Web Animation</span>
## WAAPI 的 animate 的返回值
----
- animate 方法不仅仅为元素提供动画，它还有自己的返回值。<img src="/img/web-animation-obj.png" class="content-img"> {:&.moveIn}
- <a href="javascript:void(0);" target="_blank">DEMO：两个小球撞击</a>


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;Web Animation</span>
## 其他常用 WAAPI
----
```
play()
pause()
reverse()
finish() // Promise
playbackRate // 控制动画速度（可为负值——反向）
```
<a href="https://web-animations.github.io/web-animations-demos/" target="_blank">DEMO（firefox上预览）</a>
<a href="https://codepen.io/rachelnabors/full/PNGGaV" target="_blank">ALice DEMO</a>


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;Vue Transition</span>
## 七、Vue Transition
----
**小事七**：Vue transition 中同时使用过渡和动画，可以选择性结束动画


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;性能</span>
## 八、性能
----
- css 在实现复杂动画上有局限性，需要 js 实现控制 {:&.moveIn}
- css vs js 动画性能的好坏？
  - 前面的 demo 中 css 使用不当也会导致 app 崩溃 {:&.fadeIn}
  - 还是看使用者的水平，避免频繁 reflow
- **小事八**：尽量只动画 transition 和 opacity，必要时配合 will-change


[slide style="background-image: url('/img/bg22.png')"]
<span class="theme-tag">&middot;不要过度使用动画</span>
## **小事九**：不要过度使用动画
----
> 这听着像设计的任务

- 接受一些有意义的动画 {:&.moveIn}
  - 减少视觉上的冲突 {:&.fadeIn}
  - 可操作交互提醒
  - 突出宣传主题
- 纯粹为了美观的动画就放弃吧


[slide style="background-image: url('/img/bg22.png')"]
## 总结九件小事
----
1. **可以用 scroll-snap 捕捉滚动实现简单轮播效果** {:&.fadeIn}
2. **Transition 仅在样式发生变化时才会运行**
3. **animation-timing-function 只在关键帧之间适用**
4. **animation-timing-function 默认值 ease，自动补间动画**
5. **避免将动画作用于使用了 rem 的伪元素上**
6. **现在可以开始使用 Web Animation API 啦**
7. **Vue transition 中同时使用过渡和动画，可以选择性结束动画**
8. **尽量只动画 transition 和 opacity，必要时配合 will-change**
9. **不要过度使用动画**


[slide style="background-image: url('/img/bg22.png')"]
## 参考文献
----
* Brian Birtles 讲稿<a href="https://birtles.github.io/cssconf2019/index.zh.html#/title" target="_blank">10 THINGSI WISH PEOPLE KNEW ABOUT WEB ANIMATION</a>
* <a href="https://alligator.io/css/scroll-snapping/" target="_blank">Control Page Scroll in CSS Using Scroll Snapping</a>
* <a href="https://developer.mozilla.org/zh-CN/docs/Web/API/Web_Animations_API" target="_blank">Web Animations API</a>
* <a href="https://developer.mozilla.org/zh-CN/docs/Web/API/Web_Animations_API/Using_the_Web_Animations_API" target="_blank">Using the Web Animations API</a>
* <a href="http://www.alloyteam.com/2015/12/web-animation-api-from-entry-to-the-top/" target="_blank">Web Animation API 从入门到上座</a>
* <a href="https://css-tricks.com/css-animations-vs-web-animations-api/" target="_blank">CSS Animations vs Web Animations API</a>
* <a href="https://davidwalsh.name/css-js-animation" target="_blank">CSS vs. JS Animation: Which is Faster?</a>
* <a href="https://www.zhangxinxu.com/wordpress/2018/03/web-animations-api-dynamic-feature-animation/" target="_blank">借助Web Animations API实现JS keyframes动画</a>
* <a href="https://developers.google.com/web/fundamentals/design-and-ux/animations/animations-and-performance?hl=zh-cn#css-vs-javascript-performance" target="_blank">动画与性能</a>
* <a href="https://blog.csdn.net/young_Emily/article/details/80091667" target="_blank">扇形的几种实现方式</a>


[slide style="background-image: url('/img/bg1.jpg')"  data-transition="cover-circle"]
# Thank you

