---
title: "Markdown - 进阶知识"
subtitle: ""
date: 2021-12-07T11:35:43+08:00
lastmod: 2021-12-07T11:35:43+08:00
author: "守正"
slug: "markdown_high_level"
tags: ["Markdown"]
categories: ["Study"]
featuredImage: 'https://cdn.chiga.ga/Posts/Study/06_markdown_high_level/Cover.jpg'
---

Mermaid的功能介绍及使用方法；

<!--more-->

## 概述

### 什么是Mermaid？

`Mermaid`是一种基于`Javascript`的绘图工具，使用类似于`Markdown`的语法，使用户可以方便快捷地通过代码创建图表。

`Mermaid`作为一个使用`JS`渲染的库，广泛集成于许多`Markdown`编辑器中（如`Typora`），生成的不是一个“图片”，而是一段`HTML`代码，因此安全许多。

项目地址：<https://github.com/mermaid-js/mermaid>

### Mermaid能绘制哪些图？

1. **饼状图：** 使用`pie`关键字;
2. **流程图：** 使用`graph`关键字;
3. **序列图：** 使用`sequenceDiagram`关键字;
4. **甘特图：** 使用`gantt`关键字;
5. **类图：** 使用`classDiagram`关键字;
6. **状态图：** 使用`stateDiagram`关键字;
7. **用户旅程图：** 使用`journey`关键字;

## 流程图

### 图表方向

Mermaid 支持多种图表的方向，语法如下：

```markdown
graph 方向
    图表中的其他语句...
```

定义方向|含义|
:-:|:-:|
`graph`或`graph TB`或`graph TD`|从上到下|
`graph BT`|从下到上|
`graph RL`|从右到左|
`graph LR`|从左到右|

### 节点定义

即流程图中每个文本块，包括开始、结束、处理、判断等，`Mermaid` 中每个节点都有一个 `id`，以及节点的文字。

```markdown
graph TB;
    id1[方形]
    id2(圆边矩形)
    id3([体育场形])
    id4[[子程序形]]
    id5[(圆柱形)]
    id6((圆形))
```

{{< mermaid >}}
graph TB;
    id1[方形]
    id2(圆边矩形)
    id3([体育场形])
    id4[[子程序形]]
    id5[(圆柱形)]
    id6((圆形))
{{< /mermaid >}}

```markdown
graph TB;
	id1{菱形}
	id2{{六角形}}
	id3[/平行四边形/]
	id4[\反向平行四边形\]
	id5[/梯形\]
	id6[\反向梯形/]
```

{{< mermaid >}}
graph TB;
	id1{菱形}
	id2{{六角形}}
	id3[/平行四边形/]
	id4[\反向平行四边形\]
	id5[/梯形\]
	id6[\反向梯形/]
{{< /mermaid >}}

{{< admonition type=warning title=注意 open=true >}}
如果节点的文字中包含标点符号，需要时用双引号包裹起来。另外如果希望在文字中使用换行，请使用`<br>`表述换行；
{{< /admonition >}}

### 节点间的连线

#### 连线说明

|表述|说明|
|:-:|:-:|
|`>`|添加尾部箭头|
|`-`|不添加尾部箭头|
|`--`|单线|
|`--text--`|单线上加文字|
|`==`|粗线|
|`==text==`|粗线加文字|
|`-.-`|虚线|
|`-.text.-`|虚线加文字|

#### 连线样式

- **实线箭头：** 分为无文本箭头和有文本箭头，有文本箭头有`2`种书写格式

```markdown
graph LR;
a-->b--文本1-->c-->|文本2|d
```

{{< mermaid >}}
graph LR;
a-->b--文本1-->c-->|文本2|d
{{< /mermaid >}}

- **粗实线箭头：** 分为无文本箭头和有文本箭头

```markdown
graph LR;
a==>b==文本==>c
```

{{< mermaid >}}
graph LR;
a==>b==文本==>c
{{< /mermaid >}}

- **虚线箭头：** 分为无文本箭头和有文本箭头

```markdown
graph LR;
a-.->b-.文本.->c
```

{{< mermaid >}}
graph LR;
a-.->b-.文本.->c
{{< /mermaid >}}

- **无箭头线：** 即以上三种连线去掉箭头后的形式

```markdown
graph LR;
a---b
b--文本1!---c
c---|文本2|d
d===e
e==文本3===f
f-.-g
g-.文本.-h
```

{{< mermaid >}}
graph LR;
a---b
b--文本1!---c
c---|文本2|d
d===e
e==文本3===f
f-.-g
g-.文本.-h
{{< /mermaid >}}

- **其他连线：** 需要将`graph`关键字改为`flowchart`，除了新增加的连线形式外，上面三种线的渲染效果也会不同

```markdown
flowchart LR;
    A o--o B
    B <--> C
    C x--x D
    
    旧连线 --文本--> 也会不同
```

{{< mermaid >}}
flowchart LR;
    A o--o B
    B <--> C
    C x--x D
    
    旧连线 --文本--> 也会不同
{{< /mermaid >}}

- **延长连线：** 增加相应字符即可，如下图中的`B`到`E`，连线中增加了一个`-`。字符可多次添加。

```markdown
graph LR;
    A[Start] --> B{"Is it?"}
    B --Yes--> C[OK]
    C --> D[Rethink]
    D --> B
    B --No--> E[End]
```

{{< mermaid >}}
graph LR;
    A[Start] --> B{"Is it?"}
    B --Yes--> C[OK]
    C --> D[Rethink]
    D --> B
    B --No--> E[End]
{{< /mermaid >}}

#### 连线形式

- 直链

```markdown
graph LR;
   A -- text --> B -- text2 --> C
```

{{< mermaid >}}
graph LR;
   A -- text --> B -- text2 --> C
{{< /mermaid >}}

- **多重链：** 可以使用`&`字符，或单个描述

```markdown
graph  TB;
   a --> b & c--> d
   A & B--> C & D
    X --> M
    X --> N
    Y --> M
    Y --> N
```

{{< mermaid >}}
graph  TB;
   a --> b & c--> d
   A & B--> C & D
    X --> M
    X --> N
    Y --> M
    Y --> N
{{< /mermaid >}}

### 子图表

需要将`graph`关键字改为`flowchart`，在代码段的开始加入`subgraph`，尾部加入`end`

```markdown
flowchart TB;
    c1-->a2
    subgraph one
    a1-->a2
    end
    subgraph two
    b1-->b2
    end
    subgraph three
    c1-->c2
    end
    one --> two
    three --> two
    two --> c2
end
```

{{< mermaid >}}
flowchart TB;
    c1-->a2
    subgraph one
    a1-->a2
    end
    subgraph two
    b1-->b2
    end
    subgraph three
    c1-->c2
    end
    one --> two
    three --> two
    two --> c2
{{< /mermaid >}}


### 注释

在行首加入`%%`即可。

```markdown
graph LR;
%%这是一条注释，在渲染图中不可见
    A[Hard edge] -->|Link text| B(Round edge)
    B --> C{Decision}
    C -->|One| D[Result one]
    C -->|Two| E[Result two]
```

{{< mermaid >}}
graph LR;
%%这是一条注释，在渲染图中不可见
    A[Hard edge] -->|Link text| B(Round edge)
    B --> C{Decision}
    C -->|One| D[Result one]
    C -->|Two| E[Result two]
{{< /mermaid >}}

## 例子

```
graph TB;
    id1(圆角矩形)--普通线-->id2[矩形]
    subgraph 子图表
        id2==粗线==>id3{菱形}
        id3-.虚线.->id4>右向旗帜]
        id3--无箭头---id5((圆形))
    end
```

{{< mermaid >}}
graph TB;
    id1(圆角矩形)--普通线-->id2[矩形]
    subgraph 子图表
        id2==粗线==>id3{菱形}
        id3-.虚线.->id4>右向旗帜]
        id3--无箭头---id5((圆形))
    end
{{< /mermaid >}}

## 饼状图

### 语法

|表述|说明|
|:-:|:-:|
|`pie`|开始图表|
|`title` 关键字|为饼图赋予标题|
|`"分区名"`|定义分区名|
|分区名后使用`:`|作为分隔符|
|数值|最多支持2位小数(数据会以百分比的形式展示)|

### 例子

```markdown
pie
    title 为什么总是宅在家里？
    "喜欢宅" : 15
    "天气太热或太冷" : 20
    "穷" : 500
```

{{< mermaid >}}
pie
    title 为什么总是宅在家里？
    "喜欢宅" : 15
    "天气太热或太冷" : 20
    "穷" : 500
{{< /mermaid >}}

## 甘特图

### 语法

- 使用关键词`gantt`声明甘特图

- 使用关键词`title`声明标题

- 使用关键词`section`声明板块

- 板块后是任务的名称，任务类型，开始时间，持续时间等

- 时间参数

|参数|示例|含义|
|:-:|:-:|:-:|
|YYYY|2014|4 digit year|
|YY|14|2 digit year|
Q|1..4|Quarter of year. Sets month to first month in quarter.|
M MM|1..12|Month number|
|MMM MMMM|January..Dec|Month name in locale set by moment.locale()|
|D DD|1..31|Day of month|
|Do|1st..31st|Day of month with ordinal|
|DDD DDDD|1..365|Day of year|
|X|1410715640.579|Unix timestamp|
|x|1410715640579|Unix ms timestamp|
|H HH|0..23|24 hour time|
|h hh|1..12|12 hour time used with a A.|
|a A|am pm|Post or ante meridiem|
|m mm|0..59|Minutes|
|s ss|0..59|Seconds|
|S|0..9|Tenths of a second|
|SS|0..99|Hundreds of a second|
|SSS|0..999|Thousandths of a second|
|Z ZZ|+12:00|Offset from UTC as +-HH:mm, +-HHmm, or Z|

### 例子

```markdown
gantt
        dateFormat  YYYY-MM-DD
        title Adding GANTT diagram functionality to mermaid

        section A section
        Completed task            :done,    des1, 2014-01-06,2014-01-08
        Active task               :active,  des2, 2014-01-09, 3d
        Future task               :         des3, after des2, 5d
        Future task2               :         des4, after des3, 5d

        section Critical tasks
        Completed task in the critical line :crit, done, 2014-01-06,24h
        Implement parser and jison          :crit, done, after des1, 2d
        Create tests for parser             :crit, active, 3d
        Future task in critical line        :crit, 5d
        Create tests for renderer           :2d
        Add to mermaid                      :1d

        section Documentation
        Describe gantt syntax               :active, a1, after des1, 3d
        Add gantt diagram to demo page      :after a1  , 20h
        Add another diagram to demo page    :doc1, after a1  , 48h

        section Last section
        Describe gantt syntax               :after doc1, 3d
        Add gantt diagram to demo page      : 20h
        Add another diagram to demo page    : 48h
```

{{< mermaid >}}
gantt
        dateFormat  YYYY-MM-DD
        title Adding GANTT diagram functionality to mermaid

        section A section
        Completed task            :done,    des1, 2014-01-06,2014-01-08
        Active task               :active,  des2, 2014-01-09, 3d
        Future task               :         des3, after des2, 5d
        Future task2               :         des4, after des3, 5d

        section Critical tasks
        Completed task in the critical line :crit, done, 2014-01-06,24h
        Implement parser and jison          :crit, done, after des1, 2d
        Create tests for parser             :crit, active, 3d
        Future task in critical line        :crit, 5d
        Create tests for renderer           :2d
        Add to mermaid                      :1d

        section Documentation
        Describe gantt syntax               :active, a1, after des1, 3d
        Add gantt diagram to demo page      :after a1  , 20h
        Add another diagram to demo page    :doc1, after a1  , 48h

        section Last section
        Describe gantt syntax               :after doc1, 3d
        Add gantt diagram to demo page      : 20h
        Add another diagram to demo page    : 48h
{{< /mermaid >}}

## 序列图

### 语法

使用以下语法开始序列图

```
sequenceDiagram
    [参与者1][消息线][参与者2]:消息体
    ...
```

例如

```
sequenceDiagram
    张三->>李四: 吃了吗？
    李四->>张三: 吃了
```

{{< mermaid >}}
sequenceDiagram
    张三->>李四: 吃了吗？
    李四->>张三: 吃了
{{< /mermaid >}}

### 参与者

上例中的张三、李四都是参与者，上例中的语法是最简单的，也可以明显表明参与者有哪些

```
sequenceDiagram
    participant 参与者 1
    participant 参与者 2
    ...
    participant 简称 as 参与者 3 #该语法可以在接下来的描述中使用简称来代替参与者 3
```

### 消息线

|类型|描述|
|:-:|:-:|
|`->`|无箭头的实线|
|`-->`|无箭头的虚线|
|`->>`|有箭头的实线|
|`-->>`|有箭头的虚线|
|`-x`|末端为叉的实线（表示异步）|
|`--x`|末端为叉的虚线（表示异步）|

### 处理中

在消息线末尾增加 `+` ，则消息接收者进入当前消息的“处理中”状态；

在消息线末尾增加 `-` ，则消息接收者离开当前消息的“处理中”状态。

或者使用以下语法直接说明某个参与者进入“处理中”状态

```
activate 参与者
```

### 标注

语法如下

```
Note 位置表述 参与者: 标注文字
```

其中位置表述可以为

|表述|含义|
|:-:|:-:|
|`right of`|右侧|
|`left of`|左侧|
|`over`|在当中，可以横跨多个参与者|

### 循环

语法如下

```
loop 循环的条件
    循环体描述语句
end
```

### 判断

```
alt 条件 1 描述
    分支 1 描述语句
else 条件 2 描述 # else 分支可选
    分支 2 描述语句
else ...
    ...
end
```

如果遇到可选的情况，即没有 else 分支的情况，使用如下语法：

```
opt 条件描述
    分支描述语句
end
```

### 例子

```markdown
sequenceDiagram
    participant z as 张三
    participant l as 李四
    loop 日复一日
        z->>l: 吃了吗您呐？
        l-->>z: 吃了，您呢？
        activate z
        Note left of z: 想了一下
        alt 还没吃
            z-xl: 还没呢，正准备回去吃
        else 已经吃了
            z-xl: 我也吃过了，哈哈
        end
        opt 大过年的
            l-->z: 祝您新年好啊
        end
    end
```

{{< mermaid >}}
sequenceDiagram
    participant z as 张三
    participant l as 李四
    loop 日复一日
        z->>l: 吃了吗您呐？
        l-->>z: 吃了，您呢？
        activate z
        Note left of z: 想了一下
        alt 还没吃
            z-xl: 还没呢，正准备回去吃
        else 已经吃了
            z-xl: 我也吃过了，哈哈
        end
        opt 大过年的
            l-->z: 祝您新年好啊
        end
    end
{{< /mermaid >}}


## 参考链接

- [Mermaid 实用教程](https://blog.csdn.net/fenghuizhidao/article/details/79440583)
- [Mermaid从入门到入土——Markdown进阶语法](https://zhuanlan.zhihu.com/p/355997933)
- [Mermaid，就像用 Markdown 码字一样，高效制作简易流图](https://sspai.com/post/63055)
- [mermaid 语法](https://www.cnblogs.com/dao0/p/4489837.html)