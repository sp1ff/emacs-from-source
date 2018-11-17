emacs-from-source
=================

This directory contains release 1.1.1 of `emacs-from-source`.

See the file NEWS for user-visible changes from previous releases.

Please check the system-specific notes below for any caveats related
to your operating system.

For general building and installation instructions, see the file
[INSTALL]().

`emacs-from-source` is free software.  See the file LICENSE for
copying conditions.  `emacs-from-source` is copyrighted by
[sp1ff](https://github.com/sp1ff/).  Copyright notices condense
sequential years into a range; e.g. "1987-1994" means all years from
1987 to 1994 inclusive.

What is it?
-----------

`emacs-from-source` is a [Bash](https://www.gnu.org/software/bash/)
shell script for bootstrapping, compiling & managing multiple versions
of [Emacs](https://www.gnu.org/software/emacs/), compiled from source.

To bootstrap your installation, do:

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
	  binutils...
	umask 022 && /bin/mkdir -p "/opt/emacsen/HEAD/bin"
	for file in etags ctags emacsclient  ebrowse ; do \
	  ...
	make[1]: Leaving directory '/tmp/emacs/lib-src'
	/usr/bin/install -c  src/emacs "/opt/emacsen/HEAD/bin/`echo emacs-27.0.50 | sed 's,x,x,'`"
	...
	Installing Emacs to /opt/emacsen/abb033ed7d244252d04911f5c6fd...done.
	alias emacs=/opt/emacsen/abb033ed7d244252d04911f5c6fd/bin/emacs; alias emacsclient=/opt/emacsen/abb033ed7d244252d04911f5c6fd/bin/emacsclient

This will leave you with the
[Emacs](https://www.gnu.org/software/emacs/) git repo checked out to
master/HEAD in `/tmp/emacs`, and the compiled binaries installed in
`/opt/emacsen/abb033ed7d244252d04911f5c6fd`. `abb033ed7d244252d04911f5c6fd`
names the most recent git commit on master in the git repo; i.e. the
commit from which you built. This is inconvenient to type, so do
`emacs-from-source make-current abb033ed7d244252d04911f5c6fd`; this
will create a symlink `/opt/emacsen/current ->
abb033ed7d244252d04911f5c6fd`.

To try out a particular release, do:

    emacs-from-source update -s /tmp/emacs -t emacs-26.1

This will leave the git repo at `/tmp/emacs` with the `emacs-26.1` tag
checked out, and the binaries built therefrom in `/opt/emacsen/26.1`.

To try a given commit on a given branch, do:

    emacs-from-source update -s /tmp/emacs -b foo 623d37a...

This will leave your git repo at the named commit on branch `feature/foo'.
The Emacs built therefrom will be in `/opt/emacsen/foo-623d37a...`.

As a convenience, the program can output
[Bash](https://www.gnu.org/software/bash/) code creating aliases for
[Emacs](https://www.gnu.org/software/emacs/) binaries at your
preferred location. Suppose you decide you want to use the `emacs`
built from the last `update`. You could add the following logic to
your `.bashrc`:

    eval `emacs-from-source aliases -b foo 623d37a...`
	# Will output
	# alias emacs=/opt/emacsen/foo-623d37a.../bin/emacs; alias emacsclient=/opt/emacsen/foo-623d37a.../bin/emacsclient

Once you settle on one, you may want to do:

   emacs-from-source make-current XYZ
   # This will create a symlink /opt/emacsen/current -> /opt/emacsen/XYZ
   # and /opt/emacsen/last -> <whatever curent points to now>
   eval `emacs-from-source alias XYZ`
   # Will output
   # alias emacs=/opt/emacsen/current/bin/emacs; alias emacsclient=/opt/emacsen/current/bin/emacsclient

If that doesn't work out:

    emacs-from-source revert
	# Will swap /opt/emacsen/current to /opt/emacsen/last


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

`git clone https://github.com/sp1ff/scribbu.`

System-specific Notes
---------------------

Currently supported on MacOS, Ubuntu, and RHEL.

TODO
----

  - [ ] branch names with '/' will break on install
  - [ ] configure with all options turned on/noted as TODO
    + [ ] MacOS
    + [ ] Ubuntu
    + [ ] RHEL
  - [ ] check out [https://github.com/sstephenson/bats](BATS) a bash-script unit test framework


-------------------------------------------------------------------------------
Copyright (C) 2017-2018 Michael Herstine <sp1ff@pobox.com>
