---
title: ProFTPD for CentOS 6
date: 2014-10-29T06:11:52+00:00
---

More of a note to self than anything. As usual, [YMMV](https://www.google.com/search?q=ymmv).

## Use ~~RPMforge~~ RepoForge package

```text
wget http://pkgs.repoforge.org/rpmforge-release/rpmforge-release-0.5.3-1.el5.rf.x86_64.rpm
rpm -Uvh rpmforge-release-0.5.3-1.el5.rf.x86_64.rpm
yum install proftpd -y
chkconfig --level 345 proftpd on
/etc/init.d/proftpd restart
netstat -tnlp|grep proftpd
```

## Configure `iptables`

```text
iptables -A INPUT -p tcp -m tcp --dport 21 -j ACCEPT
etc/init.d/iptables save
etc/init.d/iptables restart
```

## New Linux user; e.g., `foo`

```text
useradd foo -p /path/to/home/directory
passwd foo
```

## Does it work?

```text
Command: USER foo
Response: 331 Password required for foo
Command: PASS ********
Response: 530 Login incorrect.
Error: Critical error: Could not connect to server
```

## Errors in `/var/log/secure`

```text
Oct 29 03:41:07 bar proftpd: PAM unable to dlopen(/lib64/security/pam_stack.so): /lib64/security/pam_stack.so: cannot open shared object file: No such file or directory
Oct 29 03:41:07 bar proftpd: PAM adding faulty module: /lib64/security/pam_stack.so
Oct 29 03:41:07 bar proftpd[36319]: 127.0.0.1 (192.168.128.29[192.168.128.29]) - USER foo (Login failed): Incorrect password.`
```

## Fix PAM config for `proftpd-1.3.4a-1.el6.rf.x86_64`; e.g.,

```text
# cat /etc/pam.d/proftpd
#%PAM-1.0M-1.0
auth required pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed
auth required pam_shells.so
auth include system-auth
account include system-auth
session include system-auth
session required pam_loginuid.so
```

## Does it work now?

```text
Command: PWD
Response: 257 "/" is the current directory
Command: TYPE I
Response: 200 Type set to I
Command: PASV
Response: 227 Entering Passive Mode.
Command: MLSD
Error: Connection timed out
Error: Failed to retrieve directory listing`
```

## Configure passive FTP (PASV)

```text
# iptables -A INPUT -p tcp -m multiport --dports 60000:65535 -j ACCEPT
# etc/init.d/iptables save; etc/init.d/iptables restart
# grep passiveport /etc/proftpd.conf
PassivePorts 60000 65535
# /etc/init.d/proftpd restart
```

## Does it work, at long last?

```text
Command: MLSD
Response: 150 Opening ASCII mode data connection for MLSD
Response: 226 Transfer complete
Status: Directory listing successful
```

## References

* [http://www.linfo.org/useradd.html](http://www.linfo.org/useradd.html)
* [http://pkgs.org/centos-6/repoforge-x86_64/proftpd-1.3.4a-1.el6.rf.x86_64.rpm.html](http://pkgs.org/centos-6/repoforge-x86_64/proftpd-1.3.4a-1.el6.rf.x86_64.rpm.html)
* [http://www.proftpd.org/docs/howto/NAT.html](http://www.proftpd.org/docs/howto/NAT.html)
* [http://blog.redbranch.net/2012/04/17/proftpd-centos-6-pam-unable-to-dlopen-lib64securitypam_stack-so/](http://blog.redbranch.net/2012/04/17/proftpd-centos-6-pam-unable-to-dlopen-lib64securitypam_stack-so/)
* [http://serverfault.com/questions/594835/what-is-the-correct-way-to-open-a-range-of-ports-in-iptables](http://serverfault.com/questions/594835/what-is-the-correct-way-to-open-a-range-of-ports-in-iptables)
