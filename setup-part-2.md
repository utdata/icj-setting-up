# Part 2: Node, gcloud

These configurations are needed to run our Node-based development environments. This comes up about half-way through the semester.

::: callout-important

## Codespaces

In the last few years, virtual computing has become so prevalent and cheap that we may not need to do this kind of development locally. Github has a feature called [Codespaces](https://github.com/features/codespaces) that is baked right into your repo.

Spring 2024 is the first semester class templates have been configured to use Codespaces and I don't really have directions for using them because I haven't experienced it. Perhaps we can all learn together?

That said, I'd like to try and set up computers with Node and such as outlined below. If we run into problems, Codespaces will be our go-to.

:::

## Installing Node

Node is a Javascript runtime environment we will use to build news applications. Installation is different for Mac vs Windows. 

::: {.panel-tabset}

### Mac

We need to make sure you have xcode tools first.

#### Checking xcode

1. Run this in your Terminal:

    ```bash
    xcode-select -p
    ```

You should get a path in return. Something like "/Library/Developer/CommandLineTools".

If you don't **AND ONLY IF YOU DON'T**, you need to install it.

#### Installing xcode-select (only if needed)

1. In your Terminal run this:

    ```bash
    xcode-select --install
    ```

2. A software update popup window will appear that asks: "The xcode-select command requires the command line developer tools. Would you like to install the tools now?" choose to confirm this by clicking **Install**, then agree to the Terms of Service when requested (feel free to read them thoroughly, we’ll be here).

It can take a long while to download and install. If you get an error on this install, let me know as I have a copy I can give you.

#### NVM

We will use NVM to install Node.js. Again, follow the prompts and you should be fine.

1. Go to [this page](https://github.com/nvm-sh/nvm#install--update-script) and copy the first code chunk that starts with `curl`.
2. Paste that into your Terminal and run it.
3. After it is done, quit Terminal and relaunch it.
4. **Test**: _After relaunching a terminal_ do `nvm list` to make sure you don't get an error.

#### Node

Use NVM to install Node.

1. Install the long-term support of Node:

    ```bash
    nvm install --lts
    ```

2. **Test**: Do `node -v` to make sure it worked. It should give you back a version, like "v18.18.0".

### Windows

Microsoft recommends using nvm-windows to install node, so let's go with that.

1. Follow [these directions to install nvm-windows](https://docs.microsoft.com/en-us/windows/nodejs/setup-on-windows) **BUT READ THE NEXT STEPS FIRST**.
    - When they say Launch Powershell, you should use **Git Bash** instead.
    - When it gets to installing Node.js **DON'T DO** `nvm install latest`. Instead, use this command:

      ```bash
      nvm install --lts
      ```

2. To make sure it worked, in Git Bash do:

      ```bash
      node --version
      ```

    - You should get a response that says you are using a version, like `v18.18.0`.

:::

### Update npm

NPM is a package repository. We need to update it.

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

> IMPORTANT: You must have and use a **PERSONAL** Gmail/Google account for this process. Your **UTMail Google account will not work**.

### Install Google Cloud tools

Again, differences between macOS and Windows.

::: {.panel-tabset}

#### macOS

To make the installation of packages simple, we are going to use the MacOS package manager [brew](https://brew.sh/) to install some Google Cloud tools. You should already have brew installed from earlier in the semester.

1. Run the following to install the Google Cloud SDK

    ```bash
    brew install --cask google-cloud-sdk
    ```

2. **Test**: Run `gcloud --version` and make sure a version number is returned.

#### Windows

1. Follow the instructions found in [this link](https://www.educative.io/answers/how-to-install-google-cloud-cli-on-windows) to download and install the `gcloud` CLI tool.
2. **Test**: Once the installation has finished, run the command `gcloud --version` in your terminal, and you should get some output similar to this: `Google Cloud SDK 428.0.0`

:::

### Authenticate our session

We are now going to authenticate our Google credentials on our local machine. 

> **Make sure to select your _personal_ gmail account for this part**. If you are logged into your `utexas.edu` email, you won't have permission to do what we need to do. It works best if you **log out of all your accounts in all your browsers** (Chrome, Safari, Edge, etc) before you start.

1. In a Terminal, use the following command:

    ```bash
    gcloud auth login --brief --enable-gdrive-access
    ```

This will open a browser and ask you to log into your Google account. Select your _personal_ gmail account, you will be sent to a permissions screen that will look something like this:

![gcloud auth](images/gcloud_cli_permissions.png)

1. Click `Allow` and you will have given your computer access to manage files on your Google Drive and in the Google Cloud Project.
1. In the same browser that opened, go to [console.cloud.google.com](https://console.cloud.google.com/), where it should ask you to OK the terms of service.

### Create and configure project

Again, be in your personal Google account as you will have to authenticate again.

We are going to run through several `gcloud` commands to set you computer to access Google Docs and Google sheets through programing. It's a lot of ecsoteric steps and things could go wrong at each step. I don't outline the output you get in return, but there can be a little or a lot.

Just keep an eye out for `ERROR` or `can't find [whatever]` and hollar if that happens.

::: callout-important
You have to edit some of the commands below to be personal to you. Everywhere you see `icj-YOURNAME` you need to edit that part of the command to use your first name, all lowercase, like `icj-alex`. Then you use that same value for the later commands that use `icj-YOURNAME`. PLEASE ASK FOR HELP IF YOU NEED IT. Important: After you paste a terminal command, to edit it you have the use the left arrow key to get to the part of the command to then delete and make changes.
:::

1. Do this command to create the project (**but edit icj-YOURNAME as noted above**):

    ```bash
    gcloud projects create icj-YOURNAME --set-as-default --name="ICJ Project"
    ```

1. Do this to log in and set your project as a default:

    ```bash
    gcloud auth application-default login
    ```

1. Next, we'll create a Google service account:

    ```bash
    gcloud iam service-accounts create generic-service-account
    ```

1. Next we need to bind the service account to our project with the command below. You should get a reply that reports bindings for roles of editor and owner. (**There are TWO places here where you have to switch out `icj-YOURNAME`.**)

    ```bash
    gcloud projects add-iam-policy-binding icj-YOURNAME --member='serviceAccount:generic-service-account@icj-YOURNAME.iam.gserviceaccount.com' --role='roles/editor'
    ```

1. Then we enable the Google Docs and Sheets API for your project:

    ```bash
    gcloud services enable docs.googleapis.com sheets.googleapis.com
    ```

1. Now we'll create a service account authorization key. This is similar to ssh key above, but for Google. **Again, swap out `icj-YOURNAME`**:

    ```bash
    gcloud iam service-accounts keys create "$HOME/.config/gcloud/service_account_key.json" \
        --iam-account=generic-service-account@icj-YOURNAME.iam.gserviceaccount.com
    ```

1. Then add the key to your `.bash_profile` with this commaned:

    ```bash
    echo 'export GOOGLE_APPLICATION_CREDENTIALS="$HOME/.config/gcloud/service_account_key.json"' >>~/.bash_profile
    ```

1. Sync your terminal with the updated bash profile:

    ```bash
    source ~/.bash_profile
    ```

Yes, that was a lot. Hopefuly it worked. We're about to find out.

## Test these settings

1. Create a folder in your icj folder called `yourname-test`.
2. Open that folder in Visual Studio Code.
3. Open a VS Code Terminal and run:

    ```bash
    degit utdata/icj-google-fetch-test#main
    ```

You should get this in return:

`> cloned utdata/icj-google-fetch-test#main`

And it will download a bunch of files into your folder.

1. Run `npm install`. This will also download a bunch of files. It might take a couple of minutes to run.
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
