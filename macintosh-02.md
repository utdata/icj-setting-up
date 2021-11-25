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

1. Run this in your Terminal:

``` bash
nvm install --lts
```

After it installs, then do:

``` bash
nvm use --lts
```

1. **Test**: Do `node -v` to make sure it worked. (It should give you back "v16.13.0" as of this writing.)

### npm

Now lets update npm:

1. Run this:

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

There is a point in class when your computer will need access to your Google Drive account. Much like ssh keys, we'll create a file to save on your computer that includes a secret key that works only for you.

### Creating a service account key

Log out of Google entirely and then **make sure you're logged into a personal gmail account only** for this part. If you try to use your utexas.edu email, you won't have permission to do what we need to do.

1. The instructions for how to create a service account on Google are [here](https://cloud.google.com/docs/authentication/getting-started). Follow that link and click on `Go to the Service Account Key page`.
2. Create a project. The term "project" is a little misleading because you do not need to do this for each project. You only need to do this once per email address. Name your project `icj-project`.
3. You are next directed to create a "service account key".
  - For **Service account**, choose "New service account"
  - For the **Service account name**, use `icj`. The **Service account ID** will get filled out for you.
  - For Role, use the **Select a role** dropdown and go to `Project --> Owner` and select it.
4. Once you hit **Create key**, a file will be saved on your machine. _This file is important_ and you need to keep it on your machine! I renamed my file `google_drive_fetch_token.json` and put it in same folder with all of my other icj class projects, for example: `/Users/christian/Documents/icj/google_drive_fetch_token.json`. Put this where you can find it and won't throw it away on accident.
5. Click on **Library** in the left navigation to go to the [API Library](https://console.developers.google.com/apis/library)
6. Use the search to find the **Google Docs API** and select it.
  - Make sure `icj-project` is selected in the top nav near the Google Cloud Services logo.
  - Then click on the **Enable** button to activate it.
8. Use the search bar to find **Google Sheets API** and choose it and **Enable** it.

### Setting up the environment variable

We are setting this environment variable to authenticate ourselves to Google using the information in the json file you just created.

1. In a Terminal, do `code ~/.bash_profile` to open your ".bash_profile" file in VS Code. You should see some stuff there already from other configurations. (Hollar if you don't as that means you are likely in the wrong file.)
2. Add the text below to this file, but with your own path and file name.

```bash
# Google Auth
export GOOGLE_APPLICATION_CREDENTIALS="/Users/christian/Documents/icj/google_drive_fetch_token.json"
```

### Test these settings

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

Your path might differ for "Using gulpfile", but what you are looking for is that two files were downloaed, one called `library` and one called `bookstores`.

---

You should be done!
