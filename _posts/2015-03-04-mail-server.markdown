---
layout: post
title:  "搭建邮箱服务器"
date:   2015-03-04 10:59:41
categories: study
---

相关命令
----------------------

{% highlight Bash Shell Scripts %}

sudo tasksel install lamp-server

sudo tasksel install mail-server
	
{% endhighlight %}

参考资料
----------------------
<a href="http://vbird.dic.ksu.edu.tw/linux_server/0380mail_1.php" target="_blank">鸟哥的Linux私房菜（服务器架设篇）</a>

<a href="https://www.exratione.com/2014/05/a-mailserver-on-ubuntu-1404-postfix-dovecot-mysql/" target="_blank">A Mailserver on Ubuntu 14.04: Postfix, Dovecot, MySQL</a>

概念
----------------------

* MUA: Mail User Agent
* MDA: Mail Delivery Agent
* MTA: Mail Transfer Agent
* SMTP: Simple Mail Transfer Protocol(简单邮件传送协议)
* MRA: Mail Retrieval Agent
* POP: Post Office Protocol(邮政服务协议)
* IMAP: Internet Message Access Protocol