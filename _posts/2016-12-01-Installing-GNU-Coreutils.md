---
layout: post
title: Installing GNU Coreutils
date: '2016-12-01'
categories: snippet
---

```
D-128-95-149-192:~ sr320$ brew install coreutils
Updating Homebrew...
==> Auto-updated Homebrew!
Updated 1 tap (homebrew/core).
==> Updated Formulae
mercurial

==> Downloading https://homebrew.bintray.com/bottles/coreutils-8.26.yosemite.bot
######################################################################## 100.0%
==> Pouring coreutils-8.26.yosemite.bottle.tar.gz
==> Caveats
All commands have been installed with the prefix 'g'.

If you really need to use these commands with their normal names, you
can add a "gnubin" directory to your PATH from your bashrc like:

    PATH="/usr/local/opt/coreutils/libexec/gnubin:$PATH"

Additionally, you can access their man pages with normal names if you add
the "gnuman" directory to your MANPATH from your bashrc as well:

    MANPATH="/usr/local/opt/coreutils/libexec/gnuman:$MANPATH"

==> Summary
🍺  /usr/local/Cellar/coreutils/8.26: 430 files, 8.5M
D-128-95-149-192:~ sr320$ 

```



