---
layout: default
title: Embedding Chibi Scheme in Your C++ XCode Project
published: true
---

In this post I will explain how to set up Chibi Scheme in a C++ project using XCode 8.
I will be using Homebrew for installing Chibi.

### Xcode Command-line Tools

You will need Xcode's command-line tools. First run `xcode-select -p` from the
terminal. If you see `/Applications/Xcode.app/Contents/Developer`, you are good
to go; otherwise, run `xcode-select --install` and click "Install". Run
`xcode-select -p` once again to ensure your success.

### Installing Homebrew

I will assume you already have Ruby installed. From your cli, run

```
ruby -e “$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)”
```

To ensure proper installation, run `brew doctor`.

### Installing Chibi

In your terminal, run `brew install chibi-scheme`. Your done, assuming the installation
was successful.

### Embedding Chibi into Your Project

Another assumption I will make is that you have an existing Xcode C++ project.
In your project navigator (the folder icon in your sidebar), click on your project.
Now select the "Build Settings" tab. You can use the search bar to look for "header".
Within the "Search Paths" section, expand "Header Search Paths". You will do the next
step for setting both the "Debug" and "Release" search paths.

Click the "+" and add the path `/usr/local/include`. Again, this is for both "Debug"
and "Release".

If you do not have a *Frameworks* folder within your project, create one now. Open
finger and navigate to `/usr/local/lib`. Grab the *.dylib* of the version of Chibi
you will be using. This file will take the form of `libchibi-scheme.<verison>.dylib`.
It is important that you grab the actual *.dylib* file and not a symlink pointing
to that file. Drag this over to Xcode and into your *Frameworks* folder.

At the top of the file(s) you will be using Chibi in, insert #include `<chibi/eval.h>`.
That's it.
