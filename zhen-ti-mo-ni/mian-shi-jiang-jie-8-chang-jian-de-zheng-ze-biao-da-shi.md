# 面试讲解-8：常见的正则表达式

> 关于作用域和自由变量的场景题 - 1
>
> ```javascript
> let i;
>
> for(i = 1; i <= 3; i++){
>     setTimeout(function() {
>         console.log(i); // 1 2 3
>     }, 0);
> }
>
> // what is i ?
> //   4
> ```

> 关于作用域和自由变量的场景题 - 2
>
> ```javascript
> let a = 100;
>
> function test(){
>     alert(a); // 100
>     a = 10;
>     alert(a); // 10
> }
>
> test();
> alert(a); // 10
>
>
> ```

> 字符串以字母开头 后面是字母数字下划线 长度 6-30

const reg = /^\[a-zA-Z\]\w{5,29}$/

* ^ start              $ end
* \[ ... \] 多选一
* \w - word character -  a character from a-z, A-Z, 0-9, including the \_ \(underscore\) character
* {x,y} 长度 x-y

[More](https://www.w3schools.com/jsref/jsref_obj_regexp.asp)

* 邮政编码 6位数字        /\d{6}/
* 小写英文字母               /^\[a-z\]+$/                                              + 1-more
* 英文字母                       /^\[a-zA-Z\]+$/
* 日期格式   yyyy-mm-dd    /^\d{4}-\d{1,2}-\d{1,2}$/
* 用户名                           /^\[a-zA-Z\]\w{5,17}$/
* 简单的 IP地址              /\d+\.\d+\.\d+\.\d+/





