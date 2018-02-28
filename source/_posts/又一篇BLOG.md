---
title: 又一篇BLOG
date: 2018-01-27 00:51:04
tags:
---

## 利用Postfix和Dovecot搭建IMAP邮件系统遇到的问题
（1）错误记录报错：SMTPD：fatal: no SASL authentication mechanisms

这个问题是安装过程中，出现的第一个比较难处理的问题，解决方案找了很久，注意几个配置文件和配置位置。

    postfix的配置文件main.cf，注意修改完毕后，用postconf -n确认一下配置是否生效；
    dovecot的配置文件很多，定位在10-master.conf文件。

仔细核对之后，这个问题解决。



(2) 邮件客户端报错，无法完成认证，不支持认证方式

邮件客户端，如雷鸟，可以设置加密方式传递密码，但常用的CRAM-MD5格式，不被postfixadmin提供的MD5-CRYPT支持。因此只能选择不加密的方式传递明文密码，默认情况下服务器是不支持的，因此需要在服务器设置中，取消对这个默认限制；
