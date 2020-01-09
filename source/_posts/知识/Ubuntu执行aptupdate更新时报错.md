title: Ubuntu 执行 apt update 更新时报错
date: '2019-06-11 16:27:34'
updated: '2019-08-07 14:27:00'
tags: [Ubuntu, linux]
permalink: /articles/2019/06/11/1560241654637.html
---
```
Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

显示dpkg被锁住，无法进行apt update 或者apt-get 等操作。

执行以下操作：


#删除/var/lib/dpkg/lock文件
sudo rm  /var/lib/dpkg/lock

#按照提示执行sudo dpkg --configure -a 命令时，
#依然报如下错误:
dpkg: error: parsing file '/var/lib/dpkg/updates/0032' near line 0: newline in field name '#padding'

#查找网上资料，清除apt缓存
sudo apt clean
#删除/var/lib/dpkg/updates/下所有文件
sudo rm /var/lib/dpkg/updates/*

#再次执行更新程序，一切正常。
sudo apt update