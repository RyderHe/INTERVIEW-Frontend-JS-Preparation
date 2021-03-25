# 面试讲解-12：是否用过 requestAnimationFrame

> 手写深拷贝

* 判断 object
* 判断 array 还是 object
* recursion

{% hint style="info" %}
Object.assign    不是深拷贝！！！
{% endhint %}

> 介绍 RAF requestAnimationFrame

* 要想动画流畅 更新频率要60帧/秒 即16.67ms更新一次试图
* setTimeout 要手动控制频率     而 RAF浏览器会自动控制
* 后台标签或隐藏iframe中 RAF会暂停 而setTimeout依然执行

```javascript
// 3s 把宽度从100px 变为 640px，即增加540px
// 60帧/s 3s180帧 180次变化 每次变化3px

const $div1 = $('#div1'); // jquery
let curWidth = 100;
const maxWidth = 640;

// setTimeout
function animate() {
    curWidth = curWidth + 3;
    $div1.css('width', curWidth);
    if (curWidth < maxWidth) {
        setTimeout(animate, 16.7); // 问题：自己控制时间
    }
}

animate();

// RAF
function animate() {
    curWidth = curWidth + 3;
    $div1.css('width', curWidth);
    if (curWidth < maxWidth) {
        window.requestAnimationFrame(animate); // 时间不用自己控制 浏览器控制
    }
}
animate();
```

> 前端性能如何优化？一般考虑几个方面？

* 原则: 多使用内存、缓存 减少计算 减少网络请求
* 方向：加载页面 页面渲染 页面操作流畅度

