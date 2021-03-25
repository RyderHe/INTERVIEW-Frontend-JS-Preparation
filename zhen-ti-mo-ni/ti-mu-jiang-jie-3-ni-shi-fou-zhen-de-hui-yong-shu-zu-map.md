# 题目讲解-3：你是否真的会用数组 map

> 数组 slice 和 splice 的区别

* 功能区别 \(slice - 切片 splice - 剪接\)
* 参数和返回值
* 是否纯函数？

```javascript
var arr = [10, 20, 30, 40, 50];

// slice 纯函数
const arr1 = arr.slice();
console.log(arr);  // [10, 20, 30, 40, 50]
console.log(arr1); // [10, 20, 30, 40, 50]

const arr2 = arr.slice(1,4);
console.log(arr2); // [20, 30, 40]

const arr3 = arr.slice(2);
console.log(arr3); // [30, 40, 50]

const arr4 = arr.slice(-2);
console.log(arr4); // [40, 50]

// splice 非纯函数

// 剪接
const spliceRes1 = arr.splice(1, 2, 'a', 'b', 'c'); // starting index 1, length 2
console.log(arr);       // [10, 'a', 'b', 'c', 40, 50]
console.log(spliceRes1); // [20,30]

// 只想剪掉 不想增加
arr = [10, 20, 30, 40, 50];
const spliceRes2 = arr.splice(1, 2); // starting index 1, length 2
console.log(arr);       // [10, 40, 50]
console.log(spliceRes2); // [20,30]

// 只想增加 不想剪
arr = [10, 20, 30, 40, 50];
const spliceRes3 = arr.splice(1, 0, 'a', 'b', 'c'); 
console.log(arr);       // [10, 'a', 'b', 'c', 20, 30, 40, 50]
console.log(spliceRes3); // []
```

> \[10,20,30\].map\(parseInt\) 返回什么

* map的参数和返回值
* parseInt的参数和返回值
  * 参数
    * string:  The value to parse. If this argument is not a string, then it is converted to one using the [`ToString`](https://tc39.es/ecma262/#sec-tostring) abstract operation.
    * radix \(optional\):  An integer between `2` and `36` that represents the _radix_ \(the base in mathematical numeral systems\) of the `string`. 0 = 10进制
  * 返回值
    * An integer parsed from the given `string`.

      Or [`NaN`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/NaN) when

      * the `radix` is smaller than `2` or bigger than `36`, or
      * the first non-whitespace character cannot be converted to a number.

```javascript
const res = [10, 20, 30].map(parseInt);
console.log(res); // [10, NaN, NaN]

// 拆解
[10,20,30].map((num, index) => {
    return parseInt(num, index);
})

parseInt(10, 0) // 10
parseInt(20, 1) // no such radix => NaN
parseInt(30, 2) // Digits other than 0 or 1 are invalid for binary radix => NaN
```

举一反三:                \['1', '7', '11'\].map\(parseInt\)            返回 \[1,Nan, 3\]

> ajax 请求get和post的区别

* get 请求一般用于查询；post一般用于用户提交操作
* get参数拼接在url上；post放在请求body内 （数据体积可更大）
* 安全性: post易于防止 CSRF

