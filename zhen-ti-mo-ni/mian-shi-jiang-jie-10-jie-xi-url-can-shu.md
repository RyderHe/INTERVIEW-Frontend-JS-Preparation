# 面试讲解-10：解析 url 参数

> 如何捕获JS程序中的异常

```javascript
// 方法 1： try ... catch
try {
     // todo
} catch (err) {
     console.error(err);
} finally {
     // finally todo
}

// 方法2：自动捕获异常
window.onerror = function(message, source, lineNum, colNum, error){
     // 1. 对跨域的 js，如 CDN，不会有详细的报错信息
     // 2. 对于压缩的 js，还要配合 sourceMap 反查到未压缩代码的行、列
}
```

> 什么是JSON？

* json 是一种数据格式 本质是一段 字符串
* json 格式和JS对象结构一致，对JS语言更友好
* JSON is text, written with JavaScript object notation.
* window.JSON是一个全局对象：JSON.stringify JSON.parse

```javascript
{
    "name": "haha",
    "info": {
        "age": ,
        "city": "waterloo"
    },
    "like": "movies"
}
```

> 获取当前页面 url参数

* 传统方式：location.search

```javascript
function query(name){
    // location.search returns sth like "?a=2&b=100&c=mr"
    const search = location.search.substr(1); // 类似 array.slice
    // search === "a=2&b=100&c=mr"
    
    const reg = new RegExp(`(^|&)${name}=([^&]*)(&|$)`, 'i'); // [^&] - no &
    // i 大小写不区分
    
    const res = search.match(reg); // return array
    
    if (res === null) {
        return null;
    }
    return res[2];
}
query('a'); // 2
```

* 新API: URLSearchParams

```javascript
function query(name){
    // location.search returns sth like "?a=2&b=100&c=mr"
    const search = location.search;
    const p = new URLSearchParams(search);
    return p.get(name);
}

query('a'); // 2
```

