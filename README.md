Setting up your computer for development
========================================

This repo is intended to help students of my classes set up their computers for my class Intro to Coding for Journalists (and maybe Reporting with Data.)

I will concentrate on Macs first, as that is what is on our lab. As I set up this class for the first time, I _really_ recommend using a Mac. Hopefully, I'll work out Windows versions, too.

## Macintosh

* Install the code editor [Visual Studio Code](https://code.visualstudio.com/download). This is the code editor I will use in class.
* Add the `code` command [to your path](https://code.visualstudio.com/docs/setup/mac).
* Install [Node.js](https://nodejs.org/en/download/). Node is a Javascript runtime environment we will use to build news applications.
* Install [homebrew](https://brew.sh/). This is a package manager for Macs.
* Install [yarn](https://yarnpkg.com/en/docs/install#mac-stable). Note the one that says "Node is already installed".
* Install the `git-bash-prompt` [as described here](https://github.com/magicmonty/bash-git-prompt) by:
    * run `brew install bash-git-prompt`
    * run `$code ~/.bash_profile` and add this to the bottom of the file:

``` bash
if [ -f "$(brew --prefix)/opt/bash-git-prompt/share/gitprompt.sh" ]; then
  __GIT_PROMPT_DIR=$(brew --prefix)/opt/bash-git-prompt/share
  source "$(brew --prefix)/opt/bash-git-prompt/share/gitprompt.sh"
fi
```

* Install [miniconda](https://conda.io/miniconda.html). Use the Python 3.6 version. Miniconda is python package manager. You are welcome to install the full [Anaconda](https://conda.io/docs/user-guide/install/index.html), but it takes much more space on your computer.