# 题目讲解-2：手写深度比较 isEqual

> 手写深度比较，模拟 lodash.isEqual

```javascript
// ***** 举例 ***** //
// 有两个对象 里面属性是一样的
const o1 = {a: 10, b: {x: 100, y: 200}};
const o2 = {a: 10, b: {y: 200, x: 100}};

console.log(o1 === o2) // false 因为地址不一样
console.log(isEqual(o1, o2)) // true 这是深度比较


// ***** 深度比较 ***** //
function isObject(obj) {
    return typeof obj === 'object' && obj !== null;
}

// 参与equal的不会是function
function isEqual(obj1, obj2) {
    if (!isObject(obj1) || !isObject(obj2)) { // 值类型 null
        return obj1 === obj2;
    }
    
    // 现在确认是 array / object 
    
    // 检查是否传入同一个参数比较 isEqual(o1, o1)   
    if (obj1 ==== obj2) {
        return true;
    }
    
    // 两个都是对象或数组 而且不是同一个
    // 1. 先取出 obj1 和 obj2 的keys 比较个数
    const obj1Keys = Object.keys(obj1);
    const obj2Keys = Object.keys(obj2);
    if (obj1Keys.length !== obj2Keys.length) {
        return False;
    }
    
    // 2. 以 obj1为基准，和 obj2 依次递归比较
    for (let key in obj1) {
        // 比较 当前key的value
        const res = isEqual(obj1[key], obj2[key]);
        if (!res) {
            return false;
        }
    }
    return true;
}
```

> split\(\)和join\(\)的区别

```javascript
'1-2-3'.split('-'); // [1,2,3]
[1,2,3].join('-');  // '1-2-3'
```

> 数组\(Array\) 的 pop push unshift shift 分别做什么

* 功能是什么?
* 返回值是什么?
* 是否对原数组造成影响？\(mutate\)

```javascript
// pop
var arr = [10, 20, 30, 40];

const popRes = arr.pop();
console.log(popRes); // 40
console.log(arr);    // [10,20,30]


// push
arr = [10, 20, 30, 40];

const pushRes = arr.push(50) // 返回 length
console.log(pushRes); // 5 length
console.log(arr);     // [10,20,30,40,50]

// unshift
arr = [10, 20, 30, 40];

const unshiftRes = arr.unshift(5) // 返回 length
console.log(unshiftRes); // 5 length
console.log(arr);     // [5,10,20,30,40]

// shift 和pop类似 但shift移除头
arr = [10, 20, 30, 40];

const shiftRes = arr.shift() 
console.log(shiftRes); // 10
console.log(arr);     // [20,30,40]

// 以上都不是纯函数 都有副作用 都改变原数组
```

> \[扩展\] 数组\(Array\)的API，有哪些是纯函数

{% hint style="info" %}
**Pure functions** are functions that accept an input and returns a value without modifying any data outside its scope\(**Side Effects**\). Its output or return value must depend on the input/arguments and pure functions must return a value.
{% endhint %}

{% hint style="info" %}
纯函数:

1. 不改变原数组 \(没有副作用\)
2. 返回一个数组
{% endhint %}

```javascript
var arr = [10, 20, 30, 40];

// concat
const arr1 = arr.concat([50, 60, 70]);
console.log(arr);  // [10, 20, 30, 40]
console.log(arr1); // [10,20,30,40,50,60,70]

// map
const arr2 = arr.map(num => num * 10);
console.log(arr);  // [10, 20, 30, 40]
console.log(arr2); // [100,200,300,400]

// filter
const arr3 = arr.filter(num => num > 25);
console.log(arr);  // [10, 20, 30, 40]
console.log(arr3); // [30,40]

// slice
const arr4 = arr.slice();
console.log(arr);  // [10, 20, 30, 40]
console.log(arr4); // [10, 20, 30, 40]
```

非纯函数: 

* push pop shift unshift 
* forEach 没有返回值 
* some every 不返回
* reduce 不返回

