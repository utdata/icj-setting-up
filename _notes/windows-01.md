# Windows

I am a little less familiar with Windows, especially as it relates to OneDrive, so it's possible we'll run into issues. We'll solve them.

Everything listed here is free.

## Install git

> Windows users have to install Git and Git Bash before doing the [Command-line interface tools lesson](https://github.com/utdata/icj-cli-tools). These next few steps do that.

- Install [Git](https://git-scm.com/downloads), our source code version control program. This will allow us to save our code in steps. This will also install **Git Bash**, which will be your Terminal app.

There is one point in the installation process where you need to set "Use Git from Git Bash only".

![git setup](images/git-setup-windows.png)

- Use the default settings for everything else.
- You should now be able to find **Git Bash** from your Windows Start menu.

> If you were sent here from the Command-line interface tools lesson, it's time to [go back there now](https://github.com/utdata/icj-cli-tools#using-bash-and-a-terminal). You'll be sent back here to finish the rest later.

### Set up your git user and email

Next we'll [set your user.name](https://docs.github.com/en/get-started/getting-started-with-git/setting-your-username-in-git) so Git knows who you are.

1. In your Terminal, do this but use _your_ name instead of Mona Lisa:

```bash
git config --global user.name "Mona Lisa"
```

Now we'll [set your user.email](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/setting-your-commit-email-address#setting-your-commit-email-address-in-git).

1. In your Terminal do this but use your email:

```bash
git config --global user.email "email@example.com"
```

You will want to use the same email when you create your GitHub account.

## Set up GitHub

If you don't already have a GitHub account, go to [github.com/](http://github.com/) and create an account.

> **IMPORTANT:** Choose your username carefully and **don't make the name specific to this class**. This is your personal GitHub profile FOREVER. I would avoid upper case characters as a matter of convention. Your name becomes part of a URL for your projects when we publish them.

### Creating ssh key

We're going to create a special file on your computer so that your machine can connect to your GitHub account. (GitHub doens't like sending your password around). It will seem complicated, but it's not really.

> If you have ever set up SSH keys before, find the instructor. (If that doesn't make sense to you, you likely haven't.)

**Before you do this next step**, know it will ask you to supply a location and password: **Leave it blank and just hit enter in both cases**.

1. In your terminal, run the following command **but with your email**:

    ```bash
    ssh-keygen -t ed25519 -C "your_email@example.com"
    ```

2. When it prompts you about a location, **JUST HIT RETURN** to accept the default.
3. When it prompts you for a passphrase, **JUST HIT RETURN** to leave it blank.

You should get a nice little art looking return on your terminal, eventually.

### Adding key to Github

What those steps did is create a file on your computer and put inside of it a bunch of random characters. We now need to add the contents of those files into the Github web interface, so it can confirm you are you.

1. Once you are through the steps above, do the following command in your terminal:

```bash
clip < ~/.ssh/id_ed25519.pub
```

This copies the contents of that file you created to your clipboard. It's like finding the file, opening it and then copying the contents.

1. Go to [github.com](https://github.com/) and click your user icon and choose **Settings**.
2. In the user settings sidebar on the left, click **SSH and GPG keys**.
3. Click **New SSH key** or **Add SSH key**.
4. In the "Title" field, add a descriptive label for the new key. Name it after your computer, like "Personal MacBook Air" or something.
5. In the "Key" field, do Command-V to paste your key into the box.

It will look something like this:

![key](https://docs.github.com/assets/cb-24835/images/help/settings/ssh-key-paste.png)

Almost done!

1. Click Add SSH key.
2. If prompted, confirm your GitHub password.

### Test

1. From your Terminal, do the following command:

```bash
ssh -T git@github.com
```

- If you are asked about "RSA key fingerprint", type **yes** and hit return.
- In the end, you should have a success message like: "Hi username! You've successfully authenticated, but GitHub does not provide shell access." If you get that message, you are good!

### Alternative to SSH keys

If you can't set SSH keys, you can at least reduce the number of times you have to enter your GitHub name/password by [caching your password](https://help.github.com/articles/caching-your-github-password-in-git/). We'll have to use this method for lab computers.

## Text editor

We will use the code editor Visual Studio Code, made by Microsoft. It is free. We need to install it now.

- Install [Visual Studio Code](https://code.visualstudio.com/docs/setup/windows).
- After installing, we need to configure your VS Code integrated terminal to use Git Bash. Go to View > Command Palette and type in `>Terminal: Select Default Shell` and choose it. When it prompts you with choices, choose **git bash**.
- Open your Command Palette again (Cmd+Shift+p or View > Command Palette) and type in `>shell command` and look for the return **Shell Command: Install 'code' command in PATH. Choose that.

![Add code to path](images/shell-command.png)

- Quit both VS Code and Git Bash for this to take affect.

## Installing bash-git-prompt

We are adding some software to adjust your Terminal prompt to show your git "state" when in a tracked folder.

1. Open a _new_ Terminal window and do the following:

    ```bash
    git clone https://github.com/magicmonty/bash-git-prompt.git .bash-git-prompt --depth=1
    ```

2. Now open (or create) the `.bash_profile` file. (See note below if this doesn't work)

    ```bash
    code .bash_profile
    ```

3. Once your `.bash_profile` opens in VS Code, copy and paste this to the bottom of the file:

    ``` text
    GIT_PROMPT_ONLY_IN_REPO=1
    source ~/.bash-git-prompt/gitprompt.sh
    ```

4. Close and restart your Terminal program to load the new settings.

In addition to adding some commands to help you with git, we also added something to shorten your terminal prompt. We also added a command to stop asking you to change to zsh.

> If you use `code .bash_profile` and it doesn't open the file in VS Code then you didn't set the `code` command in the "Code Editor" section. First quit/relaunch Terminal and try again. If that doesn't work, go back to "[Launching from the command line](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line)" and do that again.

## VS Code extensions

If you look on the left-menu of Visual Studio code, there is a square puzzle looking icon that gives you a list of extensions that you can search for an enable. See the [VS Code docs](https://code.visualstudio.com/docs/editor/extension-gallery) for more info.

1. In VS Code, click on the Extensions icon.
2. In the search box, type in **Live Server** and find the one created by **Ritwick Dey**.
3. Click the Install button on that page.
4. Do the same for **markdownlint** by **David Anson**.
5. Do tne same for **Nunjucks**  by **ronnidc**.

These all make Visual Studio Code more awesomer in different ways.

## VS Code preferences

I have some helpful user preferences for VS Code that you might find useful.

1. Go to the Code > Preferences > Settings.
2. At the top right of the code editor are a series of icons, including this one:

    ![vs-code-setting-as-code](images/vs-code-setting-as-code.png)

3. In the new file that opens, copy and paste the code below and replace what is there.

    ```json
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

4. Save and close the file.

This sets the default text size, line wrapping, tab stops and other useful things we will need.

## Testing Part 1 setup

We need to make sure everything is set correctly before moving on. So here is how to check:

Before doing this, open a new Terminal window:

1. Do `git config user.name` and you should get a response that is your name.
2. Do `git config user.email` and you should get back your email address.
3. Do `ssh -T git@github.com` to test SSH keys. If you are asked about "RSA key fingerprint", say yes. In the end, you should have a success message like: "Hi username! You've successfully authenticated, but GitHub does not provide shell access."
4. Do `ls -a | grep bash` and you should get a list that includes at least ".bash-git-prompt" and ".bash_profile".
5. Do `code ~/.bash_profile` and it should open your bash_profile, which should have (at least):

![git-bash-prompt](images/bash_profile-mac.png)

---

**Next**: If you are in Intro to Coding, next up is learning more about version control using [Git and GitHub](https://github.com/utdata/icj-cli-tools#using-git-and-github).

We'll handle Part 2 of the computer setup later in the semester.
