# Starting up a UT Lab computer

Lab machines could get wiped on Monday mornings, so you might have to reset everything. You definitely will have to for the first time.

## Things to do

### code and git
- git config
- git keychain helper
- add bash prompt
- update/download `.bash_profile`

### nvm and node
- install nvm
- install node
- install npm

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

## git config

`git config --global user.name "Christian McDonald"`
`git config --global user.email christian.mcdonald@utexas.edu`