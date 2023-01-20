---
title: CentOS httpd invalid command
date: 2013-12-30T03:55:33+00:00
---

Was configuring a CentOS 6 server recently, and I decided to comment out all `httpd` (i.e., Apache web server) `LoadModule` directives. Upon restart, there were several invalid commands, so I took the time to note 'em down as it wasn't obvious (to me, at least) which commands were provided by which modules.

I liken this to a cheat sheet to <http://httpd.apache.org/docs/2.2/> then:

|Command         |Module         |
|----------------|---------------|
|AddHandler      |mod_mime       |
|Alias           |mod_alias      |
|BrowserMatch    |mod_setenvif   |
|DirectoryIndex  |mod_dir        |
|IndexOptions    |mod_autoindex  |
|LanguagePriority|mod_negotiation|
|LogFormat       |mod_log_config |
|Order           |mod_authz_host |
|TransferLog     |mod_log_config |
