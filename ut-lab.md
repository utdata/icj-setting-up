# Starting up a UT Lab computer

Lab machines could get wiped on Monday mornings, so you might have to reset everything. You definitely will have to for the first time.

## Things to do

### code and git
- git config
- git keychain helper
- update/download `.bash_profile`

### nvm and node
- install nvm
- install node
- install npm

## Git config

Check to see if your git config is set properly:

```bash
git config user.name
```

If it returns your name, great.If not, do this:

```bash
git config --global user.name "Your Name"
git config --glboal user.email youremail@yourdomain.com
```

Next, set the computer to save your credentials after the first time you enter them.

```bash
git config --global credential.helper osxkeychain
```

## Set up your bash_profile

From your Terminal, in your home directory, download the stock `.bash_profile` I have saved.

```bash
curl https://raw.githubusercontent.com/utdata/setting-up/master/.bash_profile > .bash_profile
```

Close and restart your terminal.


## bash setups

### in applications

```bash
# adds enhanced git prompt if installed
GIT_PROMPT_ONLY_IN_REPO=1
source ~/.bash-git-prompt/gitprompt.sh

# Add Visual Studio Code (code)
export PATH="$PATH://Applications/Visual Studio Code.app/Contents/Resources/app/bin"
```

### on my desktop

```bash
# adds enhanced git prompt if installed
GIT_PROMPT_ONLY_IN_REPO=1
source ~/.bash-git-prompt/gitprompt.sh

# Add Visual Studio Code (code)
export PATH="$PATH://Users/ccm346/Desktop/Visual Studio Code.app/Contents/Resources/app/bin"
```

## git keychain helper

```bash
git config --global credential.helper osxkeychain
# Set git to use the osxkeychain credential helper
```