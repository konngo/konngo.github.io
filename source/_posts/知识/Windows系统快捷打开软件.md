title: Windows系统快捷打开软件
date: '2019-06-12 10:19:11'
updated: '2019-08-07 14:18:50'
tags: [bat, windows]
permalink: 1560305951731.html
excerpt: dos脚本
---
> 达成效果：按win+1键打开命令行窗口。在命令行窗口内输入软件名称，成功打开软件。

### 1.编辑StartApp.bat
```bash
@echo off
set Obj_Length=100

::firefox
set Obj[0].Name=firefox
set Obj[0].Value=firefox.exe
:: 按以上格式添加打开文件的指令
set Obj_Index=0
set t=
set /p appName=%t%
:LoopStart
if %Obj_Index% EQU %Obj_Length% goto:EOF
SET Obj_Current.Name=0
SET Obj_Current.Value=0
FOR /F "usebackq delims==. tokens=1-3" %%I IN (`SET Obj[%Obj_Index%]`) DO (
  SET Obj_Current.%%J=%%K
)
if "%appName%"=="%Obj_Current.Name%" start "" %Obj_Current.Value% & goto:eof
set /A Obj_Index=%Obj_Index% + 1
GOTO LoopStart

```


### 2.设置快捷键

1. 将StartApp.bat文件名修改为：StartApp.exe，将文件拖放至windows桌面的工具栏第一位，将StartApp.exe的文件名还原为StartApp.bat。
2. 在C:\Users\LiJunPeng\AppData\Roaming\Microsoft\Internet Explorer\Quick Launch\User Pinned\TaskBar目录下，将StartApp.exe修改为StartApp.bat。
3. 此时可通过win+1键打开StartApp.bat的命令行窗口。

> 软件无法打开，请在Path中设置环境变量。

### 3.通过StartApp.bat打开数据库

新建Mysql.bat文件，将Mysql.bat文件所在目录添加到环境变量PATH目录中。mysql.bat文件内容如下：
```
@echo off
cd C:\Users\LiJunPeng\Documents\mysql-8.0.11-winx64\bin
mysql -u root -p
```
完成之后，在StartApp.bat目录下，添加mysql.bat的name和value。





####  常用软件目录
```
::firefox
set Obj[0].Name=firefox
set Obj[0].Value=firefox.exe
::chrome
set Obj[1].Name=chrome
set Obj[1].Value=chrome.exe
::vs code
set Obj[2].Name=vs
set Obj[2].Value=Code.exe
::Office EXCEL
set Obj[3].Name=excel
set Obj[3].Value=EXCEL.EXE
::Office POWERPNT
set Obj[4].Name=ppt
set Obj[4].Value=POWERPNT.EXE
::Office WORD
set Obj[5].Name=word
set Obj[5].Value=WINWORD.EXE
::PotPlayerMini64
set Obj[6].Name=player
set Obj[6].Value=PotPlayerMini64.exe
::IntelliJ IDEA
set Obj[7].Name=idea
set Obj[7].Value=idea64.exe
set Obj[8].Name=eclipse
set Obj[8].Value=eclipse.exe
set Obj[9].Name=mysql
set Obj[9].Value=mysql.bat
set Obj[10].Name=notepad
set Obj[10].Value=notepad++.exe
:: 按以上格式添加打开文件的指令

```