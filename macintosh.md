# Setting up  your Macintosh

Everything listed here is free unless otherwise noted.

## At the beginning of the semester

### Code editor

* Install the code editor [Visual Studio Code](https://code.visualstudio.com/download). There are other good ones ([Atom](https://atom.io/), [Sublime](https://www.sublimetext.com/3)), but I'll use VS Code in class.
* Add the `code` command [to your path](https://code.visualstudio.com/docs/setup/mac).

### Version control system

* Install [Git](https://git-scm.com/downloads), our source code version control program. This will allow us to save our code in steps. Don't worry about the Git GUI clients.
* [Set your username](https://help.github.com/articles/setting-your-username-in-git/) in Git.
* ~~Install [homebrew](https://brew.sh/). This is a package manager for Macs, to get all the cool stuff Mac doesn't do out of the box. (We're gonna avoid this if we can.)~~
* Install the `git-bash-prompt` by following the directions below. :
  1. `cd ~`
  2. `git clone https://github.com/magicmonty/bash-git-prompt.git .bash-git-prompt --depth=1  `
  3. `code ~/.bash_profile` and add this to the bottom of the file:

``` text
GIT_PROMPT_ONLY_IN_REPO=1
source ~/.bash-git-prompt/gitprompt.sh
```

Close and restart your terminal to take the new settings. [More on git-bash-prompt if we need it.](https://github.com/magicmonty/bash-git-prompt)


### Set up Github

If you don't already have a Github account, go to [github.com/](http://github.com/) and create an account. Two important things to note:

* Choose your username carefully. I wouldn't use upper case characters or special characters because this will become part of a URL later.
* USE YOUR UNIVERSITY EMAIL IF YOU HAVE ONE. You might want to apply for the [Student developer pack](https://help.github.com/articles/applying-for-a-student-developer-pack/), which will get you private repositories.
* I recommend you [set up SSH keys](https://help.github.com/articles/connecting-to-github-with-ssh/) for your computer so you don't have to type in your password all the time. It is not as scary as it looks, though there is some command-line foo to execute. (I'm not sure how this will work on lab computers. We might try [osxkeychain helper](https://help.github.com/articles/caching-your-github-password-in-git/).)

## Parts for later in the class

We won't do this until later in the semester.

### Setting up a Node environment

* If you don't have it already, install XCode from the [App store](https://itunes.apple.com/us/app/xcode/id497799835?mt=12). This will take some time to download. (Alternatively, you can run this: `$ xcode-select --install`, but it will still take forever.) Once you’ve installed XCode, Launch it and accept the Terms and Conditions.
* Install Node.js, but __DO NOT__ install from the Node.js site. Node is a Javascript runtime environment we will use to build news applications.
  * To install, we'll use NVM. Follow [this post](https://yoember.com/nodejs/the-best-way-to-install-node-js/) and install the version `8.11.3`.
  * (Note to self: Rewrite this in this repo.) [This post is similar](https://medium.com/@itsromiljain/the-best-way-to-install-node-js-npm-and-yarn-on-mac-osx-4d8a8544987a).
* ~~Install [yarn](https://yarnpkg.com/en/docs/install#mac-stable). Note the one that says "Node is already installed".~~
* ~~Maybe install [gulp](https://gulpjs.com/). `sudo npm install gulp-cli -g`. Put in computer password.~~

#### Uninstalling node

If you installed Node.js from the website, it will suck and you'll probably need to uninstall it and try again using NVM. This [post was very helpful](http://stackabuse.com/how-to-uninstall-node-js-from-mac-osx/). Especially `which node`.

### If we get into Python

* Install [miniconda](https://conda.io/miniconda.html). Use the Python 3.6 version. Miniconda is python package manager. You are welcome to install the full [Anaconda](https://conda.io/docs/user-guide/install/index.html), but it takes more space on your computer.
