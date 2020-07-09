# Setting up your Macintosh, Part 1

Everything listed here is free.

In setting up your Mac you will be doing a bunch of steps on blind faith without much explanation, mostly it is downloading software and configuring it. I don't go into a lot of details because these steps are typically only done once.

You'll be using your Terminal, which is a program that allows you to talk to your computer using text. It might be scary at first but you'll soon get used to it as you'll be using it throughout this class (mostly from within Visual Studio Code).

Be sure to read all the directions for a particular section before diving in as there are hints that you'll need as you install and configure.

## Code editor

- Install the code editor [Visual Studio Code](https://code.visualstudio.com/download) on your machine. It's normal kind of application install that shouldn't give you any trouble. There are other good code editors out there ([Atom](https://atom.io/), [Sublime](https://www.sublimetext.com/3)), but I'll use VS Code in class.
- Follow these instructions to add the `code` command [to your path](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line).
- **TEST**: Close your Terminal and restart it. Type `code ./` and see it opens VS Code. Hollar if it doesn't.

## Version control system

- Install [Git](https://git-scm.com/downloads), our source code version control program. This will allow us to save our code in steps. Don't install the Git GUI clients. There isn't an "app" for Git, it just lives inside your computer.
- Follow these step to [Set your user.name](https://help.github.com/en/github/using-git/setting-your-username-in-git#setting-your-git-username-for-every-repository-on-your-computer) for _every repository_ in Git. You only need to do the first part "for _every_ repository".
- [Set your commit user.email](https://help.github.com/en/github/setting-up-and-managing-your-github-user-account/setting-your-commit-email-address#setting-your-commit-email-address-in-git).
- **TEST**: In your Terminal, do `git config user.name` and you should get a response that is your name.
- **TEST**: Do `git config user.email` and you should get back your email address.

## Set up Github

If you don't already have a Github account, go to [github.com/](http://github.com/) and create an account.

- Choose your username carefully and don't make the name specific to this class. This is your personal Github profile FOREVER. I would avoid upper case characters as a matter of convention. Your name becomes part of a URL for your projects when we publish them.

### Saving your Github credentials

There are a couple of ways you can tell your computer to save your Github username/password. If you are using your own machine, I suggest this first one, setting up SSH keys. This creates a file on your computer with a secret key that only you have. It looks complicated, but it isn't too bad and you only have to do it once for your machine. **Do read my tips carefully, though.**

- If you have ever set up SSH keys before, find the instructor. (If that doesn't make sense, you haven't.)
  - [Start here](https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).
    - During this process, you'll be asked to save the location of the rsa_id. **Just hit return to save the default location**.
    - You'll be asked to set a password for the file. **JUST LEAVE THE PASSWORD BLANK** and hit return. It may ask you a couple of times.
  - Stop after the 4th step about passphrases (which you leave blank!)

### Add the SSH key to Github

- Follow [these directions](https://help.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account) to add your key to Github.
- TEST: From your Terminal, do `ssh -T git@github.com` to test the SSH keys. If you are asked about "RSA key fingerprint", say yes. In the end, you should have a success message like: "Hi username! You've successfully authenticated, but GitHub does not provide shell access."

### Alternative to SSH keys

If there is some reason you can't set up SSH, you can reduce the number of times you have to enter your Github name/password by [caching your password](https://help.github.com/articles/caching-your-github-password-in-git/). If you use a lab computer, you'll have to use this method.

SSH keys don't work on the UT Guest wifi. If you are unable to use the official "utexas" wifi, then you will have to use this alternative.

## Updating the bash_profile

We are adding some software to adjust your Terminal prompt to show your git "state" when in a tracked folder.

- Open a new Terminal window and do the following, one line at at time:

```bash
$ git clone https://github.com/magicmonty/bash-git-prompt.git .bash-git-prompt --depth=1
$ code .bash_profile
```

This should install the software you need to your home directory, then open (or create) the `.bash_profile` file. (If it doesn't open the file in VS Code then you didn't set the `code` command in the first section. Go back and do that and try again.)

- Copy and paste this to the bottom of the file `.bash_profile` file:

``` bash
# initiates the git bash prompt
GIT_PROMPT_ONLY_IN_REPO=1
source ~/.bash-git-prompt/gitprompt.sh

# sets shorter prompt name
PS1='\u:\W\$ '
```

- Close and restart your terminal to take the new settings.

In addition to adding some commands to help you with git, we also added something to shorten your terminal prompt.

[More on git-bash-prompt if we need it](https://github.com/magicmonty/bash-git-prompt).

## VS Code extensions

If you look on the left-menu, there is a square looking icon that gives you a list of extensions that you can search for an enable. See the [VS Code docs](https://code.visualstudio.com/docs/editor/extension-gallery) for more info.

- In VS Code, click on the Extensions icon.
- In the search box, type in `Nunjucks template`. Click on the return for Nunjucks Template.
- Click the Install button.

We'll need this toward the end of the semester.

- Now search for **markdownlint** and install it in the same way.

This one tells you when your Markdown syntax is incorrect.

## VS Code preferences

I have some helpful user preferences for VS Code that you might find useful.

- Go to the Code > Preferences > Settings.
- At the top right of the code editor are a series of icons, including this one:

![vs-code-setting-as-code](images/vs-code-setting-as-code.png)

- In the new file that opens, copy and paste the code below and replace what is there.

```js
{
    "editor.fontSize": 14,
    "terminal.integrated.fontSize": 12,
    "editor.renderWhitespace": "boundary",
    "editor.tabSize": 2,
    "[md]": {
        "editor.insertSpaces": true,
        "editor.tabSize": 2,
    },
    "editor.renderControlCharacters": true,
    "highlight-matching-tag.style": {
        "backgroundColor": "rgba(63, 191, 63, 0.20)"
    },
    "editor.wordWrap": "on",
    "window.zoomLevel": 0,
    "editor.minimap.enabled": false,
    "files.associations": {
        "*.html": "html"
    },
    "emmet.includeLanguages": {
        "njk": "html",
        "nunjucks": "html"
    },
}
```

- Save and close the file.

This sets the default text size, line wrapping, tab stops and other useful things we will need.

## Testing Part 1 setup

We need to make sure everything is set correctly before moving on. So here is how to check:

Before doing this, open a new Terminal window:

- Do `git config user.name` and you should get a response that is your name.
- Do `git config user.email` and you should get back your email address.
- Do `ssh -T git@github.com` to test SSH keys. If you are asked about "RSA key fingerprint", say yes. In the end, you should have a success message like: "Hi username! You've successfully authenticated, but GitHub does not provide shell access."
- Do `ls -a | grep bash` and you should get a list that includes at least ".bash-git-prompt" and ".bash_profile".
- Do `code ~/.bash_profile` and it should open your bash_profile, which should have (at least):

![git-bash-prompt](images/bash_profile-example.png)
