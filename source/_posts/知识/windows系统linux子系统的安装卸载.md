title: windows系统linux子系统的安装卸载
date: '2019-06-11 16:35:53'
updated: '2019-08-07 14:25:44'
tags: [子系统]
permalink: /articles/2019/06/11/1560242153673.html
---
### 安装

#### 开启windows子系统功能

在powershell中运行：
```
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```
或者：控制面板->程序和功能->启用或关闭Windows功能->勾选 适用于Linux的Windows子系统

#### 下载安装linux子系统

打开应用商城搜索“WSL”，可根据自己需求选择安装一个或多个Linux系统；

或者 点击 [github地址](https://github.com/yuk7/ArchWSL/releases) 下载archlinux对应的子系统。下载解压到C盘目录下，使用管理员权限运行Arch.exe，即可开启在windows系统下的archlinux之旅。

### 使用wslconfig命令进行管理

1. 设置默认运行的linux系统：

```
wslconfig /setdefault <DistributionName>
```

如wslconfig /setdefault archlinux ，则cmd输入bash运行archlinux

2. 卸载子系统

```
wslconfig /unregister <DistributionName>
```

如：wslconfig /unregeister ubuntu 卸载ubuntu系统。

3. 查看已安装的linux子系统

```
wslconfig /list
```

4. 设置默认用户

```
ubuntu config --default-user root
```

默认使用root用户登录ubuntu系统。


>  推荐使用open-wsl作为控制台