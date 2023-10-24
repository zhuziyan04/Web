由于曾经有这么多版本的 HTML，所以我们在写网页之前需要声明当前网页使用的 HTML 标准版本，也就是 Doctype，这样才能保证浏览器能以正确的形式“翻译”我们的 HTML 代码。

## 2.1 Doctype 考古

我们先来看看 HTML 4.01 和 XHTML 1.1 的 doctype

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
```

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
```

这个声明要写在 .html 文件的最开头，所有的 HTML 代码之前，请注意这不是一个 HTML 标签， < 后紧跟着的 ! 就是说明它与众不同。是不是看的有点眼晕。

---
## 2.2 HTML5 的 Doctype

新的 HTML5 的 Doctype 就是下面这串代码，是不是意外的简单明了。

```html
<!DOCTYPE html>
```

之所以可以简化到如此程度，是因为从 HTML5 开始，HTML 标准是一种“活”的标准，不会再有固定的版本号更新，所以我们要做的唯一一件事就是告诉浏览器，我们正在使用 HTML 编写文件。仅此而已。

___
## 2.3 不会再有 6，7，8

甚至连 HTML5 都是迎合市场的说法，其实从标准发布时开始，就只有 HTML 标准了，不再讨论版本号。这其实是一个“兼容性”保证，即所有后来发布的 HTML 标准，都 100% 支持以前的 HTML 标准。所以无论 HTML 处于什么版本，都无需特别说明。

>[!warning]
> 学习了新标准和新写法，请立刻为休闲吧的所有页面都添加 HTML5 的 doctype 声明。