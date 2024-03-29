# Setting up for Node

Hold off on this until we get to this part later in the semester.

If we have reached that point, then fire up Git Bash.

(If you ever see reference to "Terminal", I mean Git Bash for Windows users.)

## Node.js

Node is a Javascript runtime environment we will use to build news applications. This is where things get kinda dicey with my (lack of) Windows experience. Microsoft recommends using nvm-windows to install node, so let's go with that.

1. Follow [these directions to install nvm-windows](https://docs.microsoft.com/en-us/windows/nodejs/setup-on-windows) **BUT READ THE NEXT STEPS FIRST**.
    - When they say Launch Powershell, you should use **Git Bash** instead.
    - When it gets to installing Node.js **DON'T DO** `nvm install latest`. Instead, use this command:

      ```bash
      nvm install v16.18.0
      ```

2. To make sure it worked, in Git Bash do:

      ```bash
      node --version
      ```

    - You should get a response that says you are using `v16.18.0`.
3. Now lets update npm:

    ```bash
    npm install -g npm
    ```

## ICJ template setup

There are some additional global npm tools that we need to install for our tour of NodeJS-based build tools.

1. Run the following in your Git Bash:

```bash
npm install -g gulp degit
```

These are for the task manager [Gulp](https://gulpjs.com/) and a scaffolding tool [Degit](https://www.npmjs.com/package/degit).

## Google Drive authentication

There is a point in class when your computer will need access to your Google Drive account. Much like ssh keys, we'll need specific credentials that work only for you. We will use the Google Cloud Project's command line interface tool to do this.
Otherwise known as the [`gcloud` CLI](https://cloud.google.com/sdk/gcloud).

> IMPORTANT: You must have and use a **PERSONAL** Gmail/Google account for this process. Your **UTMail Google account will not work**.

### Install Google Cloud tools

1. Follow the instructions found in [this link](https://www.educative.io/answers/how-to-install-google-cloud-cli-on-windows) to download and install the `gcloud` CLI tool.
   - Once the installation has finished, run the command `gcloud --version` in your terminal, and you should get some output similar to this: `Google Cloud SDK 428.0.0`

### Authenticate our session

We are now going to authenticate our Google credentials on our local machine. **Make sure to select your _personal_ gmail account for this part**. If you use your `utexas.edu` email, you won't have permission to do what we need to do.

1. In a web browser, make sure you are logged into your **PERSONAL** Google account.
1. In a Terminal, use the following command:

    ```bash
    gcloud auth login --brief --enable-gdrive-access
    ```

This will open a browser where it will show you all of your available Google names. After you select your _personal_ gmail account, you will be sent to a permissions screen that will look something like this:

![gcloud auth](images/gcloud_cli_permissions.png)

Click `Allow` and you will have given your computer access to manage files on your Google Drive and in the Google Cloud Project.

### Create and configure project

Again, be in your personal Google account as you will have to authenticate again.

We are going to run through several `gcloud` commands to set you computer to access Google Docs and Google sheets through programing. It's a lot of ecsoteric steps and things could go wrong at each step. I don't outline the output you get in return, but there can be a little or a lot.

You may be asked some questions during installation. You should be able to answer with the default answer (usually capitalized). If you try these steps more than once you might be errors that a project exists. Ask for help.

Just keep an eye out for `ERROR` or `can't find [whatever]` and hollar if that happens.

Launch a fresh Terminal for this.

> After you run the first command below, take note of the last line of the return. Does it say `Updated property [core/project] to [icj-project]`? If not, it probably added random letters and numbers at the end of `icj-project` and you might need that string later. PLEASE ASK FOR HELP IF SO.

1. Do this command to create the project:

    ```bash
    gcloud projects create icj-project --set-as-default --name="ICJ Project"
    ```

1. Do this to log in and set your project as a default:

    ```bash
    gcloud auth application-default login
    ```

1. Next, we'll create a Google service account:

    ```bash
    gcloud iam service-accounts create generic-service-account
    ```

1. Next we need to bind the service account to our project with the command below. You should get a reply that reports bindings for roles of editor and owner. (This is where we might need to make adjustments if your project id has random letters/numbers.)

    ```bash
    gcloud projects add-iam-policy-binding icj-project --member='serviceAccount:generic-service-account@icj-project.iam.gserviceaccount.com' --role='roles/editor'
    ```

1. Then we enable the Google Docs and Sheets API for your project:

    ```bash
    gcloud services enable docs.googleapis.com sheets.googleapis.com
    ```

1. Now we'll create a service account authorization key. This is similar to ssh key above, but for Google:

    ```bash
    gcloud iam service-accounts keys create "$HOME/.config/gcloud/service_account_key.json" \
        --iam-account=generic-service-account@icj-project.iam.gserviceaccount.com
    ```

1. Then add the key to your `.bash_profile` with this commaned:

    ```bash
    echo 'export GOOGLE_APPLICATION_CREDENTIALS="$APPDATA\gcloud\service_account_key.json"' >>~\.bash_profile
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

----

You should be done!
