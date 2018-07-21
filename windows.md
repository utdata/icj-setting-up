# Windows

I'll be honest ... It's likely we'll have extra stumbling blocks with course material using Windows. I'm less familiar with it, and haven't had a chance yet to explore and tailor the course for Windows users. It is NOT impossible ... plenty of folks do development on Windows, and it is getting easier every day. Just be prepared to troubleshoot many of your own problems.

Everything listed here is free unless otherwise noted.

## Text editor

* Install [VS Code](https://code.visualstudio.com/docs/setup/windows). The installation process should add it to your `%PATH%`.

## Version control system

* Install [Git](https://git-scm.com/downloads), our source code version control program. This will allow us to save our code in steps.
* Since you are using Windows, install [Github Desktop](https://desktop.github.com/). This will get you the Git Bash shell, which understands Linux-like commands like the Mac Terminal program.

## Node.js

 Node is a Javascript runtime environment we will use to build news applications. This is where things get really dicey with my Windows experience.

* Install Node.js [using the installer](https://nodejs.org/en/download/), or with [Chocolatey](https://nodejs.org/en/download/package-manager/#windows).
* We _might_ use [yarn](https://yarnpkg.com/lang/en/docs/install/#windows-stable).

## Python 3

* Install [miniconda](https://conda.io/miniconda.html). Use the Python 3.6 version. Miniconda is python package manager. You are welcome to install the full [Anaconda](https://conda.io/docs/user-guide/install/index.html), but it takes much more space on your computer.

## Notes to self on VCS on Windows

* I need to explore how the Terminal in VS Code works. Does it understand unix commands?
* I'd like to find something equivalent to git-bash-prompt, but those features may already be baked into Git Bash.
* We might consider [Chocolatey](https://chocolatey.org/) package manager.
