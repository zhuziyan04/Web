我们已经为 index.html 增加了样式，但 elixirs.html 和 directions.html 呢？它们是否也要与主页外观保持一致？

>[!question]
>  利用现有的知识，如何让 elixirs.html 和 directions 也应用相同的样式？

## 1.1  在 `<style>` 标签中设置

我们在上一章的 [3 用选择器做复杂样式](obsidian://open?vault=WebDesignTutorial&file=11%20%E5%85%AB%E3%80%81CSS%20%E5%85%A5%E9%97%A8%2F3%20%E7%94%A8%E9%80%89%E6%8B%A9%E5%99%A8%E5%81%9A%E5%A4%8D%E6%9D%82%E8%AE%BE%E7%BD%AE(10min))章节中的 CSS 显然已经起效，如果我们把其中的代码复制三份，确实可以完成任务，但动手之前请仔细思考，我们搞开发的，会去做这些简单的重复劳动吗？

>[!tip]
> 如果你的回答是不，请猜想一下解决方案。

---
## 1.2 试试新方法

其实不难想到，既然所有的外观要一致，所有页面的 CSS 配置都相同，那应该有一种办法可以把相同的设置”提取“出来，再分别应用到不同的网页上去，减少代码的重复。具体方式应该分三步走：

1. 提取 index.html 中的所有规则，把它放到一个外部文件中。
2. 建立 index.html 和外部文件的链接，应用外部文件中的规则。
3. 在另外两张页面里也做相同的链接。

完成后就可以检查是否成功了。

###  1.2.1 创建 lounge.css 文件

* 在网站根目录创建一个名为 lounge.css 的文件，这个文件里将会包含所有的 Head first 休闲吧的样式规则。请利用 vscode 新建这个文件。
* 完成文件创建后，把原先存在于 index.html 文件中的规则复制过来。
	
	>[!warning]
	> .css 文件，只要 css 规则，切勿把 HTML 代码也复制过来！
	
	因此我们要复制的代码其实只有一下部分，可没有 `<style>`标签：
	
	```css
	h1, h2 {
	  font-family: Arial;
	  color: grey;
	}
	
	
	h1 {
	  border-bottom：1px solid black;
	}
	
	p {
	  color: maroon;
	}
	```

### 1.2.2 把 index.html 链接到外部样式表

index.html 和 lounge.css 显然是完全不相干的两个文件，系统不会自作主张把他们合并到一起完成样式规则的添加。现在，我们需要告诉浏览器，index.html 会利用一张外部样式表为页面增加样式规则。而这个操作，需要用到 `<link>` 这个新标签：

```html
<!DOCTYPE html>
<html>
  <head>
	  <meta charset="utf-8">
	  <title>Head First Lounge</title>
	  <link type ="text/css" rel="stylesheet" href="lounge.css">
  </head>
  <body>
	...
  </body>
</html>
```


### `<link type ="text/css" rel="stylesheet" href="lounge.css">`

* link:  用于引入外部信息的标记。
* type： 顾名思义，type 属性是用来描述引入内容的，这里的属性值的 text/css，显然代表了 文字/css，html5 中 type 属性不是不要的，这里保留是为了各位能看明白老网页的 css 引入。
* rel：该属性制定了 HTML 文件与所链接文件间的关系，我们链接的是一张样式表，所以值是 stylesheet。
* href：这是我们很熟悉的属性了，需要提醒的是，这里可以是相对路径，也可以是完整的 URL。
* 最后 link 是 void 元素，所以不需要结束标记。