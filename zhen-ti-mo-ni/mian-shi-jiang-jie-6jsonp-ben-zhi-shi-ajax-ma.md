# 面试讲解-6：jsonp 本质是 ajax 吗

> 解释 jsonp 的原理 为何他不是真正的ajax?

* 浏览器的同源策略 （服务端没有同源策略）和 跨域
* 哪些html标签能绕过跨域
* [jsonp的原理](../js-web-api/11.-ajax/11.3-kua-yu.md#jsonp)

> document load 和 ready 的区别

* load                                  页面的全部资源加载完才会执行
* DOMContentLoaded     DOM渲染完立刻执行

> === vs ==

* ==会尝试类型转换
* ===严格相等
* 哪些场景用==？

