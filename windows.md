# Windows

I'll be honest ... It's likely we'll have extra stumbling blocks with course material using Windows. I'm less familiar with it, and haven't had a chance yet to explore and tailor the course for Windows users. It is NOT impossible ... plenty of folks do development on Windows, and it is getting easier every day. Just be prepared to troubleshoot many of your own problems.

Everything listed here is free unless otherwise noted.

## Text editor

* Install [VS Code](https://code.visualstudio.com/docs/setup/windows). The installation process should add it to your `%PATH%`.

## Version control system

* Install [Git for Windows](https://gitforwindows.org/), our source code version control program. This will allow us to save our code in steps.
* I THINK I DON'T NEED THIS ANYMORE IF USING GITFORWINDOWS: Since you are using Windows, install [Github Desktop](https://desktop.github.com/). This will get you the Git Bash shell, which understands Linux-like commands like the Mac Terminal program.
* After setting up Git Bash, you [configure your VS Code integrated terminal](https://code.visualstudio.com/docs/editor/integrated-terminal#_windows). I _think_ the easiest way is to go to View > Command Pallete and type in `Select Default Shell` and find it, but I haven't tried it.
* [Set your username](https://help.github.com/articles/setting-your-username-in-git/) in git.

## Github

If you don't already have a github account, set one up.

* Go to [github.com](github.com) and create an account.
* [Set up authentication](https://help.github.com/articles/caching-your-github-password-in-git/), so you don't have to type in your password all the time.

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
