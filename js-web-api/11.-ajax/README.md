# 11. Ajax

> 常用的ajax工具
>
> **Soln**:
>
> * jquery.ajax\(\)
> * fetch api
> * axios

> 手写一个简易的ajax
>
> **Soln**:
>
> ```javascript
> function ajax(url, successFn) {
>   const xhr = new XMLHttpRequest();
>   xhr.open("GET", url, true);
>   xhr.onreadystatechange = function () {
>       if (xhr.readystate === 4) {
>           if (xhr.status === 200) {
>               successFn(xhr.responseText);
>           }
>       } else if (xhr.status === 404) {
>           console.log("404 not found");
>       }
>   }
>   xhr.send(null);
> }
> ```
>
> 或者
>
> ```javascript
> function ajax(url) {
>   const p = new Promise((resolve, reject) => {
>       const xhr = new XMLHttpRequest();
>       xhr.open("GET", url, true);
>       xhr.onreadystatechange = function () {
>           if (xhr.readystate === 4) {
>               if (xhr.status === 200) {
>                   resolve(JSON.parse(xhr.responseText));
>               } else if (xhr.status === 404) {
>                   reject(new Error("404 not found"));
>               }
>           }
>       }
>       xhr.send(null);
>   })
>   return p;
> }
>
> const url = "/data/test.json"; // {name: "rdr"}
>
> ajax(url)
> .then(res => console.log(res)) // {name: "rdr"}
> .catch(err => console.error(err));
> ```

> 跨域的常用方式
>
> **Soln**:
>
> * JSONP \(client\)
> * CORS \(server\)

