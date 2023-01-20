---
title: Restoring Android app data via adb push
date: 2013-09-10T14:37:55+00:00
---

After reading [CI6230](http://www.wkwsci.ntu.edu.sg/ProspectiveStudents/Graduate/MasterofScienceinInformationSystems/Pages/Curriculum.aspx) I decided to encrypt my phone storage. I was running [CyanogenMod (CM) 10.1.2](http://get.cm/get/9aO), which is awesome. But I digress.

So... the encryption went fine. It took awhile, and things were A-OK *until* I decided to tinker with my phone -- despite all of the horror stories and downtime I've endured (my colleagues can attest to that) and try [Paranoid Android (PA) 3.94](http://download.paranoidandroid.co/Developers/general/mako/pa_mako-3.94-20130806.zip). I mean, we're explorers aren't we?

So I downloaded the ROM and Google Apps zip files after doing [Titanium Backup](https://play.google.com/store/apps/details?id=com.keramidas.TitaniumBackup&hl=en) (of course!) and copied everything to my Mac (in hindsight, this was what saved me, even though I didn't realize it at that t storeime), and then rebooted to recovery.

In recovery, I realized the storage couldn't be accessed as it was encrypted. I seem to recall unrooting (and rooting) the phone, and then it wouldn't even boot into the ROM. OK, so I'd rendered my phone unworkable (again). I was stumped for awhile, but luckily Google provides [Nexus factory images](https://developers.google.com/android/nexus/images#instructions) and the [Android SDK](http://developer.android.com/sdk/index.html) so I used that to reset things. Now I had a working device, but I was unhappy because my app data was now lost. All those games state saves, and then some.

Figured I could just flash PA and then restore using TitaniumBackup, as I'd done previously. The only problem was, this didn't work anymore. I got a [parse error](http://www.titaniumtrack.com/kb/titanium-backup-kb/titanium-backup-troubleshooting.html#parse-error-when-restore-app) which I promptly ignored. I re-installed via the Play store, following by a data-only restore; i.e., just the `.properties` and `.tar.gz` files. Now this caused the applications to crash, leading me to think that my files were encrypted. I got sidetracked by the fact that the applications crashed repeatedly, and Liya could only display the [Liya](https://itunes.apple.com/dk/app/liya/id455484422?mt=12) the table structure, but nada data.

Did a ton of research trying to find out what happened:

I even used OpenSSL to decrypt -- or attempt, at least -- since I remembered my PIN, and I knew the cipher; e.g.,

```text
openssl aes-128-cbc -d -in financisto.db -nosalt -out financisto.db.clear
```

So... I'm a noob. `vim` gave a hint, in that the DML was not actually enciphered. I could see something like `create table...`, I ignored that. Then I realized then AES 128 ciphertext didn't even look like what I had, and then I opened it using `sqlite3`:

```text
sqlite3 financisto.db
SQLite version 3.7.7 2011-06-25 16:35:41
Enter ".help" for instructions
Enter SQL statements terminated with a ";"
sqlite> select * from transactions;
1|1|0|0|0|0|Opening amount (MYR)|53400|0|1300572979084||0.0|0.0|0.0||0||||UR||0|1300572979086|0|0|0|0
```

OK, nothing was encrypted after all, but my apps wouldn't work. The trick was to use adb push to individually push files into the device. It's pretty tedious, but in the end it worked for me. Just `tar -xof` the `.tar.gz`, then descend into data/data for the list of files to push over:

```text
FOO=/data/data/ru.orangesoftware.financisto/databases/
BAR=financisto.db
adb push ~/Dropbox/Mako/TitaniumBackup/$FOO/$BAR $FOO
```

Setting the envvars will help things move along a lot faster, then after that you _should_ see data in-app.

Hope this helps some poor paranoid soul like myself sometime soon. Of course, your mileage will vary.

## References

* [https://santoku-linux.com/howto/mobile-forensics/how-to-brute-force-android-encryption](https://santoku-linux.com/howto/mobile-forensics/how-to-brute-force-android-encryption)
* [https://www1.informatik.uni-erlangen.de/frost](https://www1.informatik.uni-erlangen.de/frost)
* [http://www.slideshare.net/the_netlocksmith/defcon-20-gaining-access-to-user-android-data](http://www.slideshare.net/the_netlocksmith/defcon-20-gaining-access-to-user-android-data)
