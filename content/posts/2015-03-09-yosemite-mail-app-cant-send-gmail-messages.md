---
title: Yosemite Mail.app can't send Gmail messages
date: 2015-03-09T06:06:23+00:00
---

Recently, I decided to download all my mail into Mail.app. I wanted to be able to receive and send using my existing Gmail account, but it didn't work for me. I kept getting a prompt that Gmail was offline, when I knew otherwise. (Sending via mail.google.com web app worked, for example.)

After some digging, I found the solution in an [Apple discussion forum](https://discussions.apple.com/thread/5728261). In case the answer ever gets buried (I hope not), it is related to truncation of the SMTP username; e.g. `foo@gmail.com` is shortened to `foo`. This does not work.

To change, load up Mail, then click into Preferences > Accounts > Outgoing Mail Server (SMTP) > Edit SMTP Server List. Switch to the Advanced tab, then change the "User Name" field.

As a reference, mine looks like:

![Accounts](/2015-03-09-accounts.png)

As usual, your mileage may vary. (And you'll need to enable [IMAP for Gmail](https://support.google.com/mail/troubleshooter/1668960?hl=en#ts=1665018), too.)
