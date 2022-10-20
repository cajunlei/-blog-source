---
title: "CSS - 学习笔记"
subtitle: ""
date: 2021-12-05T09:24:36+08:00
lastmod: 2021-12-05T09:24:36+08:00
author: "守正"
slug: "css_study_notes"
tags: ["HTML", "CSS"]
categories: ["Study"]
featuredImage: ''
---



<!--more-->

## 设置表格单元格宽度

网页中插入表格时，设置了表格的宽度，则会根据表格宽度拉伸；但是有时候内容过长时，就会拉伸的很难看，所以就需要固定表格宽度。

```html
<table>
    <thead>
        <tr>
        <th class="number">序号</th>
        <th class="color">颜色</th>
        <th class="text">HEX格式</th>
        <th class="text">RGB格式</th>
        </tr>
    </thead>
    <tbody>
        <tr>
        <td class="number">1</td>
        <td class="color" bgcolor="lightpink">    </td>
        <td class="text">#FFB6C1</td>
        <td class="text">255,182,193</td>
        </tr>
    </tbody>
</table>
```

```css
table {
    table-layout:fixed;
    word-wrap: break-word;
}
.number {
    width: 10%;
}
.color {
    width: 10%;
}
.text {
    width: 40%;
}
// 表格固定布局
table {
    table-layout: fixed;
    word-break: break-all;
    word-wrap: break-word;
}
```

- `table-layout:fixed` 表示：

列宽由表格宽度和列宽度设定。在固定表格布局中，水平布局仅取决于表格宽度、列宽度、表格边框宽度、单元格间距，而与单元格的内容无关。

- `word-break:break-all` 表示：

`word-break` 属性规定自动换行的处理方法。`break-all`允许在单词内换行。

- `word-wrap: break-word` 表示：

`word-wrap` 属性允许长单词或 `URL` 地址换行到下一行。b`reak-word`就表示在长单词或 `URL` 地址内部进行换行。

{{< admonition type=note title=提示 open=true >}}
`table-layout`,` word-break`,` word-wrap`这三个属性都是关于固定宽度显示控制的;

对一般的浏览器来说，只需要其中一个就可以完成控制了.
{{< /admonition >}}

## 使图片重叠放置

### 方法

**父级元素** 样式设置：
```css
position: relative;
```

**子元素** 样式设置：

```css
position: absolute;
```

这样就可以达到子元素相对父级元素定位了。

### 示例

```html
<div class="images">
    <img class="img1" src="/images1.jpg">
    <img class="img2" src="/images2.jpg">
    <img class="img3" src="/images3.jpg">
</div>
```

```css
.images {
    position: relative;
}
.images .img2 {
    display: block;
    position: absolute;
    border-radius: 10px;
    width: 50%;
    top: 10%;
    left: 50%;
}
.images .img3 {
    display: block;
    position: absolute;
    border-radius: 50%;
    width: 10%;
    top: 50%;
    left: 50%;
}
```



## 参考链接

- [css 设置表格单元格宽度](https://blog.csdn.net/qq_39292868/article/details/82464125)
- [html css样式子元素相对父级元素定位](https://www.cnblogs.com/feicheninfo/articles/11004410.html)
