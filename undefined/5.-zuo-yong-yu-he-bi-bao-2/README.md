# 5. 作用域和闭包 🗻2️⃣



> this 的不同应用场景，如何取值？

> 手写bind
>
> **Soln**: Bind 举例:
>
> ```javascript
> function fn1(a, b, c) {
>   console.log(this);
>   console.log(a, b, c);
>   return "this is fn1";    
> }
> const fn2 = fn1.bind({x: 100}, 10, 20, 30);
> console.log(fn2); // {x: 100}
>                   // 10 20 30
>                   // "this is fn1"
> ```
>
> 现在 手写bind:
>
> ```javascript
> Function.prototype.bind1 = function() {
>
>   // 将参数拆解为数组 array
>   const args = Array.prototype.slice.call(arguments);
>
>   // 获取this (数组第一项)
>   const t = args.shift() // shift 取第一项并且remove
>   
>   // fn1.bind1(...) 中的 fn1
>   const self = this
>   
>   // 返回一个函数
>   return function() {
>       return self.apply(t, args);
>   }
> }
> ```

> 闭包在实际开发中的应用场景，举例说明
>
> **Soln**:
>
> * 隐藏数据
> * 做一个简单的cache工具
>
> ```javascript
> // 闭包隐藏数据, 只提供API
> function createCache() {
>   const data = {}; // 闭包中的数据，被隐藏，不让外界访问
>   return {
>       set: function(key, val){
>           data[key] = val;
>
>       },
>       get: function(key) {
>           return data[key];
>       }
>   }
> }
>
> const c = createCache();
> c.set("a", 100);
> console.log(c.get("a")); // 100
>
> data.b = 200 // error
> ```

> 创建10个`<a>`标签， 点击的时候弹出来对应序号
>
> **Soln**:
>
> ```javascript
> let a;
> for (let i = 0; i < 10, i++) {
>   a = document.createElement("a");
>   a.innerHTML = i + "<br>";
>   a.addEventListener("click", function(e) {
>       e.preventDefault();
>       alert(i);
>   })    
>   document.body.appendChild(a);
> }
> // 这里把let i 放在for loop， 产生 block scope， 点a对应0-9
> ```

