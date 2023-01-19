---
title: Clear cached PuTTY's SSH keys
date: 2017-05-24T09:24:15+00:00
---

For all those of you who have been trying to clear Putty’s cache of host fingerprints (Windows) for development or testing, here is the answer:
 
1. Open the registry (regedit)
1. Go to HKEY\_CURRENT\_USER\Software\SimonTatham\PuTTY\SshHostKeys
1. Delete the rows that you need and presto!

Nice, TIL.
