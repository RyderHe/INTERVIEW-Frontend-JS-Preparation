---
description: Prototype & Prototype Chain
---

# 4. 原型和原型链 🗻1️⃣

{% hint style="info" %}
class 是ES6的语法规范
{% endhint %}

> 如何判断一个变量是不是数组\(Array\)？
>
> **Soln**: a instanceof Array

> class的原型本质？
>
> **Soln**: 
>
> * 原型和原型链图示
> * 属性和方法的执行规则

> 继承class的本质？
>
> **Soln**: 
>
> * 原型和原型链图示
> * 属性和方法的执行规则

> 手写一个jQuery, 考虑插件和扩展性
>
> **Soln**:
>
> ```javascript
> class jQuery {
>    constructor(selector) {
>        const result = document.querySelectorAll(selector);
>        const length = result.length;
>        for (let i = 0; i < length; i++) {
>           this[i] = result[i];    
>        }
>        this.length = length;
>        this.selector = selector;
>    }
>    get(index) {
>       return this[index];
>    }
>    each(fn) {
>       for (let i = 0; i < this.length; i++) {
>           const elem = this[i];
>           fn(elem);
>       }
>    }
>    on(type, fn) {
>       return this.each(elem => {
>           elem.addEventListener(type, fn, false);
>       })
>    }
> }
>
> // 插件
> jQuery.prototype.diag = function(info) {
>   alert(info);
> }
>
> // “造轮子”
> class MyJQuery extends JQuery {
>   constructor(selector) {
>       super(selector);
>   }
>   
>   // 扩展method
>   addClass(className) {
>       // ... 
>   }
>
>   style(data) {
>       // ... 
>   } 
> }
> ```

