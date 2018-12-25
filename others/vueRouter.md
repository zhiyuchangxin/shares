title: vue-router 源码解析
speaker: zhiyuchangxin
utl: https://github.com/zhiyuchangxin/shares
transition: slide2
files: /css/index.css
theme: moon
date: 2018-09-14

[slide style="background-image: url('/img/bg22.jpg')"]
# vue-router 源码解析
<br/>
@织语长心&nbsp;&nbsp;2018-11-19

[slide style="background-image: url('/img/bg22.jpg')"]
## 切入点
----
<img src="/img/module.png" class="seven-module"> {:&.fadeIn}
* 重新探索自我 {:&.moveIn}
  - 由内而外全面造就自己 {:&.fadeIn}
  - 七个习惯概念
* 个人领域的成功
  - 积极主动 {:&.fadeIn}
  - 以终为始
  - 要事第一

[slide style="background-image: url('/img/bg22.jpg')"]
## 目录结构
----
1. test
2. test

[slide style="background-image: url('/img/bg22.jpg')"]
## 作为插件安装
----

Vue 安装插件都做了什么？ {:&.flexbox.vleft}

```js
  Vue.use = function (plugin: Function | Object) {
    // ...
    if (typeof plugin.install === 'function') {
        plugin.install.apply(plugin, args)
    } else if (typeof plugin === 'function') {
        plugin.apply(null, args)
    }
    // ...
  }
```

1. `Vue.js` 通过 `Vue.use(plugin)` 来安装插件 {:&.moveIn}
2. 会调用 plugin 的 `install` 方法,
3. 如果没有该方法, 则将 `plugin` 本身作为函数来调用
4. 安装 vue-router 做了三件事：
  - 通过全局的混合方式来初始化 `VueRouter` {:&.fadeIn}
  - 给当前应用下的所有组件注入 `$router` 和 `$route` 对象
  - 提供 `<router-view>` 和 `<router-link>` 组件

[slide style="background-image: url('/img/bg22.jpg')"]
## Router 实例化
----

* 在入口文件中，首先要实例化一个 VueRouter ，然后将其传入 Vue 实例的 options 中 {:&.moveIn}
* VueRouter 类做了两件事：
  * 创建 matcher 对象 {:&.fadeIn}
  * 创建 history 实例


[slide style="background-image: url('/img/bg22.jpg')"]
### 路由匹配
----

* 创建 matcher 对象 {:&.moveIn}
* 创建 history 实例


[slide style="background-image: url('/img/bg13.jpg')"  data-transition="cover-circle"]
# Thank you
