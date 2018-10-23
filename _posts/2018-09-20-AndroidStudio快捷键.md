---
layout:     post
title:   Android Studio快捷键
date:       2018-09-20
author:     HarlanSong
header-img: img/upload/aa97c67c8c1d79a0ce94c0fee2a30bfd8838df307da2f-RPC97X.jpg
catalog: 	 true
tags:
    - Android
    - Android Studio
---

Ctrl+G / Ctrl+Alt+Shift+G：查询变量或者函数或者类在哪里被使用或被调用，后者是前者的复杂表现，可以选择查询范围等。

Alt+H：查找功能，全局查找

F4：查看类继承关系

F2：查看文档说明（函数使用说明）

Ctrl+E：查看最近打开过的文件

Ctrl+Shift+E：查看最近编辑过的文件

double Shift：全局查找，这个查看和Alt+H稍稍有些不同，这个是全局文件查找，到文件名称层面。

Ctrl+Shift+R：快速定位到你所想打开的文件。

Alt+↑：光标所在位置那行代码往上移动

Alt+↓：光标所在位置那行代码往下移动

Ctrl+D：删除光标所在位置那行代码

Ctrl+X：剪切光标所在位置那行代码

Alt+Shift+↓/Ctrl+C：复制光标所在行代码到下一行

Ctrl+O:快捷查找当前类中的函数，变量

Ctrl+Shift+R：修改名称

Alt+Enter：导入包

Alt+←：后退，定位到上个查看或者编辑的地方

Alt+→：往前定位，比如你定位到上个点后，想回去，就可以用这个快捷键

Ctrl+/：当行注释，反注释再按一次即可

Ctrl+Shift+/：模块注释，反注释再按一次即可,注意这边的”/“不能用小键盘的

Ctrl+Shift+小键盘/：折叠代码（Ctrl+Shift+小键盘*这个不灵了，今天没空了，后面会针对这个问题做解决，并更新上来），当然笔记本没小键盘，你可以自己改快捷键

Ctrl+Alt+S：打开settings界面

Ctrl+Alt+Shift+S：打开Project Structure界面

Alt+Shift+X：运行（Run）

Alt+Shift+D：调试运行（Debug）

Ctrl+F9：编译工程

Ctrl+Shift+K：push文件到Server（git）

Debug类快捷键

F5：但不调试进入函数内部。

F6：但不调试不进入函数内部。

F7：由函数内部返回调用处。

F8：执行到下一个断点，没断点则执行完成。

| Action  |  Mac OSX	 |  Win/Linux |
| :------------ | :------------ | :------------ |
|注释代码(//)  | Cmd + /  |  Ctrl + / |
|注释代码(/**/)|	Cmd + Option + /|Ctrl + Shift + /|
|格式化代码|	Cmd + Option + L|Ctrl + Alt + L|
|清除无效包引用|	Option + Control + O	|Alt + Ctrl + O|
|查找|	Cmd + F	|Ctrl + F|
|查找+替换	|Cmd + R	|Ctrl + R|
|上下移动代码|Option + Shift + Up/Down	|Alt + Shift + Up/Down|
|删除行|	Cmd + Delete	|Ctrl + Y|
|扩大缩小选中范围|Option + Up/Down	|Ctrl + W/Ctrl + Shift + W|
|快捷生成结构体|Cmd + Option + T|Ctrl + Alt + T|
|快捷覆写方法	|Ctrl + O|Ctrl + O|
|快捷定位到行首/尾|	Cmd + Left/Right|Ctrl + Left/Right|
|折叠展开代码块	|Cmd + Plus,Minus|Ctrl + Plus/Minus|
|折叠展开全部代码块	|Cmd + Shift + Plus,Minus|Ctrl + Shift + Plus,Minus|
|文件方法结构|Cmd + F12|	Ctrl + F12|
|查找调用的位置|Ctrl + Option + H	|Ctrl + Alt + H|
|大小写转换	|Cmd + Shift + U	|Ctrl + Shift + U|