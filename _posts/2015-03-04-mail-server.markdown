---
layout: post
title:  "搭建邮箱服务器"
date:   2015-03-04 10:59:41
categories: study
---

相关命令
----------------------

{% highlight Bash Shell Scripts %}

hostname mail.ianqiu.top

sudo tasksel install lamp-server

sudo tasksel install mail-server

apt-get install dovecot-core dovecot-imapd dovecot-pop3d
	
{% endhighlight %}

配置
----------------------

/etc/postfix/main.cf

```
smtp_use_tls = no
smtpd_use_tls = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes

smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes

smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_application_name = smtpd
broken_sasl_auth_clients = yes
```
/etc/dovecot/conf.d/10-auth.conf

```
disable_plaintext_auth = no
auth_username_format = %n
auth_mechanisms = plain

```

/etc/dovecot/conf.d/auth-system.conf.ext

```
passdb {
	dirver = shadow
}

userdb {
	driver = passwd
}
```
/etc/dovecot/conf.d/10-ssl.conf

```
ssl = no

```

/etc/dovecot/conf.d/10-master.conf

```
service auth {
  unix_listener /var/spool/postfix/private/auth {
    mode = 0666
  }
}
```

参考资料
----------------------
<a href="http://vbird.dic.ksu.edu.tw/linux_server/0380mail_1.php" target="_blank">鸟哥的Linux私房菜（服务器架设篇）</a>

<a href="https://www.exratione.com/2014/05/a-mailserver-on-ubuntu-1404-postfix-dovecot-mysql/" target="_blank">A Mailserver on Ubuntu 14.04: Postfix, Dovecot, MySQL</a>

<a target="_blank" href="https://github.com/marklee77/ansible-role-mailserver">ansible-role-mailserver</a>

概念
----------------------

* MUA: Mail User Agent
* MDA: Mail Delivery Agent
* MTA: Mail Transfer Agent
* SMTP: Simple Mail Transfer Protocol(简单邮件传送协议)
* MRA: Mail Retrieval Agent
* POP: Post Office Protocol(邮政服务协议)
* IMAP: Internet Message Access Protocol

端口
----------------------

* 25 (SMTP)
* 80 (HTTP)
* 110 (POP3)
* 143 (IMAP)
* 443 (HTTPS)
* 465 (SMTPS)
* 993 (IMAPS)
* 995 (POP3S)

组件
----------------------

* <a target="_blank" href="http://www.dovecot.org/">dovecot</a>
* <a target="_blank" href="http://www.postfix.org/">postfix</a>
* <a target="_blank" href="http://sourceforge.net/projects/postfixadmin/">postfixadmin</a>
* <a target="_blank" href="http://roundcube.net/">roundcube</a>


