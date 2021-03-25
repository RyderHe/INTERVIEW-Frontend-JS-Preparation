# 面试讲解-7：是否用过 Object.create\(\)

> 函数声明和函数表达式的区别

* 函数声明 function fn\(\){...}
* 函数表达式 const fn = function\(\){...}
* 函数声明会在代码执行前预加载 而函数表达式不会

```javascript
const res = sum(10, 20);
console.log(res); // 30

// 函数声明
function sum(x,y) {
    return x + y;
}

// 这里 和 变量提升 var 类似
```

```javascript
const res = sum(10, 20);
console.log(res); // error

// 函数表达式
const sum = function (x,y) { // 改成var 上面sum就是undefined -> 变量提升
    return x + y;
}
```

> new Object\(\) 和 Object.create\(\)的区别

* {} 等同于 new Object\(\), 原型是Object.prototype
* Object.create\(null\) 没有原型
* Object.create\({...}\) 可指定原型 - 传入什么 原型是什么

```javascript
const obj1 = {
    a: 10,
    b: 20
};

const obj2 = new Object({ // obj1 !== obj2
    a: 10,
    b: 20
});

const obj3 = newObject(obj1); // obj1 === obj3

const obj4 = Object.create(null); // {} 没有原型
const obj5 = new Object(); // {} 有原型

const obj6 = Object.create({
    a: 10,
    b: 20
}); // {} 原型是 a: 10,
    //          b: 20
    
const obj7 = Object.create(obj1); // {} 原型是 obj1
// obj7.__proto__ === obj1
// obj7 !== obj1
```

> 关于this的场景题
>
> ```javascript
> const User = {
>     count: 1,
>     getCount: function() {
>         return this.count;
>     }
> };
>
> // this的值在执行的时候才知道
>
> console.log(User.getCount()); // ??  this 是User 打印1
>
> const func = User.getCount;
> console.log(func()); // ?? this是window 打印undefined
> ```

