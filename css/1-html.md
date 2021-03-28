# 1. HTML

> 如何理解HTML语义化？
>
> **Soln**:
>
> 对比:
>
> ```markup
> <div></div>
> <div>
>     <div></div>
>     <div>
>         <div></div>
>         <div></div>
>     </div>
> </div>
> ```
>
> ```markup
> <h1></h1>
> <div>
>     <p></p>
>     <ul>
>         <li></li>
>         <li></li>
>     <ul>
> </div>
> ```
>
> * 让人更容易读懂 （增加代码可读性）
> * 让搜索引擎更容易读懂（SEO\)

> 默认情况下 那些标签是块级元素 哪些是内联元素?
>
> **Soln**:
>
> * 块状元素 （独占1行）
>   * display：block / table  
>   * div h1 h2 table ul ol p
> * 内联元素 \(不换行 直到1行满\)
>   * display: inline/inline-block
>   * span img input button











