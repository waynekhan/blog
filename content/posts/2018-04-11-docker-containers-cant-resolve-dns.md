---
title: "Docker containers can't resolve DNS"
date: 2018-04-11T06:24:08+00:00
---

I've recently switched over to using Docker for dev. work on a Windows 10 host, and it's worked pretty well. Today, `apt-get` somehow stopped working; e.g.,

```text
...RUN apt-get update && apt-get install...
---> Running in ...
Err:1 http://security.ubuntu.com/ubuntu xenial-security InRelease
Temporary failure resolving 'security.ubuntu.com'
Err:2 http://archive.ubuntu.com/ubuntu xenial InRelease
Temporary failure resolving 'archive.ubuntu.com'
Err:3 http://archive.ubuntu.com/ubuntu xenial-updates InRelease
Temporary failure resolving 'archive.ubuntu.com'
Err:4 http://archive.ubuntu.com/ubuntu xenial-backports InRelease
Temporary failure resolving 'archive.ubuntu.com'
Reading package lists...
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial/InRelease Temporary failure resolving 'archive.ubuntu.com'
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease Temporary failure resolving 'archive.ubuntu.com'
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease Temporary failure resolving 'archive.ubuntu.com'
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease Temporary failure resolving 'security.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.
```

[This StackOverflow.com post](https://serverfault.com/questions/642981/docker-containers-cant-resolve-dns-on-ubuntu-14-04-desktop-host) suggests it might be DNS-related, so I changed it from the (default) [Google DNS config](https://docs.docker.com/config/containers/container-networking/) to [Cloudflare's](https://www.theverge.com/2018/4/1/17185732/cloudflare-dns-service-1-1-1-1). Google's seem to have been (very recently) blocked for whatever reason. Here's how my Settings -> Network looks like now:

![Docker settings](/2018-04-11-docker-settings-network.png)
