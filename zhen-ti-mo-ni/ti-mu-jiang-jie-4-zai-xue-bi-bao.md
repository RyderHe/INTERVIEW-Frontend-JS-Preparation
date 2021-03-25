# 题目讲解-4：再学闭包

> 函数 call 和 apply 的区别

```javascript
// 区别在于 参数
fn.call(this, p1, p2, p3) 
fn.apply(this, arguments) // 参数用array传递
```

> 事件代理\(委托\)是什么?

```javascript
const p1 = document.getElementById('p1');
const body = document.body;

bindEvent(p1, 'click', e => {
    e.stopPropagation(); // 注释掉这一行 来体会事件冒泡
    alert('激活');
})

bindEvent(body, 'click', e => {
    alert('取消');
})
```

[🎥 回顾事件代理](../js-web-api/10.-shi-jian/10.3-shi-jian-dai-li.md)

> 闭包是什么，有什么特性？有什么负面影响？

* 回顾作用域和自由变量
* 回顾闭包应用场景：函数作为参数被传递 ， 函数作为返回值被传递
* 回顾：自由变量的查找 要在函数定义的地方 （而非执行的地方）
* 对比: this 是在执行的地方
* 影响：变量会常驻内存 得不到释放。闭包不要乱用

```javascript
// 自由变量示例 -- 内存会被释放
let a = 0;

function fn1() {
    let a1 = 100;
    
    function fn2() {
        let a2 = 200;
        
        function fn3() {
            let a3 = 300;
            return a + a1 + a2  a3; // 1. a3 被释放
        }
        fn3(); // 2. a2 fn3 被释放
    }
    fn2(); // 3. a1 fn2 被释放
}

fn1(); // 4. a fn1 被释放
```

```javascript
// 闭包 函数作为返回值 -- 内存不会被释放
function create() {
    let a = 100;
    return function() {
        console.log(a);
    }
}

let fn = create(); // a=100 不能被释放 因为 return 一个函数 包含 a
let a = 200; 
fn(); // 100

// **************

function print(fn) {
    let a = 200; 
    fn();
}

let a = 100; // a=100 不能被释放 因为 fn 包含 a
function fn() {
    console.log(a);
}

print(fn); // 100
```

