---
title: linux 搭建只收不发邮件
date: 2024-10-15 13:00:00
categories: 技术
tags:
  - linux
  - mail
---

现在用 cf 自带的，域名里的`电子邮件`一键配置。

## Postfix 只收不发

搭建教程：[Postfix 快速搭建只收不发的统一邮件验证系统](https://blog.mmf.moe/post/postfix-receive-only-email/)

添加用户
``` shell
useradd -m <newuser>
chsh -s /bin/bash <newuser> # 默认 bash
vi /etc/postfix/canonical-redirect
postmap /etc/postfix/canonical-redirect && postfix reload
```

`canonical-redirect` 内容
``` txt
<newuser>@yourdomain.com <newuser>@yourdomain.com
```

## mailutils 使用教程
- `mail`：显示邮件列表
- 输入编号查看邮件
- `n`：查看下一封邮件
- `p`：查看上一封邮件
- `d`：删除当前邮件
- `q`：退出

