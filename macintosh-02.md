# Macintosh Part 2: Installing Node.js setup
Hold off on this until we get to this part later in the semester.

If we have reached that point, then fire up your Terminal.

## Checking xcode
See if you already have the XCode command-line tools installed.

1. Run this in your Terminal:

```bash
xcode-select -p
```

You should get a path in return. Something like "/Library/Developer/CommandLineTools".

If you don't **AND ONLY IF YOU DON'T**, you need to install it.

### Installing xcode-select (only if needed)
1. In your Terminal run this:

``` bash
xcode-select --install
```

2. A software update popup window will appear that asks: "The xcode-select command requires the command line developer tools. Would you like to install the tools now?" choose to confirm this by clicking **Install**, then agree to the Terms of Service when requested (feel free to read them thoroughly, we’ll be here).

It can take a long while to download and install. If you get an error on this install, let me know as I have a copy I can give you.

These [xcode-select install directions came from  here](https://osxdaily.com/2014/02/12/install-command-line-tools-mac-os-x/)

## Setting up a Node environment

### NVM
We will use NVM to install Node.js. Again, follow the prompts and you should be fine.

1. Go to [this page](https://github.com/nvm-sh/nvm#install--update-script) and copy the first code chunk that starts with `curl`.
2. Paste that into your Terminal and run it.
3. After it is done, quit Terminal and relaunch it.

- **Test**: _After relaunching a terminal_ do `nvm list` to make sure you don't get an error.

### Node
Use NVM to install Node.

1. Install `v16.18.0` of Node via the next two commands:

```bash
name@computer icj-project-rig % nvm install 16.18.0
...
name@computer icj-project-rig % nvm use 16.18.0    
Now using node v16.18.0 (npm v8.19.2)
```

2. **Test**: Do `node -v` to make sure it worked. It should give you back "v16.18.0".

```bash
name@computer icj-project-rig % node -v 
v16.18.0
```

### npm

1. To update npm, run this:

```bash
npm install -g npm
```

2. **Test**: Do `npm -v` and it should return with a version number.

## ICJ project setup

There are some additional global npm tools that we need to install for our tour of NodeJS-based build tools.

1. Run this:

```bash
npm install -g gulp degit
```

These are for the task manager [Gulp](https://gulpjs.com/) and a scaffolding tool [Degit](https://www.npmjs.com/package/degit).

## Google Drive authentication

There is a point in class when your computer will need access to your Google Drive account. Much like ssh keys, we'll need specific credentials that work only for you. We will use the Google Cloud Project's command line interface tool to do this.
Otherwise known as the [`gcloud` CLI](https://cloud.google.com/sdk/gcloud).

### Steps to save our Google credentials and access our project
1. To make the installation of packages simple, we are going to use the MacOS package manager [brew](https://brew.sh/). 
Click on the brew link, copy the text beginning with `/bin/bash`, and then paste it into your terminal. 
This may take a minute and put out a lot of information on your terminal, but just wait until it is done.
Once the installation has finished, run the command `brew --version` in your console, and you should get output similar to this:
```bash
name@computer icj-project-rig % brew --version
Homebrew 4.0.22
Homebrew/homebrew-core (git revision 6fb14ad0d84; last commit 2023-03-20)
Homebrew/homebrew-cask (git revision d15dfcc577; last commit 2023-03-20)
name@computer icj-project-rig % 
```
2. Click on [this link](https://formulae.brew.sh/cask/google-cloud-sdk) to download the `gcloud` CLI tool. 
Just like the above command this may take a second, but wait until it says it is finished.
Once the installation has finished, run the command `gcloud --version` in your terminal, and you should get some output similar to this:
```bash
name@computer icj-project-rig % gcloud --version
Google Cloud SDK 428.0.0
bq 2.0.91
core 2023.04.25
gcloud-crc32c 1.0.0
gsutil 5.23
Updates are available for some Google Cloud CLI components.  To install them,
please run:
  $ gcloud components update
name@computer icj-project-rig % 
```

3. We are now going to authenticate our Google credentials on our local machine, using the following command `gcloud auth login --brief --enable-gdrive-access`. 
This will open a browser where it will show you all of your available Google names. 
**Make sure to select your _personal_ gmail account for this part**. If you use your `utexas.edu` email, you won't have permission to do what we need to do.
After you select your _personal_ gmail account, you will be sent to a permissions screen that will look something like this:
<img src='images/gcloud_cli_permissions.png' height='500'> \
Click `Allow` and you will have given your computer access to manage files on your Google Drive and in the Google Cloud Project.
4. Now we are going to [create the project](https://cloud.google.com/sdk/gcloud/reference/projects/create) that we are going to work with in this class via the command `gcloud projects create icj-project --set-as-default`.
This command creates our new project called `icj-project` on the Google Cloud Platform and sets it as our default project.

Once this process is done, enter the command `gcloud auth application-default login` into your terminal, follow the browser prompts, and you should be able to see what project you are logged into.
```bash
name@computer icj-project-rig % gcloud auth application-default login
Your browser has been opened to visit:

    https://accounts.google.com/o/oauth2/auth?[VERY_LARGE_STRING]


Credentials saved to file: [$HOME/.config/gcloud/application_default_credentials.json]

These credentials will be used by any library that requests Application Default Credentials (ADC).

Quota project "[RECENTLY_CREATED_PROJECT_ID]" was added to ADC which can be used by Google client libraries for billing and quota. Note that some services may still bill the project owning the resource.
name@computer icj-project-rig % 
```

### Setting up the environment variable
This environment variable will be used when you are accessing this project through [GitHub Codespaces](https://github.com/features/codespaces).
To create the environment variable, make sure that you logged in using the `gcloud` command above.

1. In a Terminal, do `code ~/.bash_profile` to open your ".bash_profile" file in VS Code. In there, you should see some stuff there already from other configurations. (Holler if you don't as that means you are likely in the wrong file.)
2. Add the text below to the `~./bash_profile` file, save, and exit the file.
```bash
# Google Auth
export GOOGLE_APPLICATION_CREDENTIALS="$HOME/.config/gcloud/application_default_credentials.json"
```

## Test these settings

1. Create a folder in your icj folder called `yourname-test`.
2. Open that folder in Visual Studio Code.
3. Open a VS Code Terminal and run:

```bash
degit utdata/icj-google-fetch-test#main
```

You should get this in return:

```bash
> cloned utdata/icj-google-fetch-test#main
```

And it will download a bunch of files into your folder.

1. Run `npm ci`. This will also download a bunch of files. It might take a couple of minutes to run.
2. Run `gulp fetch`.

If everything works, you should have a return like this:

``` bash
$ gulp fetch
[14:38:53] Using gulpfile ~/Documents/icj/icj-fetch-test/gulpfile.js
[14:38:53] Starting 'fetch'...
[14:38:53] Finished 'fetch' after 8.61 ms
Downloaded `library` (1RgMhjtkXlbbf9uzSzy_xPRKwxcVZIZqVytgM_JoU4E4)
Downloaded `bookstores` (1gDwO-32cgpBDn_0niV0iu6TqQTaRDr4nmSqnT53magY)
```

Your path might differ for "Using gulpfile", but what you are looking for is that two files were downloaded, one called `library` and one called `bookstores`.

---

You should be done!
