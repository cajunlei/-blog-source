---
title: "Bat - 学习笔记"
subtitle: ""
date: 2021-10-27T15:42:53+08:00
lastmod: 2022-01-24T09:41:53+08:00
author: "守正"
authorLink: ""
description: ""
slug: "bat_study_notes"
tags: ["Bat"]
categories: ["Study"]

hiddenFromHomePage: true
hiddenFromSearch: false
---

在学习 bat 批处理过程中学习的一些笔记分享……

<!--more-->

## 常用命令

### echo 和 @

```bat
::关闭单行回显
@                      
::从下一行开始关闭回显
echo off
::从本行开始关闭回显。(一般批处理第一行都是这个)
@echo off
::从下一行开始打开回显
echo on
::显示当前是 echo off 状态还是 echo on 状态
echo
::输出一个**回车换行**，空白行，(同echo, echo; echo+ echo[ echo] echo/ echo")
echo.
```

### 窗口设置相关命令

```bat
::设置cmd窗口的标题：
title=窗口标题
::设定窗口大小：
mode con cols=30 lines=20
```

### 进入目录

```bat
::进入根目录
cd"
::显示当前目录
cd
::可以同时更改盘符和目录
cd /d d:"sdk
```

### 打开相关命令

```bat
::打开文件夹
start D:\文件夹1
::打开文件
start D:\文件夹1\test.txt
::用默认浏览器打开链接:
start www.baidu.com
::运行某个应用程序，例如：微信
start /d "C:\Program Files (x86)\Tencent\WeChat" WeChat.exe
```

### 电源相关命令

```bat
::自动关机（单位：秒）
shutdown -s -t 300
::取消自动关机
shutdown -a
::立刻重启
shutdown -r -t 0
::自动休眠（单位：秒）
shutdown -h -t 60
```

### 注释和暂停

```bat
::注释行不执行操作
REM 这是注释
::这是注释内容
::暂停命令
pause
```

### 日期和时间

```bat
::显示当前日期，并提示输入新日期，按""回车""略过输入
date
::只显示当前日期，不提示输入新日期
date /t
::显示当前时间，并提示输入新时间，按""回车""略过输入
time
::只显示当前时间，不提示输入新时间
time /t
```

### 复制当前时间到剪贴板

```bat
::定义变量 aaa 截取当前日期-时间
set aaa="%date:~0,10%-%time:~0,5%"
::将变量复制到剪贴板
set /p=Push：%aaa%<nul | clip
::显示空行
echo.
::显示提示内容
echo Push：%aaa%已复制到剪贴板
```

### 跳转命令

```bat
::行首为:表示该行是标签行，标签行不执行操作
:label
::跳转到指定标签,执行标签内容
goto label
```

### 制作菜单

```bat
:menu
cls
echo.
echo                        菜单   
echo ==========================================================
echo.
echo ――――――――――――――【1】系统文件清理       ―――――――――――
echo.
echo ――――――――――――――【2】启动Oracle服务     ―――――――――――
echo.
echo ――――――――――――――【3】关闭Oracle服务     ―――――――――――
echo.
echo ==========================================================
 
set /p user_input=请输入：
if %user_input%==1 goto a
if %user_input%==2 goto b
if %user_input%==3 goto c
if not %user_input%=="" goto z 
 
rem 系统文件清理
:a
echo 正在清除系统临时文件 *.tmp *._tmp *.log *.chk *.old 

```

### 生成文件夹目录树状结构

1. 按下 `Win+R` 打开运行，输入 `cmd` ，点击确定；
2. 使用cd + 路径的方式，进入对应的目录，若不在C盘需要在`cd`后面加上`/d`如：
```batch
cd /d D:/music
```
3. 使用`dir`命令，查看当前目录的列表，此时如果想查看某一个目录下的文件或文件名，是无法看到的；
4. 使用`tree /f`命令，当前文件夹的所有文件将以树状结构显示；
5. 使用`tree /f > tree.txt`命令，将生成的文件目录树形结构写入到`tree.txt`文件中，`tree.txt`这个文件名称是可以修改的；
6.  打开对应的文件目录，就可以看到多了一个`tree.txt`的文件，其中`tree.txt`文件里面的内容，和屏幕输出的内容是一致的。

### Xcopy命令

#### 本机复制文件或文件夹的实例

```bat
Xcopy d:\UpdateFiles e:\123  /s /e /y
```

**命令解释：** 将D盘的UpdateFiles文件夹中包含的所有东西，全部复制到E盘的123文件夹内；/s /e /y

**参数说明：** 在复制文件的同时也复制空目录或子目录，如果目标路径已经有相同文件了，使用覆盖方式而不进行提示。

#### 移动A目录的所有文件到B目录

移动A目录的所有文件到B目录，且保留A目录的目录结构；

如果A下面有子目录，则在B中也创建相同目录，并把对应目录的文件移动到B的相同目录结构位置；（含系统文件和隐藏文件）

```bat
@echo off
rem 复制指定目录的目录结构到目标目录，并移动的文件到目标目录，且保留目录结构(空目录也复制)
set ObjPath=\\192.168.1.186\Temp Files\技术部\BPD\sourceFiles\ZOFUND
set DestPath=E:\EastFax\FFPsourceFiles\sourceFiles\ZOFUND
set DestExt=* 
xcopy /s /e /h "%ObjPath%\%DestExt%" "%DestPath%"
del /a /s /q /f "%ObjPath%\"
```

### 博客字体精简半自动化

1. 在桌面新建一个空白文件，后缀名改为`.bat`；
2. 用记事本打开新建的`.bat`文件；
3. 将以下代码复制到记事本，保存双击即可使用；

```batch
@echo off
:: 定位到blog文件夹
cd D:\Cajun.Lei\Blog
:: 生成文件
hugo --theme=LoveIt --baseUrl="https://ll.sc.cn"
:: 复制public文件夹到桌面临时文件夹1
xcopy D:\Cajun.Lei\Blog\public\ D:\Desktop\博客temp11\ /s
:: 定位到复制后的文件夹1
cd D:\Desktop\博客temp11\

:: 重命名html文件并复制到临时文件夹2
setlocal enabledelayedexpansion
set FileNum=1000
::打开系统延时
dir /b/od
:: 开始复制
For /f "tokens=*" %%i in ('dir /ad /b /s "%~dp0"') do (
  For /f "tokens=*" %%j in ('dir /a-d /b /s "%%i\*.html"') do (
    if not "%%j"=="%~nx0" (
      set /a FileNum+=1 
      ren "%%j" "!FileNum:~1!.html"
    xcopy "%%i\!FileNum:~1!.html" "D:\Desktop\博客temp22\" /s
    )
  )
)
:: 删除复制后的文件夹1
rd /s /q "D:\Desktop\博客temp11"
:: 打开临时文件夹2
start explorer "D:\Desktop\博客temp22"
:: 打开html2text
start /d "D:\Cajun.Lei\Fonts\html2text" Html2Text.exe

echo.
echo 请手动将所有html文件拖入html2text软件 --> 开始转换；
echo.

pause

:: 定位到临时文件夹2
cd D:\Desktop\博客temp22
:: 合并为一个txt文件
type *.txt > D:\Desktop\aa.txt
:: 删除复制后的文件夹2
rd /s /q "D:\Desktop\博客temp22"

pause

:: 打开字体精简文件夹
start explorer D:\Cajun.Lei\Fonts\字体精简
```

## 参考链接

- [Xcopy命令参数使用介绍](https://www.jb51.net/article/48948.htm)
