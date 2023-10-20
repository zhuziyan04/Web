 ## 3.1 认识 W3C 验证工具

[The W3C Markup Validation Service](https://validator.w3.org/) 这个网站是官方提供的验证工具：
1. Validate by URI 可以提交已经在互联网上的页面进行验证；
2. Validate by File Upload 是提交网页文件进行验证；
3. Validate by Direct Input 则是直接复制粘贴代码进行验证。

请各位选择一个合适的方法验证你休闲吧 index.html 的代码，毕竟这张网页写了这么久，你自己也很想知道代码是不是完全符合标准吧。

不出意料的话，你们将会看到刺眼的:<span style="background-color: #f00;border-radius:6px;border:1px solid #ccc';color:blue">Error </span>,  显示 Error (错误)，warning (警告)，请检查下你的页面，看看到底有多少问题。

---
## 3.2 修正错误

>[!warning]- 为提高各位的英语水平，请各位想办法看懂检查后的说明文档，并尽量改正错误再点开这个栏目。
> 如果提到字符串编码的问题，我们可以在 `<head>` 部分的 == 第一行 == 加入：
> ```html
> <meta charset="utf-8">
> ```

当所有的 Error 都改正，我们就可以看到代表正确的绿条了。
<p style="background-color:#cfc; color:#000; border: 1px solid #ccc;">Document checking completed. No errors or warnings to show.</p>

>[!bug] DeBug
> 接下来，请把 directions.html 和 elixirs.html 中的代码也进行验证，并修正错误。

---
## 3.3 常见错误指南

* 一定要以 doctype 开头。
* 不能没有 `<html>` 标签。
* 只有 `<head>` 和 `<body>` 允许直接放在 `<html>` 中间，没有例外。
* 在 `<head>` 中要指定正确的字符编码。
* 一定要在 `<head>` 中包含 `<title>`
* 不能进行无意义的嵌套，比如在 `<a>` 中嵌套 `<a>`。
* void 元素不允许嵌套其他元素。
* 标签的必选属性不可忽略，比如 `<img>` 的 src 和 alt 属性。
