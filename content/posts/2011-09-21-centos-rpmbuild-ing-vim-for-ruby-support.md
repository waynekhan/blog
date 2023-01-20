---
title: CentOS rpmbuild-ing vim for Ruby support
date: 2011-09-21T02:47:16+00:00
---

Recently I switched from Ubuntu 11.04 to CentOS 5.7, only to find out that CentOS's version of vim was build sans Ruby support:

```text
vim --version | grep ruby
```

`-ruby` as in Ruby support is unavailable. This was undesirable, as I've become a [Command-T user](https://wincent.com/products/command-t). This is an excellent plugin (for `vim`) requiring Ruby support. There are a couple of blog posts about it, but required consolidation, so here is my (mostly) repost on the solution.

The posts recommend setting up an `rpmbuild` environment for building from source, which is basically a Linux user `rpmbuild`, plus a `~/.rpmmacros` definition, plus the source RPM.

```text
# Not needed if this user exists
useradd rpmbuild

# Switch to it
su - rpmbuild

# What's in ~/.rpmmacros?
cat ~/.rpmmacros
%_topdir /home/rpmbuild/rpm
%_tmppath /home/rpmbuild/rpm/tmp

# Building for x86_64
mkdir -p rpm/{BUILD,RPMS/x86_64,RPMS/noarch,SOURCES,SRPMS,SPECS,tmp}

# Download the source RPM, removing the perl-devel dependency from vim.spec
cd rpm/SRPMS
wget http://ftp.redhat.com/pub/redhat/linux/enterprise/6Server/en/os/SRPMS/vim-7.2.411-1.6.el6.src.rpm

# Install rpmbuild
yum -y install rpm-build

# Start the build process
rpmbuild -bb ~/rpm/SPEC/vim.spec

# Install the newly-built RPM
rpm -Uvh ~/rpm/RPMS/x86_64/vim-{m,c,e}*
```

## References

* [http://m.linuxweblog.com/vim-ruby-centos](http://m.linuxweblog.com/vim-ruby-centos)
* [http://wiki.centos.org/HowTos/SetupRpmBuildEnvironment](http://wiki.centos.org/HowTos/SetupRpmBuildEnvironment)
* [http://www.lamolabs.org/blog/2662/fixing-ruby-support-in-vim-on-fedora-10-11-and-centos-5-installing-the-vim-textile-plugin/](http://www.lamolabs.org/blog/2662/fixing-ruby-support-in-vim-on-fedora-10-11-and-centos-5-installing-the-vim-textile-plugin/)
