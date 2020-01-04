---
title: Let's Make A Web App  -  Part 1 - Developer Tools
description: This is part 2 in a series that is following me making an application using React and Node as the primary platform. This part is all about getting your your developer tools installed and configured.
---


![Photo by Todd Quackenbush on Unsplash](https://cdn-images-1.medium.com/max/1200/0*DhASlU9-h1PjEc_5)

In order to develop this application, it's expected that you will have certain tools installed and configured from the start. I will detail each area for Linux, MacOS and Windows.  At the end of this article, you should have the following installed and configured.

* Build Tools (C++, Python2, curl)
* nvm and node
* git
* kdiff3
* bash or zsh
* Starship
* Visual Studio Code
* Docker


# Build Tools

In order to build node projects, not only do you need Node, but you also need some additional build tools in order to handle binary compiled modules in Node.

## Linux

Use your package manager for this.  For debian/ubuntu/pop users, you can use the following command.

```
sudo apt install build-essential curl python2 git
```

## MacOS

First install [Homebrew](https://brew.sh/), which should be a good place to start from, this will give you your build tools and some extras.

##Windows

Pay close attention to the next section (Node), which will include a step for installing developer tools needed for Node.


# Node

## Linux and MacOS

Use these instructions to [install nvm](https://github.com/nvm-sh/nvm).  After you have installed and configured, you will want to use `nvm i 12.13 && nvm use 12.13`

## Windows

* Download and run the installer for [Node](https://nodejs.org/en/)
* Make sure to check the box to install developer tools on the last screen

After installation is complete you will now have Node as well as C++ build tools, python 2.7.x and chocolatey installed

Optionally, you may Download [nvm for windows](https://github.com/coreybutler/nvm-windows/releases), this version of nvm is not the same as for Linux and MacOS and is optional.  You should do this after intalling the Node release to add the build tools.


# Git

We're using Git for source control, you should install the tooling you need.

## Linux

You should have it installed with the Build Tools apt command above already.

## MacOS

You have an older version of git during the tooling install for Homebrew, you should update it with `brew install git`.  You should see [this answer](https://apple.stackexchange.com/a/93179/49048) to make sure you're using the version installed via homebrew.

## Windows

You will be getting several tools installed with git, because of this, the instructions are detailed below, please be sure to follow carefully. Start by downloading [Git](https://git-scm.com/downloads) for windows and starting the install.

* **Select Components:** check the Windows explorer integration as well as the association options.
* **Default Editor:** choose the custom option, and in the field enter `notepad.exe` while you may be tempted to have more options integrated, the editor you use really needs to be able to exit cleanly. Notepad is really the friendliest option for this one.
* **PATH environment:** use Git and optional Unix tools from the Windows Command Prompt. This will give you the least hassle in practical use, there is a warning, and unless you are using those specific tools this is absolutely the most headache free option for most people.
* **HTTPS transport:** Use the native Windows Secure Channel Library.
* **Line Ending Conversions:** Checkout as-is, commit Unix-style line endings. While not the default, this will give you the least problems working with others in the future of your projects consistently. If you have files that are specifically binary, you should use a .gitattributes file in your project to define them, and it will work out best this way.
* **Terminal Emulator:** Use Windows' default console window. This, again, will give you the least headaches most of the time. If you want a different more feature rich terminal viewer, I would suggest looking at Cmder or the new Windows Terminal.

IIRC, there is an option to install and use a credential manager, go ahead and choose this option.


## All

You should now configure your username and email address to be used by git.

```bash
git config --global user.name "Your Real Name"
git config --global user.email "you@yourdomain"
```


# kdiff3 (recommended)

I recommend having a merge tool that supports 3-way merging. Kdiff3 is a pretty good option, there are others, but are beyond the scope of this article.

## Linux

```sudo apt install kdiff3```

## MacOS

```brew cask install kdiff3```

## Windows

```choco install kdiff3```

## All

Configure git to use kdiff3.

```bash
git config --global --add merge.tool kdiff3
git config --global --add diff.tool kdiff3
```

Windows users should also add the following:

```bash
git config --global --add mergetool.kdiff3.path "C:/Program Files/KDiff3/kdiff3.exe"
git config --global --add mergetool.kdiff3.trustExitCode false
git config --global --add difftool.kdiff3.path "C:/Program Files/KDiff3/kdiff3.exe"
git config --global --add difftool.kdiff3.trustExitCode false
```


# Starship (recommended)

I recommend that you install and configure [Starship](https://starship.rs/) with your bash terminal. It works in most configurable shells and installation options vary.


# Visual Studio Code (recommended)

There are those who love [Visual Studio Code](https://code.visualstudio.com/) (VS Code) and few that don't like it. My own opinion is it's a near perfect mix of editor and tools. The git integration is decent, though I tend to just use the command line. The integrated terminal is one of the most useful features I've seen in any text editor or IDE anywhere, ever. It's right with me, and the project I'm working on, which allows me to run whatever commands I need right there.

## Linux

Use the official snap version where available. `sudo snap install --classic code`

## MacOS and Windows

Use the [direct download](https://code.visualstudio.com/Download), which includes automatic update functionality.


# Docker

Linux users will be installing the native Docker Engine (Community Edition), while MacOS and Windows users will be installing Docker Desktop.

## Linux

* [Installation](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
* [Post-Installation](https://docs.docker.com/install/linux/linux-postinstall/)

## MacOS

Download and install [Docker Desktop for Mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac) or use `brew cask install docker`

## Windows

Download and install [Docker Desktop for Windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows) directly or `choco install docker-desktop --pre`. 

***DO NOT*** enable windows containers, you want to use Linux containers, which are more broadly supported and what is expected the vast majority of the time.

## MacOS and Windows

Docker Desktop will need to complete configuration including setting up a [Docker Hub](https://hub.docker.com/) account.  You will also need to configure drive access in order to transfer files in and out of your desktop into containers.



# Summary

Hopefully you find this article useful, I had started it as part of Application Structure but decided to break it off separately so I could add more detail.