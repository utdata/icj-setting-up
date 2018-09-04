# Windows

I'll be honest ... We may have extra stumbling blocks with course material using Windows. I'm less familiar with it, and haven't had a chance yet to explore and tailor the course for Windows users. It is NOT impossible ... plenty of folks do development on Windows, and it is getting easier every day. Just be prepared to troubleshoot many of your own problems.

Everything listed here is free unless otherwise noted.

## At the beginning of the semester

### Text editor

* Install [VS Code](https://code.visualstudio.com/docs/setup/windows). The installation process should add it to your `%PATH%`.
* (There are other good code editors like [Atom](https://atom.io/) and [Sublime](https://www.sublimetext.com/3), but I'll use VS Code in class.)

### Version control system

* Install [Git](https://git-scm.com/download/win), our source code version control program. This will allow us to save our code in steps. This will also install Git Bash, which will be your terminal app.
* Configure your [Git profile](https://help.github.com/articles/setting-your-username-in-git/#platform-windows) so you don't have to type you password all the time.
* After setting up Git Bash, you [configure your VS Code integrated terminal](https://code.visualstudio.com/docs/editor/integrated-terminal#_windows). I _think_ the easiest way is to go to View > Command Pallete and type in `Select Default Shell` and find it, but I haven't tried it.

### Set up Github

If you don't already have a Github account, go to [github.com/](http://github.com/) and create an account. Two important things to note:

* Choose your username carefully. Don't use upper case characters or special characters because this will become part of a URL later. Don't make the name specific to this class. This is your personal Github profile FOREVER.
* USE YOUR UNIVERSITY EMAIL IF YOU HAVE ONE. You might want to apply for the [Student developer pack](https://help.github.com/articles/applying-for-a-student-developer-pack/), which will get you private repositories.

### Saving your Github credentials

There are ways you can tell your computers to save your Github username/password. If you are using your own machine, I suggest this first one, setting up SSH keys. If that proves difficult, try the second option.

* I use these directions to create [SSH keys](https://help.github.com/articles/connecting-to-github-with-ssh/) on my machine so I'm never asked for a password. It is not as scary as it looks, though there is some command-line foo to execute.
* Or, you can at least reduce the number of times you have to enter your Github name/password by [caching your password](https://help.github.com/articles/caching-your-github-password-in-git/). We'll have to use this method for lab computers.

## For later in the semester

We don't do this until later, when we start using Node-based tools.

### Node.js

 Node is a Javascript runtime environment we will use to build news applications. This is where things get really dicey with my Windows experience.

* Install Node.js [using the installer](https://nodejs.org/en/download/), or with [Chocolatey](https://nodejs.org/en/download/package-manager/#windows). MAYBE, just maybe, it's better to use [NVM for Window](https://danielarancibia.wordpress.com/2017/03/28/install-or-upgrade-nodejs-with-nvm-for-windows/), but I don't know for sure.
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

### Python 3

* Install [miniconda](https://conda.io/miniconda.html). Use the Python 3.6 version. Miniconda is python package manager. You are welcome to install the full [Anaconda](https://conda.io/docs/user-guide/install/index.html), but it takes much more space on your computer.
