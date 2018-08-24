# Setting up  your Macintosh

Everything listed here is free unless otherwise noted.

## At the beginning of the semester

### Code editor

* Install the code editor [Visual Studio Code](https://code.visualstudio.com/download). There are other good ones ([Atom](https://atom.io/), [Sublime](https://www.sublimetext.com/3)), but I'll use VS Code in class.
* Add the `code` command [to your path](https://code.visualstudio.com/docs/setup/mac).

### Version control system

* Install [Git](https://git-scm.com/downloads), our source code version control program. This will allow us to save our code in steps. Don't worry about the Git GUI clients.
* [Set your username](https://help.github.com/articles/setting-your-username-in-git/) in Git.
* Open a new Terminal window to install the `git-bash-prompt` and do the following:

```bash
git clone https://github.com/magicmonty/bash-git-prompt.git .bash-git-prompt --depth=1
```

* If you were able to set the `code` command above, you should be able to do `code ./` to open VS Code in a new window from your home directory. If that doesn't work, then from VS Code, start a New Window, the Open your home folder on your Mac.
* Look for a file called `.bash_profile`, which might not exist yet. If you have one, open it. If you don't, then use VS Code to create a new file there and call it ".bash_profile". The preceding dot is important.
* Add this to the bottom of the file `.bash_profile` file:

``` text
GIT_PROMPT_ONLY_IN_REPO=1
source ~/.bash-git-prompt/gitprompt.sh
```

Close and restart your terminal to take the new settings. [More on git-bash-prompt if we need it](https://github.com/magicmonty/bash-git-prompt).

### Set up Github

If you don't already have a Github account, go to [github.com/](http://github.com/) and create an account. Two important things to note:

* Choose your username carefully. I wouldn't use upper case characters or special characters because this will become part of a URL later.
* USE YOUR UNIVERSITY EMAIL IF YOU HAVE ONE. You might want to apply for the [Student developer pack](https://help.github.com/articles/applying-for-a-student-developer-pack/), which will get you private repositories.

### Saving your Github credentials

There are ways you can tell your computers to save your Github username/password. If you are using your own machine, I suggest this first one, setting up SSH keys. If that proves difficult, try the second option. 

* You can reduce the number of times you have to enter your Github name/password by [caching your password](https://help.github.com/articles/caching-your-github-password-in-git/). We'll have to use this method for lab computers.
* But, I use these directions for [SSH keys](https://help.github.com/articles/connecting-to-github-with-ssh/) on my machine so I'm never asked for a password. It is not as scary as it looks, though there is some command-line foo to execute.

## Parts for later in the class: Node.js setup

We won't do this until later in the semester.

### Setting up a Node environment

* If you don't have it already, install XCode from the [App store](https://itunes.apple.com/us/app/xcode/id497799835?mt=12). This will take some time to download. (Alternatively, you can run this: `$ xcode-select --install`, but it will still take forever.) Once you’ve installed XCode, Launch it and accept the Terms and Conditions.
* We will use NVM to install Node.js. Again, follow the prompts and you should be fine:

``` bash
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
```

* Close and reopen a terminal and do `nvm list` to make sure you don't get an error.
* Install node:

``` bash
nvm install 8.11.4
```

* Do `node --version` to make sure it worked. (v8.11.4 was the current stable version when this was written.)
* Now lets update npm:

```bash
npm install -g npm
```

### First Graphics App setup

There are some additional global npm tools that we need to install for our tour of NodeJS-based build tools. Do each of these, one line at a time.

```bash
npm install -g yo
npm install -g gulp
npm install -g generator-yeogurt
npm install -g grunt
```

These are for [Yoeman](http://yeoman.io/), [Gulp](https://gulpjs.com/), [Yeogurt](https://github.com/larsonjj/generator-yeogurt) and [Grunt](https://gruntjs.com/).

### Resources for Uninstalling node

I used this [yoember](https://yoember.com/nodejs/the-best-way-to-install-node-js/) and this [medium post]((https://medium.com/@itsromiljain/the-best-way-to-install-node-js-npm-and-yarn-on-mac-osx-4d8a8544987a)) to come up with the script above.

If you installed Node.js from the website, it will suck and you'll probably need to uninstall it and try again using NVM. This [post was very helpful](http://stackabuse.com/how-to-uninstall-node-js-from-mac-osx/). Especially `which node`.

## If we get into Python

* Install [miniconda](https://conda.io/miniconda.html). Use the Python 3.6 version. Miniconda is python package manager. You are welcome to install the full [Anaconda](https://conda.io/docs/user-guide/install/index.html), but it takes more space on your computer.
