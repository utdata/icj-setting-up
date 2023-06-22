# Setting up for Node
We don't do this until later in the semester, when we start using Node-based tools.

## Node.js
Node is a Javascript runtime environment we will use to build news applications. This is where things get kinda dicey with my (lack of) Windows experience. Microsoft recommends using nvm-windows to install node, so let's go with that.

- Follow [these directions to install nvm-windows](https://docs.microsoft.com/en-us/windows/nodejs/setup-on-windows) **BUT READ THE NEXT STEPS FIRST**.
  - When they say Launch Powershell, you should use **Git Bash** instead.
  - When it gets to installing Node.js **DON'T DO `nvm install latest`**.
  - Instead, use this command: `nvm install v16.18.0`
- In Git Bash, use the command `node --version` to make sure it worked.
  - You should get a response that says you are using `v16.18.0`.
- Now lets update npm:

```bash
npm install -g npm
```

## ICJ template setup
There are some additional global npm tools that we need to install for our tour of NodeJS-based build tools. Do each of these, one line at a time.

```bash
npm install -g gulp
npm install -g degit
```

These are for the task manager [Gulp](https://gulpjs.com/) and a scaffolding tool [Degit](https://www.npmjs.com/package/degit).

## Google Drive authentication
1. Follow the instructions found in [this link](https://www.educative.io/answers/how-to-install-google-cloud-cli-on-windows) to download and install the `gcloud` CLI tool.
   Once the installation has finished, run the command `gcloud --version` in your terminal, and you should get some output similar to this:
```bash
% gcloud --version
Google Cloud SDK 428.0.0
bq 2.0.91
core 2023.04.25
gcloud-crc32c 1.0.0
gsutil 5.23
Updates are available for some Google Cloud CLI components.  To install them,
please run:
  $ gcloud components update
% 
```

2. We are now going to authenticate our Google credentials on our local machine, using the following command `gcloud auth login --brief --enable-gdrive-access`.
   This will open a browser where it will show you all of your available Google names.
   **Make sure to select your _personal_ gmail account for this part**. If you use your `utexas.edu` email, you won't have permission to do what we need to do.
   After you select your _personal_ gmail account, you will be sent to a permissions screen that will look something like this:
   <img src='images/gcloud_cli_permissions.png' height='500'> \
   Click `Allow` and you will have given your computer access to manage files on your Google Drive and in the Google Cloud Project.
3. Now we are going to [create the project](https://cloud.google.com/sdk/gcloud/reference/projects/create) that we are going to work with in this class via the command `gcloud projects create icj-project --set-as-default`.
   This command creates our new project called `icj-project` on the Google Cloud Platform and sets it as our default project.

Once this process is done, enter the command `gcloud auth application-default login` into your terminal, follow the browser prompts, and you should be able to see what project you are logged into.
```bash
% gcloud auth application-default login
Your browser has been opened to visit:

    https://accounts.google.com/o/oauth2/auth?[VERY_LARGE_STRING]


Credentials saved to file: [%APPDATA%\gcloud\application_default_credentials.json]

These credentials will be used by any library that requests Application Default Credentials (ADC).

Quota project "[RECENTLY_CREATED_PROJECT_ID]" was added to ADC which can be used by Google client libraries for billing and quota. Note that some services may still bill the project owning the resource.
% 
```

We'll test this with the icj-project-template when the time comes. If you use OneDrive, you might have to use **Git Bash** for some steps instead of the terminal within VS Code.

### Setting up the environment variable
> There _may_ be some issues setting this up on Windows machines that use OneDrive. It has been successfully installed on a non-OneDrive setup using this method.

We are setting this environment variable to authenticate ourselves to Google using the information in the json file you just created.

1. Open a new Git Bash prompt.
2. Enter `code .bash_profile` to open your `.bash_profile` file in VS Code. You should see some stuff there already from other configurations. (Holler if you don't as that means you are likely in the wrong file.)
```bash
# Google Auth
export GOOGLE_APPLICATION_CREDENTIALS="$APPDATA\gcloud\application_default_credentials.json"
```

## Possible test scenario
- Create a folder in your icj folder called `yourname-test`.
- Open that folder in Visual Studio Code.
- Open a VS Code Terminal and run:

```bash
$ degit utdata/icj-google-fetch-test#main
```

You should get this in return:

```bash
> cloned utdata/icj-google-fetch-test#main
```

And it will download a bunch of files into your folder.

- Run `npm ci`. This will also download a bunch of files. It might take a couple of minutes to run.
- Run `gulp fetch`.

If everything works, you should have a return like this:

```bash
$ gulp fetch
[14:38:53] Using gulpfile ~/Documents/icj/icj-fetch-test/gulpfile.js
[14:38:53] Starting 'fetch'...
[14:38:53] Finished 'fetch' after 8.61 ms
Downloaded `library` (1RgMhjtkXlbbf9uzSzy_xPRKwxcVZIZqVytgM_JoU4E4)
Downloaded `bookstores` (1gDwO-32cgpBDn_0niV0iu6TqQTaRDr4nmSqnT53magY)
```

Your path might differ for "Using gulpfile", but what you are looking for is **"Downloaded \`library\`"** and **"Downloaded \`bookstores\`**. If you didn't get BOTH of those then something isn't right.

If you get an error, try this before reaching out to me:

- Open Git Bash
- Use `cd` to get into your test folder. Make sure you are there using `pwd`.
- run `gulp fetch` to see if it downloads two files.

If that also doesn't work, reach out to me to troubleshoot.

----

You should be done!

> Note for Crit: Might be able to use `%userprofile%` instead of `C:/Users/your_username/`.
