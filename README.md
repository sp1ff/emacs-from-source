emacs-from-source
=================

This directory contains the initial release of `emacs-from-source`.

See the file NEWS for user-visible changes from previous releases.

Please check the system-specific notes below for any caveats related
to your operating system.

For general building and installation instructions, see the
file [INSTALL]().

emacs-from-source is free software.  See the file COPYING for copying
conditions.  emacs-from-source is copyright by Michael Herstine.
Copyright notices condense sequential years into a range;
e.g. "1987-1994" means all years from 1987 to 1994 inclusive.

What is it?
-----------

`emacs-from-source` is a Bash shell script for bootstrapping,
compiling & managing multiple versions of Emacs compiled from source.

To build emacs from scratch do the following:

    emacs-from-source bootstrap
	===========================================================================
	bootstrapping to /tmp:

	  - the checkout directory will be emacs
	  - the install directory will be /opt/emacsen/HEAD
	===========================================================================
	Installing pre-requisites...
	Reading package lists... Done
	Building dependency tree
	Reading state information... Done
	The following additional packages will be installed:
	  binutils cpp cpp-5 dpkg-dev fakeroot g++ g++-5 gcc gcc-5 libalgorithm-diff-perl libalgorithm-diff-xs-perl
	  libalgorithm-merge-perl libasan2 libatomic1 libc-dev-bin libc6-dev libcc1-0 libcilkrts5 libdpkg-perl libfakeroot
	  libfile-fcntllock-perl libgcc-5-dev libgomp1 libisl15 libitm1 liblsan0 libmpc3 libmpx0 libquadmath0
	  libstdc++-5-dev libtsan0 libubsan0 linux-libc-dev make manpages-dev
	Suggested packages:
	  binutils-doc cpp-doc gcc-5-locales debian-keyring g++-multilib g++-5-multilib gcc-5-doc libstdc++6-5-dbg
	  gcc-multilib autoconf automake libtool flex bison gdb gcc-doc gcc-5-multilib libgcc1-dbg libgomp1-dbg
	  libitm1-dbg libatomic1-dbg libasan2-dbg liblsan0-dbg libtsan0-dbg libubsan0-dbg libcilkrts5-dbg libmpx0-dbg
	  libquadmath0-dbg glibc-doc libstdc++-5-doc make-doc
	The following NEW packages will be installed:
	  binutils build-essential cpp cpp-5 dpkg-dev fakeroot g++ g++-5 gcc gcc-5 libalgorithm-diff-perl
	  libalgorithm-diff-xs-perl libalgorithm-merge-perl libasan2 libatomic1 libc-dev-bin libc6-dev libcc1-0
	  libcilkrts5 libdpkg-perl libfakeroot libfile-fcntllock-perl libgcc-5-dev libgomp1 libisl15 libitm1 liblsan0
	  libmpc3 libmpx0 libquadmath0 libstdc++-5-dev libtsan0 libubsan0 linux-libc-dev make manpages-dev
	0 upgraded, 36 newly installed, 0 to remove and 4 not upgraded.
	Need to get 38.6 MB of archives.
	After this operation, 144 MB of additional disk space will be used.
	Get:1 http://archive.ubuntu.com/ubuntu xenial/main amd64 libmpc3 amd64 1.0.3-1 [39.7 kB]
	Get:2 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 binutils amd64 2.26.1-1ubuntu1~16.04.5 [2,311 kB]
	Get:3 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libc-dev-bin amd64 2.23-0ubuntu9 [68.6 kB]
	Get:4 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-libc-dev amd64 4.4.0-101.124 [844 kB]
	Get:5 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libc6-dev amd64 2.23-0ubuntu9 [2,082 kB]
	...
	Installing utilities for users to run.
	umask 022 && /bin/mkdir -p "/opt/emacsen/HEAD/bin"
	for file in etags ctags emacsclient  ebrowse ; do \
	  /usr/bin/install -c  ${file} \
	    "/opt/emacsen/HEAD/bin"/` \
	      echo ${file} | sed -e 's/$//' -e 's,x,x,' \
	    ` || exit; \
	done
	make[1]: Leaving directory '/tmp/emacs/lib-src'
	/usr/bin/install -c  src/emacs "/opt/emacsen/HEAD/bin/`echo emacs-27.0.50 | sed 's,x,x,'`"
	chmod 755 "/opt/emacsen/HEAD/bin/`echo emacs-27.0.50 | sed 's,x,x,'`"
	rm -f "/opt/emacsen/HEAD/bin/`echo emacs | sed 's,x,x,'`"
	cd "/opt/emacsen/HEAD/bin" && ln -s "`echo emacs-27.0.50 | sed 's,x,x,'`" "`echo emacs | sed 's,x,x,'`"
	make -C lib-src maybe-blessmail
	make[1]: Entering directory '/tmp/emacs/lib-src'
	  GEN      blessmail
	Assuming /var/mail is really the mail spool directory, you should
	run  lib-src/blessmail /opt/emacsen/HEAD/libexec/emacs/27.0.50/x86_64-pc-linux-gnu/movemail
	as root, to give  movemail  appropriate permissions.
	Do that after running  make install.
	make[1]: Leaving directory '/tmp/emacs/lib-src'
	alias emacs=/opt/emacsen/HEAD/bin/emacs
	Installing Emacs to /opt/emacsen/HEAD...done.
	alias emacs=/opt/emacsen/HEAD/bin/emacs; alias emacsclient=/opt/emacsen/HEAD/bin/emacsclient

to update an existing install:

	emacs-from-source update -s /tmp/emacs

to alias `emacs` to the version you want to run:

	eval `/vagrant/emacs-from-source aliases`
	# alias emacs=/opt/emacsen/HEAD/bin/emacs; alias emacsclient=/opt/emacsen/HEAD/bin/emacsclient

Downloading
-----------

You can find the project at https://github.com/sp1ff/emacs-from-source.

Documentation
-------------

Only the `--help` message, at present.


Bug Reporting
-------------

sp1ff@pobox.com


Git Access
----------

https://github.com/sp1ff/scribbu.

System-specific Notes
---------------------

Currently supports MacOS, Ubuntu, and RHEL.

TODO
----

  - [ ] configure with all options turned on/noted as TODO
    + [ ] MacOS
    + [ ] Ubuntu
    + [ ] RHEL
  - [ ] check out [https://github.com/sstephenson/bats](BATS) a bash-script unit test framework


-------------------------------------------------------------------------------
Copyright (C) 2017 Michael Herstine <sp1ff@pobox.com>
