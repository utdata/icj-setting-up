# Starting up a UT Lab computer

Lab machines could get wiped on Monday mornings, so you might have to reset everything. You definitely will have to set this up for the first time.

## Test git setups

**Test if it is setup**: Open a new Terminal window and check the git configs:

```bash
git config user.name
```

If it returns your name, great. You can probably stop here.

### If you didn't get your name in the test

If git is not set for you, you need to set it.

- Set your user.name:

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

Be prepared to enter your github username and password.

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

## Checking if Node is installed

- Check the Node version

```bash
node -v
```

Should give you back a version number, like "v8.11.4". If it does, you can probably stop here.

### Install NVM, Node, npm

If you didn't get a version number above, you need to install stuff.

- From your Terminal, in your home directory, install NVM:

```bash
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
```

- Close and restart your Terminal window.
- Now install the version of Node we wll use:

```bash
nvm install 8.11.4
```

- Now install node package manager:

```bash
npm install -g npm
```

- Install [Gulp](https://gulpjs.com/) and [Degit](https://www.npmjs.com/package/degit):

```bash
npm install -g gulp degit
```
