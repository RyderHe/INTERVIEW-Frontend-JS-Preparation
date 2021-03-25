# 9. BOM

DOM: Document Object Model

BOM: Browser Object Model

> 如何识别浏览器类型
>
> **Soln :**
>
> ```javascript
> const ua = navigator.userAgent; // get browser's info
> const isChrome = ua.indexOf("Chrome");
> console.log(isChrome);
> ```

> 分析拆解 url 各个部分
>
> **Soln :**
>
> ```
> console.log(location.href); // url
> console.log(location.protocol); // http / https
> console.log(location.host); // www.google.ca
> console.log(location.pathname); // /serach
> console.log(location.search); // ?a=100&b=200
> console.log(location.hash); // #Anchor
> ```

