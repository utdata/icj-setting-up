# Macintosh Part 2: Installing Node.js setup

Hold off on this until we get to this part later in the semester.

## Checking xcode

See if you already have the XCode command-line tools installed.

`xcode-select -p`

You should get a path in return. Something like "/Library/Developer/CommandLineTools". If you don't, you need to install it: `xcode-select --install`. But only if you did NOT get a path in the above command.

~~If you don't have it already, install XCode from the [App store](https://itunes.apple.com/us/app/xcode/id497799835?mt=12). This will take some time to download. (Alternatively, you can run this: `$ xcode-select --install`, but it will still take forever.) Once you’ve installed XCode, Launch it and accept the Terms and Conditions.~~

## Setting up a Node environment

### NVM

* We will use NVM to install Node.js. Again, follow the prompts and you should be fine:

``` bash
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
```

* **Test**: Close and reopen a terminal and do `nvm list` to make sure you don't get an error.

### Node

* Use NVM to install Node:

``` bash
nvm install 8.11.4
```

* **Test**: Do `node --version` to make sure it worked. (It should give you back "v8.11.4", which was the current stable version when this was written.)

### npm

* Now lets update npm:

```bash
npm install -g npm
```

- **Test**: Do `npm -v` and it should return with a version number.

## First Graphics App setup

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
