---
title: 你好，世界
date: 2026-11-05 22:53:36 +0800
---

这是第一篇文章。以后每写一篇新的，只要在 `_posts/` 目录下新建一个文件即可，文件名格式固定为：

```
YYYY-MM-DD-英文短标题.md
```

例如 `2026-11-12-my-first-week.md`。文件名里的日期就是文章的发布日，`---` 之间的部分是元信息（front matter），下面的内容是正文，用 Markdown 写。

## 支持的写法

**加粗**、*斜体*、`行内代码`、[链接](https://github.com/extrisha)

```python
def hello(name):
    print(f"hello, {name}")
```

- 列表项一
- 列表项二

> 引用块。

## 关于图片

把图片放进 `assets/images/`，然后在文章里这样引用：

```
![图片说明](/assets/images/example.png)
```

注意开头的斜杠不能少，这样在任何页面路径下都能正确加载。
