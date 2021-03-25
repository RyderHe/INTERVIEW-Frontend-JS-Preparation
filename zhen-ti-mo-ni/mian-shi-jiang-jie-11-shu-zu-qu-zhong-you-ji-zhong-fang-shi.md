# 面试讲解-11：数组去重有几种方式？

> 将 url参数解析为JS对象

```javascript
// 方法 1：
function queryToObj(){
    const res = {};
    const serach = location.search.sybstr(1); // 去掉前面的？
    search.split('&').forEach(paramStr => {
        const arr = paramStr.split('=');
        const key = arr[0];
        const val = arr[1];
        res[key] = val;
    })
    
    return res;
}

// 方法 2：URLSearchParams
function queryToObj(){
    const res = {};
    const pList = new URLSearchParams(location.search);
    pList.forEach((val, key) => {
        res[key] = val;
    })
    return res;
}
```

> 手写数组 flatern 考虑多层级

```javascript
flat([[1,2],3,[4,5,[6,7,[8,9,[10,11]]]]]) // [1,2,3,4,5,6,7,8,9,10,11]
```

```javascript
function flat(arr){
    // 验证 arr中 还有没有深层数组 [1,2,[3,4]]
    const isDeep = arr.some(item => item instanceof Array);
    if (!isDeep){
        retun arr; // 已经 flatten [1,2,3,4]
    }
    
    const res = Array.prototype.concat.apply([], arr); // [].apply(arr)  
    
    return flat(res); // 递归
}

const res = flat([1,2,[3,4],5]);
console.log(res);
```

> 数组去重

* 传统方式：遍历元素挨个比较 去重
* 使用 set
* 考虑计算效率

```javascript
// 方法 1：传统方式 - 遍历两次 - O（n^2）
function unique(arr){
    const res = [];
    
    arr.forEach(item => { 
        if (res.indexOf(item) < 0) { // indexOf 也用遍历
            res.push(item);
        }
    })
    
    return res;
}

// 方法 2： set - 无顺序 不能重复 - O(n)
function unique(arr){
    const set = new Set(arr);
    return [...set];
}
```

