## 1.1 观察代码
>[!info]
> 超文本标记语言 (HyperText Markup language) 简称 HTML

我们已经知道 HTML 语言是浏览器用来显示页面的关键，所以在学习的最初，我们先做一个“连线题”，下面是 Head First Lounge（休闲餐吧）宣传页面的 HTML 代码。

```html
<html>
  <head>
    <title>Head First Lounge</title>
  </head>
  
  <body>
    <h1>Welcome to the Head First Lounge</h1>
    <img src="drinks.gif">
    <p>
      Join us any evening for 
      refreshing elixirs,
      conversation and maybe a game or two of
      <em>Dance Dance Revolution</em>.
      Wireless access is always provided;
      BYOWS (Bring your own web server).
    </p>
    <h2>Directions</h2>
    <p>
      You'll find us right in the center of downtown Webville.
      If you need help finding us, check out 
      our detailed directions.Come join us!
    </p>
  </body>
</html>
```

而下面这张网页就是上述代码被浏览器“解释”后呈现在用户面前的样子：

![[031HeadFisrtLounge.png]]

>[!question]
你能找出来各行代码分别与页面那部分相关吗？

___
## 1.2 执行代码

>[!todo]
> 请利用 VS Code 编辑页面，复制上文中的代码到自己的电脑上，并在浏览器执行，观察结果是否与本例一致，不要忘记把下面这张图一并复制过去。（\appendixes\drinks.gif）

![[drinks.gif]]

不难发现，代码中的 `<html>` `<head>` `<p>` `<img>` 等尖括号括起来的单词或字符就是“超文本标记语言”中的所谓==标记==。

>[!tip]
> 标记会告诉浏览器文本的含义。

比如 `<p>` 代表段落; `<img>` 代表图片等等。

>[!tip]
> 同时标记还会告诉浏览器页面的结构
> 
```html
  <html>
    <head>
 
    </head>
    <body>

    </body>
  </html>
  ```

>[!question]
>请猜想一下，这三个表示“页面结构”的标记都有什么含义？