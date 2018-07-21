# Setting up  your Macintosh

Everything listed here is free unless otherwise noted.

## Code editor

* Install the code editor [Visual Studio Code](https://code.visualstudio.com/download). There are other good ones ([Atom](https://atom.io/), [Sublime](https://www.sublimetext.com/3)), but this is the code editor I will use in class.
* Add the `code` command [to your path](https://code.visualstudio.com/docs/setup/mac).

## Version control system

* Install [Git](https://git-scm.com/downloads), our source code version control program. This will allow us to save our code in steps. Don't worry about the Git GUI clients.
* [Set your username](https://help.github.com/articles/setting-your-username-in-git/) in git.
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

Close and restart your terminal to take the new settings.

## Set up Github

* If you don't already have a github account, go to [github.com](github.com) and create an account.
* [Set up authentication](https://help.github.com/articles/caching-your-github-password-in-git/), so you don't have to type in your password all the time.

## Setting up a Node environment

* If you don't have it already, install XCode from the [App store](https://itunes.apple.com/us/app/xcode/id497799835?mt=12). (Alternatively, you can run this: `$ xcode-select --install`.) Once you’ve installed XCode, Launch it and accept the Terms and Conditions.
* Install Node.js, but DO NOT install from the Node.js site. Node is a Javascript runtime environment we will use to build news applications.
  * To install, we'll use NVM. Follow [this post](https://yoember.com/nodejs/the-best-way-to-install-node-js/) and install the version `8.11.3`.
  * (Note to self: Rewrite this in this repo.) [This post is similar](https://medium.com/@itsromiljain/the-best-way-to-install-node-js-npm-and-yarn-on-mac-osx-4d8a8544987a).
* Install [yarn](https://yarnpkg.com/en/docs/install#mac-stable). Note the one that says "Node is already installed".
* Maybe install [gulp](https://gulpjs.com/). `sudo npm install gulp-cli -g`. Put in computer password.

### Uninstalling node

If you installed Node.js from the website, it will suck and you'll probably need to uninstall it and try again using NVM. This [post was very helpful](http://stackabuse.com/how-to-uninstall-node-js-from-mac-osx/). Especially `which node`.

## If we get into Python

* Install [miniconda](https://conda.io/miniconda.html). Use the Python 3.6 version. Miniconda is python package manager. You are welcome to install the full [Anaconda](https://conda.io/docs/user-guide/install/index.html), but it takes much more space on your computer.
