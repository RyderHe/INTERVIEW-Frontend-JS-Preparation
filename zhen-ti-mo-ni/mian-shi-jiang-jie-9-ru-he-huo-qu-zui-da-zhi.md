# 面试讲解-9：如何获取最大值

> 手写    字符串 trim 方法 保证浏览器兼容性

```javascript
String.prototype.trim = function(){
    return this.replace(/^\s+/, '').replace(/\s+$/, '');
                // trimLeft             trimRight
}
```

> 如何获取多个数字中的最大值

```javascript
// 方法 1
function max() {
    const nums = Array.prototype.slice.call(arguments); // 变成 array
    let max = 0;
    nums.forEach(n => {
        if (n > max) {
            max = n;
        }
    })
    return max;
}

// 方法 2
Math.max(10,30,20,40); // Math.min
```

> 如何用JS实现继承

* class 继承
* prototype 继承 （不推荐 ES5）

