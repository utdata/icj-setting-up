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
git config --global user.email youremail@yourdomain.com
```

Next, set the computer to save your credentials after the first time you enter them.

```bash
git config --global credential.helper osxkeychain
```

Be prepared to enter your github username and password.

### Install bash-git-prompt

When you launch Terminal, it should put you in your home directory. If not, do `cd ~`.

- Do the following command to download bash-git-prompt:

```bash
git clone https://github.com/magicmonty/bash-git-prompt.git .bash-git-prompt --depth=1
```

## Installing node

- First, check if Node is already installed:

```bash
node -v
```

If Node is already installed, you should get back a version number, like "v8.11.4". If it does, you can probably stop here.

### Install NVM, Node, npm

If you didn't get a version number above, you need to install stuff.

- From your Terminal, in your home directory, install NVM:

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```

- Close and restart your Terminal window.
- Now install the version of Node we wll use:

```bash
nvm install v16.13.0
```

- Now install node package manager:

```bash
npm install -g npm
```

- Install [Gulp](https://gulpjs.com/) and [Degit](https://www.npmjs.com/package/degit):

```bash
npm install -g gulp degit
```

## Google Drive authentication

When using the icj-project-template we use a secret key file to authenticate to Google Drive.

- If you haven't already, follow the directions in [macintosh-02.md](macintosh-02.md) for **Creating a service account key**.
  - If you have created the file already but don't have a copy of the file saved, you can go to [Google Cloud Platform > APIs & Services > Credentials](https://console.cloud.google.com/apis/credentials), edit your existing key and click **Create key** to download the file.
- Rename the downloaded file as `google_drive_fetch_token.json` and save it in a safe place where you can pull it onto a lab computer each time you set up.
- Move a copy of the file to the Desktop of your lab computer.

Now that you have created the file and save it somewhere, you only need to download it to your Desktop in the future.

### Download .bash_profile for lab computers

I have a copy of a `.bash_profile` file that you can download onto your computer with the following command.

```bash
curl https://raw.githubusercontent.com/utdata/setting-up/main/.bash_profile-lab > .bash_profile
```

Close and restart your Terminal. You should be good for the day (or week).

### Visual Studio Code preferences

You might also consider getting the VS Code preferences I have here: [VS code goodies](vscode-goodies.md).
