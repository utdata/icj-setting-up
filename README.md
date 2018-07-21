# Setting up your computer for development

I really recommend that you use your own computer in my classes, especially if you own a Macintosh. Windows users will have more of a challenge, especially since this is the first year of this revamped class, but we'll work through issues.

This repo is intended to help students of my classes set up their computers for my class Intro to Coding for Journalists (and maybe Reporting with Data.)

I will concentrate on Macs first, as that is what is on our lab. If you are using a lab computer, most (but not all) of this will be done already.

## Macintosh

### Install a code editor

* Install the code editor [Visual Studio Code](https://code.visualstudio.com/download). This is the code editor I will use in class.
* Add the `code` command [to your path](https://code.visualstudio.com/docs/setup/mac).

### Installing version control

* Install [Git](https://git-scm.com/downloads), our source control program. This will allow us to save our code in steps. Don't worry about the Git GUI clients. (Unless you insist on using Windows, in which case you should install [Github Desktop](https://desktop.github.com/). We'll want the git shell from that install. I really hope you'll use a Mac.)
* Install [homebrew](https://brew.sh/). This is a package manager for Macs, to get all the cool stuff Mac doesn't do out of the box.
* Install the `git-bash-prompt` [as described here](https://github.com/magicmonty/bash-git-prompt) by:
    * run `$ brew install bash-git-prompt`
    * run `$ code ~/.bash_profile` and add this to the bottom of the file:

``` bash
if [ -f "$(brew --prefix)/opt/bash-git-prompt/share/gitprompt.sh" ]; then
  __GIT_PROMPT_DIR=$(brew --prefix)/opt/bash-git-prompt/share
  source "$(brew --prefix)/opt/bash-git-prompt/share/gitprompt.sh"
fi
```

Close your terminal and start a new one.

### Setting up a Node environment 

Don't worry about this part until later in the class.

* If you don't have it already, install XCode from the [App store](https://itunes.apple.com/us/app/xcode/id497799835?mt=12). (Alternatively, you can run this: `$ xcode-select --install`.) Once you’ve installed XCode, Launch it and accept the Terms and Conditions.
* Install Node.js, but DO NOT install from the Node.js site. Node is a Javascript runtime environment we will use to build news applications.
    * To install, we'll use NVM. Follow [this post](https://yoember.com/nodejs/the-best-way-to-install-node-js/) and install the version `8.11.3`.
    * (Note to self: Rewrite this in this repo.) [This post is similar](https://medium.com/@itsromiljain/the-best-way-to-install-node-js-npm-and-yarn-on-mac-osx-4d8a8544987a).
* Install [yarn](https://yarnpkg.com/en/docs/install#mac-stable). Note the one that says "Node is already installed".
* Maybe install [gulp](https://gulpjs.com/). `sudo npm install gulp-cli -g`. Put in computer password.

#### Uninstalling node

If you installed Node.js from the website, it will suck and you'll probably need to uninstall it and try again using NVM. This [post was very helpful](http://stackabuse.com/how-to-uninstall-node-js-from-mac-osx/). Especially `which node`.

### If we get into Python

* Install [miniconda](https://conda.io/miniconda.html). Use the Python 3.6 version. Miniconda is python package manager. You are welcome to install the full [Anaconda](https://conda.io/docs/user-guide/install/index.html), but it takes much more space on your computer.

## Windows

I'll be honest ... It's likely we'll have extra stumbling blocks with course material using Windows. I'm less familiar with it, and haven't had a chance yet to find the tailorings necessary for Windows users. It is NOT impossible ... plenty of folks do development on Windows, and it is getting easier every day. But be prepared to do some troubleshooting.

### Install text editor

* Install [VS Code](https://code.visualstudio.com/docs/setup/windows). The installation process should add it to your `%PATH%`.

### Code version control software

* Install [Git](https://git-scm.com/downloads), our source version control program. This will allow us to save our code in steps.
* Since you are using Window, install [Github Desktop](https://desktop.github.com/). This will get you the Git Bash shell, which will work more like the Mac Terminal program.

#### Notes on VCS on Windows

* I need to explore ow the Terminal in VS Code works. Does it understand unix commands?
* I'd like to find something equivalent to git-bash-prompt, but it may already be baked into Git Bash.
* We might consider [Chocolatey](https://chocolatey.org/) package manager.

### Install Node.js

This is where things get really dicey with my Windows experience.

* Install Node.js [using the installer](https://nodejs.org/en/download/), or with [Chocolatey](https://nodejs.org/en/download/package-manager/#windows).
* We _might_ use [yarn](https://yarnpkg.com/lang/en/docs/install/#windows-stable).
