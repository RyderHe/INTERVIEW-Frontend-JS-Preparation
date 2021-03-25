---
description: Asynchronous
---

# 6. 异步 🗻3️⃣

> 同步 synchronous vs 异步 asynchronous
>
> **Soln**: 
>
> * 异步不会阻塞代码执行
> * 同步会阻塞代码执行

> 手写用promise加载一张图片
>
> **Soln**:
>
> [对比async/await写法🛩 ](../7.-yi-bu-jin-jie/7.3-async-await.md)
>
> ```javascript
> function loadImg(src) {
>   const p = new Promise((resolve, reject) => {
>       const img = document.createElement("img");
>       img.onLoad = () => { // 这里也可以用addEventListener
>           resolve(img);
>       }
>       img.onerror = () => {
>           const err = new Error("图片加载失败");
>           reject(err);
>       }
>       img.src = src;
>   });
>   return p;
> }
>
> const url1 = "https://avatars.githubusercontent.com/RyderHe";
> loadImg(url1).then(img => {
>   console.log(img.width);
>   return img;
> }).then(img => {
>   console.log(img.height);  
> }).catch(err => {
>   console.log(err);
> });
>
> const url2 =  "https://avatars.githubusercontent.com/kimberly332";
> loadImg(url1).then(img1 => {
>   console.log(img1.width);
>   return img1; // 普通对象
> }).then(img1 => {
>   console.log(img1.height);
>   return loadImg(url2); // promise
> }).then(img2 => {
>   console.log(img2.width);
>   return img2;
> }).then(img2 => {
>   console.log(img2.height);
> }).catch(err => {
>   console.log(err);
> })
> ```

> 前端使用异步的场景
>
> **Soln**:
>
> * 网络请求 \(ajax, 图片加载\)
> * 定时任务 （setTimeout, setInterval\)

> 代码题: 以下代码的打印顺序
>
> ```javascript
> consoel.log(1);
> setTimeOut(function() {
>    console.log(2);
> }, 1000 )
> console.log(3);
> setTimeOut(function() {
>   console.log(4);
> }, 0 )
> console.log(5);
> ```
>
> **Soln**: 1 3 5 4 2

