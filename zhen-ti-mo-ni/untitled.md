# 题目讲解-1：何为变量提升？

> var 和 let const 区别

* var是ES5语法；let const 是ES6语法；var有变量提升
* var和let是变量，可修改；const是变量，不可修改
* let const是block scope；var不是block scope

```javascript
// 变量提升 ES5
console.log(a); // undefined
var a = 20;

// 在ES5中，以上等于
var a;
console.log(a);
a = 20;

console.log(b); // error: b is not defined
let b = 20;
```

```javascript
// 块级作用域 Block Scope

// var 没有 block scope
for (var i = 0; i < 10; i++) {
    var j = i + 1;
}

console.log(i, j); // 10 10

// let 有 block scope
for (let i = 0; i < 10; i++) {
    let j = i + 1;
}

console.log(i, j); // error: i is not defined
```

> typeof 返回哪些类型

* all primitive type \(值类型\): number, string, symbol, boolean, undefined, bigint
* object \(注意 type of null === 'object'\)
* function

> 列举 强制类型转换 和 隐式类型转换

* 强制: parseInt parseFloat toString
* 隐式: if、逻辑运算、==、+拼接字符串

