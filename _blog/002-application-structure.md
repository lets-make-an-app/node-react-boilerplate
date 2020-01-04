---
title: Let's Make A Web App  -  Part 1 - Application Structure
description: This is part 1 in a series that is following me making an application using React and Node as the primary platform. This part is all about getting your your application structure and environment ready.
---
# Let's Make A Web App - Part 1- Application Structure

This is part 1 in a series that is following me making an application using React and Node as the primary platform. As I progress, I will duplicate and update the Index on [Part 0](000-announcement.md), as well as a links to the adjacent article.

[< Part 0 - Getting Started](000-announcement.md)
> Part 2 - TBD

![Photo by Cristina Gottardi on Unsplash](https://cdn-images-1.medium.com/max/1200/0*DCoU7Hz9ExKSV02L)

I'm literally writing this and flushing out the portions of the article as I work in effort to capture as much detail as I can in terms of organizing my thoughts. I'd started with cloning the repository below, but inserted "Project Management" and "Install Your Tools" into the article/workflow very quickly.


# Project Management

As this project is in a [repository on Github](https://github.com/lets-make-an-app/node-react-boilerplate/), I'll be using the build in [Project Boards](https://help.github.com/en/github/managing-your-work-on-github/about-project-boards) feature in order to organize tasks. I'll be using the "Basic Kanban" style. This works very well for individual developers or a smaller team or number of workers on a specific project. In the workplace, I'm most familiar with an Agile workflow using what is now [Azure DevOps](https://azure.microsoft.com/en-us/services/devops/) (formerly Team Foundation Server and Visual Studio Team Services).

After creating the project board, I added a couple of columns, here's my final order.

**To do**- this is the default starting point, I didn't change this. I did look at the first checklist in starting out, but didn't do all the things, I moved the checklist card into the done column, then archived.

**Research** - (added) at this point, the issue/task needs to be better defined in order to move to the approved column for mainline development. This step may include creating a branch and/or doing research in order to get a task ready to work on.
Approved - (added) this is my work queue, items should only move here when they're actually ready to be worked on, well thought out and not before. For features related to the articles, I will prefix a 5-character padded number to the beginning, if I were using DevOps in a non-blog series, I'd reference the assigned ID and may continue to do so in my commits (as I figure this out).

**In Progress**- this is work that is actively being done now.

**Dev Complete** - (added) this is where a pending review should happen, development is complete, and a pull request is made, but shouldn't move past a QA/Staging environment until code review happens. This is here for tracking. In a live project, this would be a point where a QA application deployment may happen and/or other stages might be inserted into the release/approval workflow.

**Done** - this means the pull request has been merged, and once configured the project will be build/deployed to a production server. After a feature/sprint/progress review, the card will be archived.


# Beginning Structure

I first added a note/card to the Top of the todo list concerning this article… One of the things I didn't know off the top of my head was the markdown syntax for a checkbox/list - [ ] and - [x] for unchecked/checked respectively.

In future posts, I'll probably start with the card checklist and work through filling things out as I go. For an existing project phase, you will likely want to have some or all of the following items in practice before moving an item to Accepted status.

* Well Defined Story
* Dependencies Identified
* Sized / Estimated
* User Experience Defined & Artifacts Ready
* Performace Criteria Identified
* Acceptance Criteria Defined
* Feature Owner Identified
* Demonstration Needs Identified

For a smaller project, this may not be needed… for larger projects with potentially multiple teams working on a project/product, it becomes essential.
The checkboxes for this article are as follows…

* 00001 Application Structure
* Start blog article
* Clone Repository
* Add docs/blog entries to current
* Add initial documentation
* Add blog details
* Add initial project structure
* Add blog details
* Detail on commit/pr/etc
* Dev Complete / PR
* Merge Compelte / Done


# Install Your Tools

In order to do work, you need the tools to get your job done.  First you're going to need some build tools.  I will detail each area for Linux, MacOS and Windows in order.  I'm doing windows last in each section as some details will be more lengthy.  After this section, you should have the following tools installed and configured.

* Build Tools (C++, Python2, curl)
* nvm and node
* git
* kdiff3
* bash or zsh
* Starship
* Visual Studio Code
* Docker

## Build Tools

**Linux** - users can use your package manager for this.  For debian/ubuntu/pop users, you can use the following command.

```
sudo apt install build-essential curl python2 git
```

**MacOS** - users should first install [Homebrew](https://brew.sh/), which should be a good place to start from.

**Windows** - users will install with Node in the next section.


## Node

**Linux** - users should [install nvm directly](https://github.com/nvm-sh/nvm).  Make sure to add the statement to your `~/.bashrc` file and reload your terminal (or run it directly) and run `nvm i 12.13`.

**MacOS** - users can install with `brew install nvm`, make sure to add the appropriate output to your `~/.bashrc` or `~/.zshrc` file, reload your terminal and run `nvm i 12.13`.

**Windows** - Download and run the installer for [Node](https://nodejs.org/en/) look for the checkbox to download and install developer tools, you will want to check this.  After installation is complete you will now have Node as well as C++ build tools, python 2.7.x and chocolatey installed

**Windows (optional)** - Download [nvm for windows](https://github.com/coreybutler/nvm-windows/releases), this version of nvm is not the same as for Linux and MacOS and is optional.  You should do this after intalling the Node release to add the build tools.

**Linux and MacOS** - users should add `nvm use 12.13` to the bottom of your`~/.bashrc` file.

**All** - users should add [npm completion](https://docs.npmjs.com/cli/completion.html) to your `~/bashrc` file (`source <(npm completion)`)


## Git

We're using Git for source control, you should install the tooling you need.

**Linux** - users should have it installed with the Build Tools apt command above already.

**MacOS** - users get an older version of git during the tooling install for Homebrew, you should update it with `brew install git`.  You should see [this answer](https://apple.stackexchange.com/a/93179/49048) to make sure you're using the version installed via homebrew.

**Windows** - users will be getting several tools installed with git, because of this, the instructions are detailed below, please be sure to follow carefully. Start by downloading [Git](https://git-scm.com/downloads) for windows....

* Select Components: check the Windows explorer integration as well as the association options.
* Default Editor: choose the custom option, and in the field enter `notepad.exe` while you may be tempted to have more options integrated, the editor you use really needs to be able to exit cleanly. Notepad is really the friendliest option for this one.
* PATH environment: use Git and optional Unix tools from the Windows Command Prompt. This will give you the least hassle in practical use, there is a warning, and unless you are using those specific tools this is absolutely the most headache free option for most people.
* HTTPS transport: Use the native Windows Secure Channel Library.
* Line Ending Conversions: Checkout as-is, commit Unix-style line endings. While not the default, this will give you the least problems working with others in the future of your projects consistently. If you have files that are specifically binary, you should use a .gitattributes file in your project to define them, and it will work out best this way.
* Terminal Emulator: Use Windows' default console window. This, again, will give you the least headaches most of the time. If you want a different more feature rich terminal viewer, I would suggest looking at Cmder or the new Windows Terminal.

**All** users should configure your username and email address to be used by git.

```bash
git config --global user.name "Your Real Name"
git config --global user.email "you@yourdomain"
```


## kdiff3 (recommended)

I recommend having a merge tool that supports 3-way merging. Kdiff3 is a pretty good option, there are others, but are beyond the scope of this article.

**Linux** - `sudo apt install kdiff3`

**MacOS** - `brew cask install kdiff3`

**Windows** - `choco install kdiff3`

**All** - users will then need to configure git to use kdiff3.

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


## Starship (recommended)

I recommend that you install and configure [Starship](https://starship.rs/) with your bash terminal. It works in most configurable shells and installation options vary.


## Visual Studio Code (recommended)

There are those who love [Visual Studio Code](https://code.visualstudio.com/Download) (VS Code) and few that don't like it. My own opinion is it's a near perfect mix of editor and tools. The git integration is decent, though I tend to just use the command line. The integrated terminal is one of the most useful features I've seen in any text editor or IDE anywhere, ever. It's right with me, and the project I'm working on, which allows me to run whatever commands I need right there.

**Linux** - users should use the official snap version where available. `sudo snap install --classic code`

**MacOS** - users should use the direct download, which includes automatic update functionality.

**Windows** - users should use the direct download, which includes automatic update functionality.

## Docker

**Linux** - users will want to install and configure [Docker Engine - Community Edition](https://docs.docker.com/install/linux/docker-ce/ubuntu/) directly.  After installing, you should follow the [post-installaction steps](https://docs.docker.com/install/linux/linux-postinstall/).

**MacOS** - users can [Download Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac) or use `brew cask install docker`

**Windows** - users can [Download Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows) directly or `choco install docker-desktop --pre`.  *DO NOT* enable windows containers, you want to use Linux containers, which are more broadly supported and what is expected the vast majority of the time.

**MacOS and Windows** - users will need to complete configuration including setting up a dockerhub user account as well.


# Cloning The Project

First we create our directory for cloning the project to. I tend to favor this convention only because it works well and consistently regardless of the repository.

```bash
mkdir -p ~/src/github.org/lets-make-an-app
cd ~/src/github.org/lets-make-an-app
git clone git@github.com:lets-make-an-app/node-react-boilerplate.git
code ~/src/github.org/lets-make-an-app/node-react-boilerplate
```

I have the domain name of the repository server first, this lets me know where the source is, then I have the project/owner and finally the project itself. I will also create a ~/src/local/experiment-name for anything I'm experimenting with.

I will suggest sticking with kebab-case naming for directories and files to save yourself future headaches. What this means is sticking to lower case and using a hyphen as a separator character. You don't have to hit shift at all this way. Also, although you may be working in Windows or MacOS with a case-insensitive file system, most applications are being deployed on Linus, which is case sensitive and will lead to actual production bugs if you aren't careful.


# Initial Structure

Before anything else, I want to make sure that I have the latest in master (the clone will be here, but for future use). As well as create a new branch to work against.

```bash
git pull
git checkout -b 001-application-structure--card-123
git push --set-upstream origin 001-application-structure--card-123
```

In this case there are a couple of numbers you'll see in part of my branch name. The `001` number in my branch name is to Version target, or in this case, the blog article that I am using. If you have specific application version/release targets you should use that numbering here, if you are doing rolling releases, you can skip this part. This is followed by the general description of what is being worked on (Application Structure).

Finally, you'll see two hyphens followed by a reference number… this is taken from the card link on the Project Board, but could just as easily be a reference id for a Github Issue or to a Feature/Story/Task in DevOps. I put this in the name of the branch to make it easier to create a Reference tag in the Source Code Management (SCM) server, in this case Github.

```
git commit -m "Add initial Application Structure items. TAGHERE"
```

The specifics of the scm you are using and it's own tagging features may vary, for the most part a given issue or work item is simple #0000 where 0000 represents the id of the issue or work item.
For this series, my branches will always be ###-title structure to make it easier to see the progress as it's made in the history, which is more important than the project management in this case.


## Blog Entries

The entries themselves will be in markdown format with yaml front matter. I will start by copying the contents of this article an the previous article into new files. After this article, I will start with the markdown version and post on medium as the pull request makes it into master. I am prefixing docs with an underscore so that in my directory view, it's right at the top.

`_blog/###-{TITLE}.md `- will be files tracking this blog as well as any related includes.

```bash
mkdir -p _blog
touch _blog/000-announcement.md
touch _blog/001-application-structure.md
```

## Docs

Most of these will be simply placeholders at this point, but want to outline them.

`README.md` - is the project's main entry document, you should have this, and it should point out the project and lead you to installation and/or tooling required as well as general information and licensing details. You sould also link to your docs directory.

`_docs/index.md `- is the entry point into documentation, creating a placeholder file for now. Optionally, you may want to run an automated process that takes your markdown docs as well as other details and generates a documentation website.

`_docs/environment.md `- will detail the environment variables that the application needs or can optionally use to run. The use of environment variables is part of The Twelve-Factor App, and although not as common for even power users, will help you in developing an application that can be deployed in flexible ways.

```
mkdir -p _docs
touch _docs/index.md
touch _docs/environment.md
```

The commands above will create the files in question, and then let me edit them as needed. You can also use your editor of choice for this.


## Projects

```bash
.../node-react-boilerplate on 001-application-structure 
> npm init
```

The above command will start me down an interview for creating an initial `package.json` file. I won't detail this here, but will state that if you are not creating a public module for publishing to npm (node package manager), then you should immediately open said file and add `"private": true,` to the top.

I then copy this file as follows…

```bash
mkdir config
cp package.json srv/package.json
mkdir srv
cp package.json srv/package.json
mkdir pub
cp package.json srv/package.json
mkdir app
cp package.json srv/package.json
mkdir auth
cp package.json srv/package.json
mkdir scripts
cp package.json srv/package.json
```

The reason that I do this, is that the package.json file has a scripts section, you can use this as a task runner for whatever your workflow is. It also has any dependencies for your application. The file in the root directory is for whole-application build and run scripts. Each directory will have it's own scripts and dependencies that don't all have to get deployed (particularly the applications).


# Working the Task

At this point, I'm now taking a moment to actually review and add my initial docs entries a bit as well as copying the articles from medium…


# Committing and Pull Requests

As you work on a given task, you should make regular commits. You will first need to add any changed files, and from there commit with an appropriate message, which I make note of in the cloning section above.