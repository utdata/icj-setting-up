
# Setting up for Node

We don't do this until later in the semester, when we start using Node-based tools.

## Node.js

Node is a Javascript runtime environment we will use to build news applications. This is where things get really dicey with my Windows experience.

* Install Node.js [using the installer](https://nodejs.org/en/download/)
* Do `node --version` to make sure it worked. (v8.11.4 was the current stable version when this was written.)
* Now lets update npm:

```bash
npm install -g npm
```

## ICJ template setup

There are some additional global npm tools that we need to install for our tour of NodeJS-based build tools. Do each of these, one line at a time.

```bash
npm install -g gulp
npm install -g degit
```

These are for the task manager [Gulp](https://gulpjs.com/) and a scaffolding tool [Degit](https://www.npmjs.com/package/degit).

## Alternate installing of Node

> Don't do this unless specifically asked.

* An alternate method to install Node might be to use [NVM for Window](https://danielarancibia.wordpress.com/2017/03/28/install-or-upgrade-nodejs-with-nvm-for-windows/), but I don't know for sure.
* Yet Another option is to use the Windows package manager [Chocolatey](https://nodejs.org/en/download/package-manager/#windows).)

## Python 3

> Don't do this unless specifically asked.

If we get into Python scripting, use Miniconda.

* Install [miniconda](https://conda.io/miniconda.html). Use the Python 3.6 version. Miniconda is python package manager. You are welcome to install the full [Anaconda](https://conda.io/docs/user-guide/install/index.html), but it takes much more space on your computer.
