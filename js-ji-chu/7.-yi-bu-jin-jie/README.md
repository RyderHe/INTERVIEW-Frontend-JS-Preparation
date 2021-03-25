# 7. 异步进阶 🚀



> 描述 event-loop \(事件循环/事件轮询\) 的机制, 可画图
>
> **Soln**:
>
> * event-loop的过程
> * 和DOM渲染的关系
> * 微任务和宏任务在event loop过程中的不同处理

> 什么宏任务和微任务？两者有什么区别？
>
> **Soln**:
>
> * 宏任务: setTimeout, setInterval, Ajax, DOM事件
> * 微任务: Promise, async/await
> * 区别
>   * 微任务比宏任务执行时间早
>   * 微任务在DOM渲染之前; 宏任务在DOM渲染之后

> Promise 有哪三种状态？ 如何变化？
>
> **Soln**:
>
> * 状态： 1. pending 2. resolved 3. rejected
> * 变化:
>   * pending -&gt; resolved
>   * pending -&gt; rejected
>   * 变化不可逆
>   * resolve会触发then的回调；rejected会触发catch的回调

> Promise - then 和 catch 的连接
>
> 场景1：
>
> ```javascript
> Promise.resolve().then(() => {// promise.resolve()执行完 状态是resolved
>   console.log(1); 
> }).catch(() => { // 第一个then执行完 状态是resolved 所以catch不会被执行
>   console.log(2);
> }).then(() => {
>   console.log(3);
> }); // 最终状态resolved
> ```
>
> **Soln**: 1 3

> Promise - then 和 catch 的连接
>
> 场景2：
>
> ```javascript
> Promise.resolve().then(() => { // promise.reolve()执行完状态是resolved
>   console.log(1);
>   throw new Error("error1"); // 报错 
> }).catch(() => {  // 第一个then执行完 状态是 rejected -> catch
>   console.log(2);
> }).then(() => { // catch执行完 状态是 resolved -> then
>   console.log(3);
> }); // 最终状态 resolved
> ```
>
> **Soln**: 1 2 3

> Promise - then 和 catch 的连接
>
> 场景3：
>
> ```javascript
> Promise.resolve().then(() => { // promise.resolve执行完状态是 resolved
>   console.log(1);
>   throw new Error("error1"); // 报错
> }).catch(() => { // 第一个then执行完 状态是 rejected -> 触发 catch 回调
>   console.log(2);
> }).catch(() => { // catch执行完 状态是 resolved -> 触发 then 回调
>   console.log(3);
> });
> ```
>
> **Soln**: 1 2

> async/await 语法
>
> 场景1：
>
> ```javascript
> async function fn() {
>   return 100;
> }
> (async function() {
>   const a = fn(); // ?
>   const b = await fn(); // ?
> })();
> ```
>
> **Soln**: 
>
> a = Promise.resolve\(100\)     因为 async return promise 
>
> b = 100                                    因为 await 相当于 promise的then

> async/await 语法
>
> 场景2：
>
> ```javascript
> (async function() {
>   console.log("start");
>   const a = await 100; // await 相当于 Promise then
>   console.log("a", a);
>   const b = await Promise.resolve(200);
>   console.log("b", b);
>   const c = await Promise.reject(300); // 报错
>   console.log("c", c);
>   console.log("end");
> })();
> ```
>
> **Soln**: 打印顺序:
>
> start
>
> a 100
>
> b 200

> Promise 和 setTimeout 的顺序
>
> 场景：
>
> ```javascript
> console.log(100);
>
> // 宏任务
> setTimeout(() => { 
>   console.log(200); // callback function
> });
>
> // 微任务
> Promise.resolve().then(() => {
>   console.log(300); // callback function
> });
> console.log(400);
> ```
>
> **Soln**: 100 400 \| 300 200 
>
> 一行一行执行，遇到callback function先存储起来 不执行
>
>  等到call stack 空了， 再依次执行 callback 
>
> 微任务比宏任务执行早 所以300在 200前

> async/await 的顺序
>
> 场景:
>
> ```javascript
> async function async1() {
>   console.log("async1 start"); // 2
>   await async2();
>   // await 后面的都是回调内容 - 微任务
>   console.log("async1 end"); // 6
> }
> async function async2() {
>   console.log("async2"); // 3
> }
>
> console.log("script start"); // 1
>
> setTimeout(function() { // 宏任务 setTimeout
>   console.log("setTimeout"); // 8
> }, 0);
>
> async1();
>
> // 初始化 Promise时， 传入的函数会立刻被执行
> new Promise(function(resolve) {
>   console.log("promise1"); // 4
>   resolve(); // resolved
> }).then(function( { // 微任务
>   console.log("promise2"); // 7
> }))
>
> console.log("script end"); // 5
> // 同步代码执行完毕 (event loop - call stack 被清空)
> //   现在， 先执行微任务
> //   再尝试触发DOM渲染
> //   最后触发 event loop机制， 执行宏任务
> ```
>
> **Soln**: 
>
> script start
>
> async1 start
>
> async2
>
> promise1
>
> script end
>
> async1 end
>
> promise2
>
> setTimeout

