---
title: "ORA-24454: client host name is not set when connecting from Ubuntu instance on AWS EC2"
date: 2017-07-24T04:28:49+00:00
---

So I have this Ubuntu client connecting to Oracle Database (the server). Changed its host name late last week, and then the users realized that the app is no longer working correctly...

Thankfully, it's a configuration issue which I resolved with [help from Stack Overflow](https://dba.stackexchange.com/questions/167477/ora-24454-client-host-name-is-not-set-when-connecting-from-ubuntu-instance-on) (of course). Simply update `/etc/hosts` with the correct host name -- in my case, the recently updated host name (e.g., hostname -A), problem solved!
