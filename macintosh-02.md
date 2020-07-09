# Macintosh Part 2: Installing Node.js setup

Hold off on this until we get to this part later in the semester.

If we have reached that point, then fire up your Terminal.

## Checking xcode

See if you already have the XCode command-line tools installed.

`xcode-select -p`

You should get a path in return. Something like "/Library/Developer/CommandLineTools".

If you don't **AND ONLY IF YOU DON'T**, you need to install it: `xcode-select --install`. It can take a long while to download and install.

## Setting up a Node environment

### NVM

- We will use NVM to install Node.js. Again, follow the prompts and you should be fine:

``` bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
```

- **Test**: Close and reopen a terminal and do `nvm list` to make sure you don't get an error.

### Node

- Use NVM to install Node:

``` bash
nvm install 10.19.0
```

- **Test**: Do `node -v` to make sure it worked. (It should give you back "v10.19.0", which was the current stable version when this was written.)

### npm

- Now lets update npm:

```bash
npm install -g npm
```

- **Test**: Do `npm -v` and it should return with a version number.

## ICJ project setup

There are some additional global npm tools that we need to install for our tour of NodeJS-based build tools. Do each of these, one line at a time.

```bash
npm install -g gulp
npm install -g degit
```

These are for the task manager [Gulp](https://gulpjs.com/) and a scaffolding tool [Degit](https://www.npmjs.com/package/degit).

## Google Drive authentication

There is a point in class when your computer will need access to your Google Drive account. Much like ssh keys, we'll create a file to save on your computer that includes a secret key that works only for you.

### Creating a service account key

**Make sure you're logged into a personal gmail account** for this part. If you try to use your utexas.edu email, you won't have permission to do what we need to do.

- The instructions for how to create a service account on Google are [here](https://cloud.google.com/docs/authentication/getting-started). Follow that link and click on `Go to the Service Account Key page`.
- Create a project. The term "project" is a little misleading because you do not need to do this for each project. You only need to do this once per email address. Name your project `icj-project`.
- You are next directed to create a "service account key".
  - For **Service account**, choose "New service account"
  - For the **Service account name**, use `icj`. The **Service account ID** will get filled out for you.
  - For Role, use the **Select a role** dropdown and go to `Project --> Owner` and select it.
- Once you hit **Create key**, a file will be saved on your machine. _This file is important_ and you need to keep it on your machine! I renamed my file `google_drive_fetch_token.json` and put it in same folder with all of my other icj class projects, for example: `/Users/christian/Documents/icj/google_drive_fetch_token.json`. Put this where you can find it and won't throw it away on accident.
- Click on **Library** in the left navigation to go to the [API Library](https://console.developers.google.com/apis/library)
- Use the search to find the **Google Docs API** and select it.
  - Make sure `icj-project` is selected in the top nav near the Google Cloud Services logo.
  - Then click on the **Enable** button to activate it.
- Use the search bar to find **Google Sheets API** and choose it and **Enable** it.

### Setting up the environment variable

We are setting this environment variable to authenticate ourselves to Google using the information in the json file you just created.

- In a Terminal, do `code ~/.bash_profile` to open your ".bash_profile" file in VS Code. You should see some stuff there already from other configurations. (Hollar if you don't as that means you are likely in the wrong file.)
- Add the text below to this file, but with your own path and file name.

```bash
# Google Auth
export GOOGLE_APPLICATION_CREDENTIALS="/Users/christian/Documents/icj/google_drive_fetch_token.json"
```

----

You should be done!
