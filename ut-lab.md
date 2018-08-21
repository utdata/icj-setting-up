# Starting up a UT Lab computer

Lab machines could get wiped on Monday mornings, so you might have to reset everything. You definitely will have to set this up for the first time.

## Bash and git setups

### Git config

Open a new Terminal window and check the git configs:

```bash
git config user.name
```

If it returns your name, great. You can probably stop here.

If not, do this (with your actual name):

```bash
git config --global user.name "Your Name"
```

And then set your email (with your actual email):

```bash
git config --glboal user.email youremail@yourdomain.com
```

Next, set the computer to save your credentials after the first time you enter them.

```bash
git config --global credential.helper osxkeychain
```

### Install bash-git-prompt

From your Terminal, in your home directory, download bash-git-prompt:

```bash
git clone https://github.com/magicmonty/bash-git-prompt.git .bash-git-prompt --depth=1
```

### Download the lab bash_profile

From your Terminal, in your home directory, download the stock `.bash_profile` I have saved.

```bash
curl https://raw.githubusercontent.com/utdata/setting-up/master/.bash_profile-lab > .bash_profile
```

Close and restart your terminal. You should be good for the day (or week).

## Installing Node

When we need it, you will have to install (and possibly re-install) the node ecosystem.

### Install NVM, Node, npm

From your Terminal, in your home directory, install NVM:

```bash
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
```

Close and restart your Terminal window.

Now install the version of Node we wll use:

```bash
nvm install 8.11.4
```

Now install node package manager:

```bash
npm install -g npm
```

Install [Yoeman](http://yeoman.io/):

```bash
npm install -g yo
```

Install [Gulp](https://gulpjs.com/):

```bash
npm install -g gulp
```

Install [yeogurt](https://github.com/larsonjj/generator-yeogurt):

```bash
npm install -g generator-yeogurt
```
