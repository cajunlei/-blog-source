---
weight: 1
title: "Auto CAD - 使用技巧和疑难杂症解决办法"
subtitle: ""
date: 2021-10-21T23:53:40+08:00
lastmod: 2021-11-29T09:25:40+08:00
author: "守正"
authorLink: ""
description: ""
slug: "cad_skills_problem"
tags: ["Auto CAD"]
categories: ["Work"]
featuredImage: "https://cdn.chiga.ga/Posts/Work/AutoCAD/01_Skill/Cover.webp"
---

本人在使用`Auto CAD`的过程中的一些学习笔记分享。持续更新中 ······

<!--more-->

## 使用技巧

### 高版本设置“经典模式”

从`2015`开始，`CAD`默认就没有经典模式界面了，但是朋友都习惯了使用原来的经典模式空间，接下来教你**不用插件**`CAD`高版本如何快速调出“经典模式”空间

**第一步** 打开`CAD`，找到左上角的向下三角形，点击显示菜单栏；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/01_Skill/2021-11-16_09-09-47.png` alt=我这里已经显示了菜单栏 width=60% >}}

**第二步** 打开工具菜单 --> 选项板 --> 点击功能区，将功能区关闭；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Work/AutoCAD/01_Skill/2021-11-16_09-11-26.png alt=img width=60% >

**第三步** 打开工具菜单 --> 工具栏 --> `AutoCAD`，根据个人需要把标准，样式，图层，特性，绘图，修改，绘图次序勾选上；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Work/AutoCAD/01_Skill/2021-11-16_09-12-12.png alt=img width=60% >

**第四步** 然后点击右下角的齿轮，将当前工作空间另存为`AutoCAD`经典（或者自己喜欢的名字），保存即可；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Work/AutoCAD/01_Skill/2021-11-16_09-14-21.png alt=img width=40% >

### 高版本关闭开始页面

**第一步** 打开`CAD`后，默认打开的是开始页；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/01_Skill/2021-10-25_16-27-54.png` alt=默认的开始页面 >}}

**第二步** 新建一个空白文件；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/01_Skill/2021-10-25_16-28-58.webp` alt=新建CAD文件 >}}

**第三步** 在命令行中输入`startmode`命令后回车；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Work/AutoCAD/01_Skill/2021-10-25_16-29-29.png alt=img width=60% >

**第四步** 将默认的`1`改为`0`，然后回车；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Work/AutoCAD/01_Skill/2021-10-25_16-29-44.png alt=img width=60% >

此时，开始页就已经关闭了。

<img class=l-img src={{< param cdnPrefix >}}/Posts/Work/AutoCAD/01_Skill/2021-10-25_16-30-22.png alt=img width=95% >

<img class=l-img src={{< param cdnPrefix >}}/Posts/Work/AutoCAD/01_Skill/2021-10-25_16-30-47.webp alt=img width=95% >

{{< admonition type=tip title=" 提示" open=true >}}

若要恢复，将 **第四步** 的`0`改为`1`，然后回车。

{{< /admonition >}}

---

### 快速修改属性文字

在`CAD`中要编辑普通文字，直接双击就可以修改；

但属性块中的属性文字，我们双击以后会先弹出一个对话框，然后才能修改；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/01_Skill/2021-10-22_21-03-54.png` alt=双击属性块的编辑界面 width=75% >}}

那么属性文字如何实现像普通文字一样双击修改呢？

{{< admonition type=tip title=" 操作方法：" open=true >}}

按住 Ctrl 键，双击属性文字。

{{< imgcapcdn src=`/Posts/Work/AutoCAD/01_Skill/2021-10-22_21-04-14.png` alt=无弹窗，直接编辑 width=60% >}}

{{< /admonition >}}

### 属性块中文字高度无法更改

在修改文字高度的时候，发现文字高度是显示灰色的；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/01_Skill/2021-10-22_19-18-30.png` alt=查看使用的文字样式 width=75% >}}

双击属性块，在增强属性编辑器 --> 文字选项 --> 文字样式；

记住所使用的文字样式；

快捷键`ST`打开文字样式 --> 找到所使用的样式，将大小一栏的高度改成`0`就行了；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/01_Skill/2021-10-22_19-19-08.png` alt=修改文字高度 width=75% >}}

再次双击属性块，打开增强属性编辑器 --> 文字选项 --> 高度；

这个时候就正常显示，可以修改了；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/01_Skill/2021-10-22_19-19-38.png` alt=操作成功 width=75% >}}

### 批量修改属性快的特性

`CAD`中批量修改图块的特性，如属性的颜色等;

```Text
BATTMAN
```

比如我现在要将材料名称的颜色都改为红色 ；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Work/AutoCAD/01_Skill/2021-10-22_21-48-17.png alt=img width=85% >

输入`battman`命令，回车；

在块属性管理器左上角 --> 选择快 --> 设置；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/01_Skill/2021-10-22_21-13-15.png` alt=块属性管理器 width=75% >}}

在块属性设置对话框先全部清除,然后勾选 提示和颜色 --> 确定;

{{< imgcapcdn src=`/Posts/Work/AutoCAD/01_Skill/2021-10-22_21-27-23.png` alt=块属性设置对话框 width=75% >}}

选择需要编辑的行 --> 编辑 --> 在编辑属性对话框选择特性 --> 颜色 --> 红色 --> 确定 --> 确定；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/01_Skill/2021-10-22_21-28-33.png` alt=编辑属性对话框 width=75% >}}

图块属性就都改过来了；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/01_Skill/2021-10-22_21-45-47.png` alt=修改成功 width=85% >}}

`BATTMAN`命令不仅可以修改图块属性的颜色，还可以编辑图块的其他属性定义、从块中删除属性以及更改插入块时系统提示用户输入属性值的顺序。

{{< admonition type=example title=" 对话框中各个控件的作用：" open=false >}}

**1、选择块：** 单击“选择块”按钮后，对话框将临时关闭，可以使用鼠标从图中拾取要编辑的块。

如果修改了块的属性，并且未保存所做的更改就选择一个新块，系统将提示在选择其他块之前先保存更改。

**2、块列表：** 列出具有属性的当前图形中的所有块定义。选择要修改属性的块。

属性列表： 显示所选块中每个属性的特性。

**3、同步：** 更新具有当前定义的属性特性的选定块的全部实例。此操作不会影响每个块中赋给属性的值。

**4、上移：** 在提示序列的早期阶段移动选定的属性标签。选定固定属性时，“上移”按钮不可用。

**5、下移：** 在提示序列的后期阶段移动选定的属性标签。选定常量属性时，“下移”按钮不可使用。

**6、编辑：** 打开“编辑属性”对话框，从中可以修改属性特性。

**7、删除：** 从块定义中删除选定的属性。如果在选择“删除”之前已选择了“设置”对话框中的“将修改应用到现有参照”，将删除当前图形中全部块实例的属性。对于仅具有一个属性的块，“删除”按钮不可使用。

**8、在图形中找到的块：** X 报告当前图形中选定块的实例总数。

**9、在当前空间中找到的块：** X 报告当前模型空间或布局中选定块的实例数。

**10、设置：** 打开“块属性设置”对话框，从中可以自定义“块属性管理器”中属性信息的列出方式。

**11、应用：** 应用所做的更改，但不关闭对话框。

{{< /admonition >}}

### 文字加背景

为了使文字更醒目，不被图形遮挡，可以使用背景遮罩；

**第一步** 选中文字，按`Ctrl + 1`打开特性面板；

**第二步** 点击文字 --> 背景遮罩；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Work/AutoCAD/01_Skill/2021-11-04_12-50-19.png alt=img width=50% >

**第三步** 勾选「使用背景遮罩」、「使用图形背景颜色」，确定；

<img class=l-img src={{< param cdnPrefix >}}/Posts/Work/AutoCAD/01_Skill/2021-11-04_12-50-36.png alt=img width=75% >

{{< admonition type=warning title=" 注意" open=true >}}

- 只有**多行文字**可以添加「背景遮罩」；

- **单**行文字转换为**多**行文字命令：`TXT2MTXT`；

{{< /admonition >}}

### 输入特殊符号

符号|输入|
:--:|:--:|
正负号±|%%p|
直径符号|%%c|
温度符号|%%d|
带下划线字体|%%u|
带上划线字体|%%o|
一级钢符号|%%130|
二级钢符号|%%131|
三级钢符号|%%132|
四级钢符号|%%133|
特殊钢筋|%%134|
L型钢|%%135|
H型钢|%%136|
槽型钢|%%137|
工字钢|%%138|
上标文字开|%%140|
上标文字关|%%141|
下标文字开|%%142|
下标文字关|%%143|
小于等于≤|%%146|
大于等于≥|%%147|
小于号<|%%60|
等于号=|%%61|
大于号>|%%62|
约等于|%%173|
小于等于≤|%%174|
大于等于≥|%%175|
乘号×|%%178|
除号÷|%%179|
不等于|%%180|
不小于|%%186|
不大于|%%187|
Ⅰ|%%150|
Ⅱ|%%151|
Ⅲ|%%152|
Ⅳ|%%153|
Ⅴ|%%154|
Ⅵ|%%155|
Ⅶ|%%156|
Ⅷ|%%157|
Ⅸ|%%158|
Ⅹ|%%159|
圆中有一个字符的特殊文字的开始，如①|%%200|
圆中有一个字符的特殊文字的结束|%%201|
圆中有二个字符的特殊文字的开始|%%202|
圆中有二个字符的特殊文字的结束|%%203|
圆中有三个字符的特殊文字的开始|%%204|
圆中有三个字符的特殊文字的结束|%%205|
扁钢|%%191|
工字钢|%%192|
角钢|%%193|
槽钢|%%194|
方钢|%%195|
卷边角钢|%%196|
卷边槽钢|%%197|
Z型钢|%%198|
平方米|%%164或m%%1412%%142|
一级钢|%%129|
二级钢|%%130|
三级钢|%%160|
罗马1|%%131|
罗马2|%%132|
罗马4|%%134|
罗马5|%%135|
罗马6|%%136|
罗马7|%%137|
罗马8|%%138|
罗马9|%%139|
罗马10|%%140|
上标上|%%141|
上标归位|%%142|
下标下|%%143|
下标归位|%%144|
上下标上|%%145|
上下标下|%%146|
上下标归位|%%144|
千分号|%%151|
∑|%%156|
人民币|%%165|
打钩|%%168|
打叉|%%169|
一位轴|%%147|
一位轴圈|%%148|
二位轴|%%149|
二位轴圈|%%150|
方形空|%%201|
方形填|%%202|
三角号|%%203|
希腊字母|%%209~238所有小写及几个大写|
左箭号|%%241|
右箭号|%%242|
上箭号|%%243|
下箭号|%%244|
黑左箭号|%%245|
黑右箭号|%%246|
黑上箭号|%%247|
黑下箭号|%%248|
标高写法|%%251 %%252|

{{< admonition type=warning title=注意 open=true >}}
如以上符号未正常显示，请搜索下载以下字体。
1. `TssdEng.ttf`
2. `SJQY.ttf`
3. `hztxt.shx`
{{< /admonition >}}

## 疑难杂症

### 另存的时候不弹出对话框

**第一步** 打开`CAD`，在下端的命令栏里输入`Filedia`，回车；

**第二步** 将原来的值修改为`1`（输入数字1），回车。

点击文件/存为显示出现对话框

{{< admonition type=note title="注意事项" open=true >}}

- `FILEDIA`设置为`1`，将弹出对话框。
- `FILEDIA`设置为`0`，将显示命令行提示。

{{< /admonition >}}

### 布局状态栏跳来跳去

切换到布局选项卡以后，底部状态栏就跳来跳去，十分影响作图，解决办法如下；

**第一步** 命令行输入`STATUSBARAUTOWRAP`，回车；

```Text
STATUSBARAUTOWRAP
```

**第二步** 将原来的值修改为`OFF`，回车。

### 不能连续选择

我们在选择图元的时候，有可能会遇到这种情况，选择了第一个图形的时候，再选择第二个图形的时候，第一个会被取消选中；

**第一步** 输入命令`OP`，回车；

**第二步** 切换到「选择集」选项卡；

**第三步** 将「用`shift`键添加到选择集」取消勾选；

**第四步** 点击「应用」 --> 点击「确定」，再次选择图形就恢复正常了。

### 按F8卡顿

**第一步** 命令行输入`Tempoverrides`，回车；

```Text
Tempoverrides
```

**第二步** 将原来的值修改为`0`（输入数字0），回车。

### 布局视口显示数量

遇到布局视口某些视口不显示，但是刷新不显示的视口又会显示出来，一般就是设置了最大视口数量，按以下步骤解决：

**第一步** 命令行输入`MAXACTVP`，回车；

```Text
MAXACTVP
```

**第二步** 将原来的值修改为`64`（最大值为64），回车。

### 填充捕捉

{{< admonition type=success title=" 开启填充捕捉" open=true >}}

**第一步** 命令行输入`Osoptions`，回车；

```Text
Osoptions
```

**第二步** 将原来的值修改为`0`（输入数字0），回车。

{{< /admonition >}}

{{< admonition type=failure title=" 关闭填充捕捉" open=true >}}

**第一步** 命令行输入`Osoptions`，回车；

```Text
Osoptions
```

**第二步** 将原来的值修改为`1`（输入1），回车。

{{< /admonition >}}

### 填充比例统一

**第一步** 命令行输入`Measurement`，回车；

```Text
Measurement
```

**第二步** 将原来的值修改为`0`（输入数字0），回车。

### 解除标注关联

**第一步** 命令行输`DIMDISASSOCIATE`，回车；

```Text
DIMDISASSOCIATE
```

**第二步** 框选需要解除关联的标注。

### 最大化视口

命令行输`VPMAX`，回车；

```Text
VPMAX
```

### 重新植入PGP

修改完`PGP`文件后，执行命令立即生效；

不需要重启`CAD`软件；

命令行输`Reinit`，回车；

```Text
Reinit
```

### 选中对象，特性无属性

#### 问题描述

通过命令`PROPERTIES`或者快捷键`Ctrl + 1`打开特性面板；

却发现选中对象后，特性面板却无法显示所选对象的属性值；

#### 问题分析

这个问题在`CAD 2014`会经常碰到；

一般情况是觉得`AutoCAD 360`没什么用，还占内存，就卸载掉了?

#### 解决方法

在安装包里面找到`AcAuthEntities19chs.tlb`和`axdb19chs.tlb`；

把这两个文件放到`Auto CAD 2014`的安装根目录里面；

默认安装目录`C:\Program Files\Autodesk\AutoCAD 2014`；

也可以通过右键`CAD`图标，查看起始位置；

{{< imgcapcdn src=`/Posts/Work/AutoCAD/01_Skill/2021-10-30_21-20-34.png` alt=右键快捷方式，查看属性 width=60% >}}

关闭所有`CAD`窗口，重新启动`CAD`软件，打开文件，这个时候选择对象打开特性面板就可以查看其属性值了。

#### 文件下载

[**1、AcAuthEntities19chs.tlb**](/document/AcAuthEntities19chs.tlb)

[**2、axdb19chs.tlb**](/document/axdb19chs.tlb)

### 绘图坐标倾斜

#### 情况一、设置了等轴测草图为打开

<img class=l-img src={{< param cdnPrefix >}}/Posts/Work/AutoCAD/01_Skill/2021-10-29_15-58-33.png alt=img width=95% >

命令行输入`Isodraft`，回车；

```Text
ISODRAFT
```

{{< imgcapcdn src=`/Posts/Work/AutoCAD/01_Skill/2021-10-29_16-03-19.png` alt=输入命令 width=50% >}}

将原来的值修改为`O`（输入字母O），回车。

{{< imgcapcdn src=`/Posts/Work/AutoCAD/01_Skill/2021-10-29_16-03-30.png` alt=输入参数 >}}

{{< admonition type=abstract title=" 命令参数解释" open=true >}}

**正交（O）：** 关闭等轴测草图。

选择下列选项之一来打开等轴测草图：

**左等轴测平面（L）：**<br>
指定创建左平面，由一对 90 度和 150 度的轴定义。

**上等轴测平面（T）：**<br>
指定创建上平面，由一对 30 度和 150 度的轴定义。

**右等轴测平面（R）：**<br>
指定创建右平面，由一对 90 度和 30 度的轴定义。

{{< /admonition >}}

#### 情况二、设置了当前视口的捕捉和旋转角度

<img class=l-img src={{< param cdnPrefix >}}/Posts/Work/AutoCAD/01_Skill/2021-10-29_15-59-39.png alt=img width=95% >

命令行输入`Snapang`，回车；

```Text
SNAPANG
```

{{< imgcapcdn src=`/Posts/Work/AutoCAD/01_Skill/2021-10-29_15-59-50.png` alt=输入命令 width=50% >}}

将原来的值修改为`0`（输入数字0），回车。

<img class=l-img src={{< param cdnPrefix >}}/Posts/Work/AutoCAD/01_Skill/2021-10-29_16-00-00.png alt=img width=75% >
