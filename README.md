---
description: >-
  这是我准备Frontend Developer面试的基础笔记 是跟着慕课网的课程进行的准备 - 快速搞定前端技术一面 匹配大厂面试要求
  https://coding.imooc.com/class/400.html
---

# 课程大纲

## 几个面试题

> typeof 能判断哪些类型

考点：变量类型

> === vs ==

考点： 强制类型转换

> window.onload vs DOMContentLoaded

> 为什么把css放在head里 把script放在body最底下

考点: 页面加载过程

> JS 创建10个\标签， 点击的时候弹出对应序号

考点: JS作用域 \(比如，闭包\)

> 手写节流 throttle vs 防抖 debounce

考点：性能, 体验优化

> Promise 解决什么问题

考点： JS异步

{% hint style="info" %}
* 拿到面试题第一时间看到的是什么\(==考点==\)
* 如何看待永远做不完的题海 \(==以不变应万变 题变考点不变==\)
* 如何对待接下来遇到的面试题？\(==总结考点并扩展再反思题目==\)
{% endhint %}

## 前端知识体系

从哪些方面梳理

* W3C
* ECMA 262
* 开发环境
* 运行环境

**知识体系**

* CSS基础知识
  * 布局
    * 盒模型
    * BFC
    * float
    * flex
  * 定位
  * 图文样式
  * 移动端响应式
    * rem
    * media query
    * vw/vh
  * 动画/渐变
* JS基础知识
  * [变量类型和计算](undefined/3.-bian-liang-lei-xing-he-ji-suan/)
    * [值类型和引用类型](undefined/3.-bian-liang-lei-xing-he-ji-suan/3.1-bian-liang-lei-xing.md)
    * [类型判断 typeof](undefined/3.-bian-liang-lei-xing-he-ji-suan/3.2-typeof.md)
    * [逻辑运算](undefined/3.-bian-liang-lei-xing-he-ji-suan/3.4-bian-liang-ji-suan-qiang-zhi-lei-xing-zhuan-huan.md#if-yu-ju-he-luo-ji-yun-suan)
  * [原型和原型链](undefined/prototype/)
    * [class](undefined/prototype/4.1-class-and-inheritance.md#class)
    * [继承](undefined/prototype/4.1-class-and-inheritance.md#inheritance)
    * [原型](undefined/prototype/4.3-prototype-and-prototype-chain.md#prototype-yuan-xing)
    * [原型链](undefined/prototype/4.3-prototype-and-prototype-chain.md#prototype-chain-yuan-xing-lian)
    * [instanceof](undefined/prototype/4.2-instanceof.md)
  * [作用域 闭包](undefined/5.-zuo-yong-yu-he-bi-bao-2/)
    * [作用域](undefined/5.-zuo-yong-yu-he-bi-bao-2/5.1-zuo-yong-yu.md)
    * [自由变量](undefined/5.-zuo-yong-yu-he-bi-bao-2/5.2-zi-you-bian-liang.md)
    * [闭包](undefined/5.-zuo-yong-yu-he-bi-bao-2/5.3-bi-bao.md) 
    * [this](undefined/5.-zuo-yong-yu-he-bi-bao-2/5.4-this.md)
  * [异步](undefined/6.-yi-bu-3/)
    * [单线程](undefined/6.-yi-bu-3/6.1-dan-xian-cheng-he-yi-bu.md)
    * [callback](undefined/6.-yi-bu-3/6.4-callback-hell-he-promise.md)
    * [应用场景](undefined/6.-yi-bu-3/6.3-ying-yong-chang-jing.md)
    * [promise](undefined/7.-yi-bu-jin-jie/7.2-promise.md)
    * [event-loop](undefined/7.-yi-bu-jin-jie/7.1-event-loop.md)
    * [async/await](undefined/7.-yi-bu-jin-jie/7.3-async-await.md)
    * [微任务/宏任务](undefined/7.-yi-bu-jin-jie/7.5-hong-ren-wu-he-wei-ren-wu.md)
  * 模块化
    * ES6 Module
* JS WEB API
  * [DOM](js-web-api/untitled/)
    * [树形结构](js-web-api/untitled/8.1-dom-ben-zhi.md)
    * [节点操作](js-web-api/untitled/8.2-dom-jie-dian-cao-zuo.md)
    * [属性](js-web-api/untitled/8.2-dom-jie-dian-cao-zuo.md)
    * [树结构操作](js-web-api/untitled/8.3-dom-jie-gou-cao-zuo.md)
    * [性能](js-web-api/untitled/8.4-dom-xing-neng.md)
  * [BOM](js-web-api/9.-bom/)
    * [navigator](js-web-api/9.-bom/9.1-navigator.md)
    * [screen](js-web-api/9.-bom/9.2-screen.md)
    * [location](js-web-api/9.-bom/9.3-location.md)
    * [history](js-web-api/9.-bom/9.4-history.md)
  * [事件](js-web-api/10.-shi-jian/)
    * [绑定](js-web-api/10.-shi-jian/10.1-shi-jian-bang-ding.md)
    * [冒泡](js-web-api/10.-shi-jian/10.2-shi-jian-mao-pao.md)
    * [代理](js-web-api/10.-shi-jian/10.3-shi-jian-dai-li.md)
  * [ajax](js-web-api/11.-ajax/)
    * [XML HttpRequest](js-web-api/11.-ajax/11.1-xmlhttprequest-1.md)
    * [状态码](js-web-api/11.-ajax/11.2-zhuang-tai-ma.md)
    * [跨域](js-web-api/11.-ajax/11.3-kua-yu.md)
  * [存储](js-web-api/12.-cun-chu/)
    * [cookie](js-web-api/12.-cun-chu/12.1-cookie.md)
    * [localStorage](js-web-api/12.-cun-chu/12.2-localstorage-and-sessionstorage.md)
    * [sessionStorage](js-web-api/12.-cun-chu/12.2-localstorage-and-sessionstorage.md)
* [开发环境](kai-fa-huan-jing/untitled/)
  * [git](kai-fa-huan-jing/untitled/14.1-git.md)
  * [调试](kai-fa-huan-jing/untitled/14.2-chrome-tiao-shi-gong-ju.md)
  * [webpack 和 babel](kai-fa-huan-jing/untitled/14.4-webpack-he-babel.md)
  * [linux 命令](kai-fa-huan-jing/untitled/14.6-linux-chang-yong-ming-ling.md)
* [运行环境](yun-hang-huan-jing/untitled/)
  * [页面加载](yun-hang-huan-jing/untitled/15.1-wang-ye-jia-zai-guo-cheng.md)
    * [加载](yun-hang-huan-jing/untitled/15.1-wang-ye-jia-zai-guo-cheng.md#jia-zai-zi-yuan-de-xing-shi)
    * [渲染](yun-hang-huan-jing/untitled/15.1-wang-ye-jia-zai-guo-cheng.md#xuan-ran-ye-mian-de-guo-cheng)
  * [性能优化](yun-hang-huan-jing/untitled/15.2-xing-neng-you-hua.md)
    * [加载资源优化](yun-hang-huan-jing/untitled/15.2-xing-neng-you-hua.md#rang-jia-zai-geng-kuai)
    * [渲染优化](yun-hang-huan-jing/untitled/15.2-xing-neng-you-hua.md#rang-xuan-ran-geng-kuai)
  * [安全](yun-hang-huan-jing/untitled/15.3-an-quan.md)
    * XSS
    * XSRF
* [HTTP 协议](http/13.-http/)
  * [状态码](http/13.-http/13.1-http-zhuang-tai-ma.md)
  * [method](http/13.-http/13.2-http-methods.md)
  * [Restful API](http/13.-http/13.3-restful-api.md)
  * [headers](http/13.-http/13.4-http-headers.md)
  * [缓存策略](http/13.-http/13.5-http-caching.md)

