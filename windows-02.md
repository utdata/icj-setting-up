
# Setting up for Node

We don't do this until later in the semester, when we start using Node-based tools.

## Node.js

Node is a Javascript runtime environment we will use to build news applications. This is where things get kinda dicey with my (lack of) Windows experience.

- Install Node.js [using the installer](https://nodejs.org/en/download/)
- In Git Bash, do `node --version` to make sure it worked. (v8.11.4 was the current stable version when this was written.)
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

There is a point in class when your computer will need access to your Google Drive account. Much like we did with ssh keys, we'll create a file to save on your computer that includes a secret key that works only for you.

### Creating a service account

**Make sure you're logged into a _personal_ gmail account for this part**. If you use your utexas.edu email, you won't have permission to do what we need to do.

The instructions for how to create a service account on Google are [here](https://cloud.google.com/docs/authentication/getting-started). Follow that link and click on `Go to the Service Account Key page`.

- First, you must create a project. The term "project" is a little misleading because you do not need to do this for each project. You only need to do this once per email address. Name your project `icj-project`.
- You are next directed to create a "service account key".
  - For **Service account**, choose "New service account".
  - For the **Service account name**, use `icj`. The **Service account ID** will get filled out for you.
  - For Role, use the **Select a role** dropdown and go to `Project --> Owner` and select it.
- Once you hit **Create key**, a file will be saved on your machine. _This file is important_ and you need to keep it on your machine! I renamed my file `google_drive_fetch_token.json` and put it in same folder with all of my other icj class projects, for example: `/Users/christian/Documents/icj/google_drive_fetch_token.json`.
- Click on **Library** in the left navigation to go to the [API Library](https://console.developers.google.com/apis/library).
- Use the search to find the **Google Docs API** and select it.
  - Make sure `icj-project` is selected in the top nav near the Google Cloud Services logo.
  - Then click on the **Enable** buttton to activate it.
- Use the search bar to find **Google Sheets API** and choose it and **Enable** it.

### Setting up the environment variable

Now we need to install this file as an environment variable to authenticate to Google using the information in the json file you just created.

> I need to work with someone on Windows to find the best way to do this. Since we use Git Bash, we _might_ be able to do it like we do for Mac. Otherwise we have to try the methods described in [Google's instructions for Windows](https://cloud.google.com/docs/authentication/getting-started#windows).

----

You should be done!
