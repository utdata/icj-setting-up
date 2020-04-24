
# Setting up for Node

We don't do this until later in the semester, when we start using Node-based tools.

## Node.js

Node is a Javascript runtime environment we will use to build news applications. This is where things get really dicey with my Windows experience.

* Install Node.js [using the installer](https://nodejs.org/en/download/)
* Do `node --version` to make sure it worked. (v8.11.4 was the current stable version when this was written.)
* Now lets update npm:

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

## Alternate installing of Node

> Don't do this unless specifically asked.

* An alternate method to install Node might be to use [NVM for Window](https://danielarancibia.wordpress.com/2017/03/28/install-or-upgrade-nodejs-with-nvm-for-windows/), but I don't know for sure.
* Yet Another option is to use the Windows package manager [Chocolatey](https://nodejs.org/en/download/package-manager/#windows).)

## Google Drive authentication

There is a point in class when your computer will need access to your Google Drive account. Much like ssh keys, we'll create a file to save on your computer that includes a secret key that works only for you.

### Creating a service account

**Make sure you're logged into a personal gmail account** for this part. If you use your utexas.edu email, you won't have permission to do what we need to do.

The instructions for how to create a service account on Google are [here](https://cloud.google.com/docs/authentication/getting-started). Follow that link and click on `Go to the Service Account Key page`.

- First, you must create a project. The term "project" is a little misleading because you do not need to do this for each project. You only need to do this once per email address. Name your project `icj-project`.

- You are next directed to create a "service account key".
  - For **Service account**, choose "New service account"
  - For the **Service account name**, use `icj`. The **Service account ID** will get filled out for you.
  - For Role, use the **Select a role** dropdown and go to `Project --> Owner` and select it.
- Once you hit **Create key**, a file will be saved on your machine. _This file is important_ and you need to keep it on your machine! I renamed my file `google_drive_fetch_token.json` and put it in same folder with all of my other icj class projects, for example: `/Users/christian/Documents/icj/google_drive_fetch_token.json`.
- Click on **Library** in the left navigation to go to the [API Library](https://console.developers.google.com/apis/library)
- Use the search to find the **Google Docs API** and select it.
  - Make sure `icj-project` is selected in the top nav near the Google Cloud Services logo.
  - Then click on the **Enable** buttton to activate it.
- Use the search bar to find **Google Sheets API** and choose it and **Enable** it.

### Setting up the environment variable

Now we need to install this file as an environment variable to authenticate to Google using the information in the json file you just created.

Refer to [Google's instructions if you're using Windows](https://cloud.google.com/docs/authentication/getting-started#windows).
