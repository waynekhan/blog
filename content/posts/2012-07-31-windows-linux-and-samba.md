---
title: Windows, Linux and Samba
date: 2012-07-31T06:20:10+00:00
---

I needed to copy a 140 megabyte file from a Windows 2000 server. The only problem was that it didn't support FTP (or SFTP) and I couldn't download FileZilla Server since there was no network connection. I asked my colleague for a quick fix to this, and I can't recall what he said, but suddenly I remember that I'd RHEL 3 (and Samba) and I could use Windows to map a Samba share. Problem solved.

Sometimes it is thinking about a problem from a different perspective client/server instead of server/client. Heh
