title: ssr搭建
date: '2019-07-01 14:02:52'
updated: '2019-11-06 23:14:33'
tags: [待分类]
permalink: 1561960972309.html
---
> 不要用于任何商业使用。

## ssr搭建

购买vps服务器的过程省略。如有困难请[查看](https://www.jianshu.com/p/3d0345505dcc) ，尽量使用centos7操作系统。


连接上服务器后，输入：
```
 wget -N --no-check-certificate https://raw.githubusercontent.com/ToyoDAdoubi/doubi/master/ssrmu.sh && chmod +x ssrmu.sh && bash ssrmu.sh
```

根据自己需要填写用户名密码混淆规则之类，如果不会就一路回车。

如果安装成功会显示如下：
```
1.  ############################################################
2.  用户 [doubi] 的配置信息：
4.  I P : xxx.xxx.xxx.xxx
5.  端口 : 2333
6.  密码 : doub.io
7.  加密 : aes-128-ctr
8.  协议 : auth_aes128_md5
9.  混淆 : plain
10.  设备数限制: 5
11.  单线程限速: 666 KB/S
12.  端口总限速: 2333 KB/S
13.  禁止的端口 : 无限制
15.  已使用流量 : 上传: XXX KB + 下载: XXX MB = XXX MB
16.  剩余的流量 : 980 MB
17.  用户总流量 : 1 GB
19.  SS 链接: ss://xxxxxxxxxxxxx
20.  SS 二维码: http://pan.baidu.com/share/qrcode?w=300&h=300&url=ss://xxxxxxxxxxxxx
21.  SSR 链接: ssr://xxxxxxxxxxxxx
22.  SSR 二维码: http://pan.baidu.com/share/qrcode?w=300&h=300&url=ssr://xxxxxxxxxxxxx
24.  提示:
25.  在浏览器中，打开二维码链接，就可以看到二维码图片。
26.  协议和混淆后面的[ _compatible ]，指的是 兼容原版协议/混淆。
28.  ############################################################
```

脚本使用说明：

```
1.  bash ssrmu.sh
3.  # 还有一个 运行参数，是用于所有用户流量清零的
4.  bash ssrmu.sh clearall
5.  # 不过不需要管这个，可以通过脚本自动化的设置 crontab 定时运行脚本
```

输入相应的数字执行命令：

```
ShadowsocksR MuJSON 一键管理脚本 [vX.X.X]
 ---- Toyo | doub.io/ss-jc60 ----
  1. 安装 ShadowsocksR
  2. 更新 ShadowsocksR
  3. 卸载 ShadowsocksR
  4. 安装 libsodium(chacha20)
  ————————————
  5. 查看 账号信息
  6. 显示 连接信息
  7. 设置 用户配置
  8. 手动 修改配置
  9. 配置 流量清零
  ————————————
  10. 启动 ShadowsocksR
  11. 停止 ShadowsocksR
  12. 重启 ShadowsocksR
  13. 查看 ShadowsocksR 日志
  ————————————
  14. 其他功能
  15. 升级脚本
  当前状态: 已安装 并 已启动
  请输入数字 [1-15]：
```


## BBR加速

输入一键脚本：
```
wget -N --no-check-certificate "https://raw.githubusercontent.com/chiakge/Linux-NetSpeed/master/tcp.sh" && chmod +x tcp.sh && ./tcp.sh`
```
运行成功之后：

![057054220051865.jpg](https://img.hacpai.com/file/2019/07/057054220051865-8d24b18a.jpg)


( 这个截图看起来就很快....

选择1，会提示你重新启动服务器（可能，我也忘了，反正提示你就确定重启启动服务器，然后你重新连接就好），然后选择4。


这样整个的ssr就搭建完毕了。

更新:

```
ssr://MTA4LjE2MC4xMzcuMTk5OjIzMzM6YXV0aF9hZXMxMjhfbWQ1OmFlcy0xMjgtY3RyOnBsYWluOlpHOTFZaTVwYncvP29iZnNwYXJhbT0mcHJvdG9wYXJhbT0mcmVtYXJrcz1NVEE0TGpFMk1DNHhNemN1TVRrNSZncm91cD0
```
