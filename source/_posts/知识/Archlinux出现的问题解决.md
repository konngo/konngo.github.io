title: Archlinux出现的问题解决
date: '2019-06-11 16:03:51'
updated: '2019-08-07 14:29:10'
tags: [archlinux, linux]
permalink: /articles/2019/06/11/1560240231478.html
---
# pacman更新时报错 signature is invalid

```
rm -R  /etc/pacman.d/gnupg/      # 删除gnupg目录及其文件
 pacman-key --init
 pacman-key --populate archlinux
 pacman-key --populate archlinuxcn    # 启用了archlinux中文软件库的还要执行这个
```