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
    * run `$ brew install bash-git-prompt`
    * run `$ code ~/.bash_profile` and add this to the bottom of the file:

``` bash
if [ -f "$(brew --prefix)/opt/bash-git-prompt/share/gitprompt.sh" ]; then
  __GIT_PROMPT_DIR=$(brew --prefix)/opt/bash-git-prompt/share
  source "$(brew --prefix)/opt/bash-git-prompt/share/gitprompt.sh"
fi
```
    * run `$ code ~/.bashrc`. Add this to the bottom of the file:

``` bash
 # Set config variables first
   GIT_PROMPT_ONLY_IN_REPO=1

   # GIT_PROMPT_FETCH_REMOTE_STATUS=0   # uncomment to avoid fetching remote status
   # GIT_PROMPT_IGNORE_SUBMODULES=1 # uncomment to avoid searching for changed files in submodules

   # GIT_PROMPT_SHOW_UPSTREAM=1 # uncomment to show upstream tracking branch
   # GIT_PROMPT_SHOW_UNTRACKED_FILES=all # can be no, normal or all; determines counting of untracked files

   # GIT_PROMPT_SHOW_CHANGED_FILES_COUNT=0 # uncomment to avoid printing the number of changed files

   # GIT_PROMPT_STATUS_COMMAND=gitstatus_pre-1.7.10.sh # uncomment to support Git older than 1.7.10

   # GIT_PROMPT_START=...    # uncomment for custom prompt start sequence
   # GIT_PROMPT_END=...      # uncomment for custom prompt end sequence

   # as last entry source the gitprompt script
   # GIT_PROMPT_THEME=Custom # use custom theme specified in file GIT_PROMPT_THEME_FILE (default ~/.git-prompt-colors.sh)
   # GIT_PROMPT_THEME_FILE=~/.git-prompt-colors.sh
   # GIT_PROMPT_THEME=Solarized # use theme optimized for solarized color scheme
   source ~/.bash-git-prompt/gitprompt.sh
```
You can use these changes to adjust the git commands that will now show on your command prompt. Close out your command prompt and open a new one.

* Install [miniconda](https://conda.io/miniconda.html). Use the Python 3.6 version. Miniconda is python package manager. You are welcome to install the full [Anaconda](https://conda.io/docs/user-guide/install/index.html), but it takes much more space on your computer.