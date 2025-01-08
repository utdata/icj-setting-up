# Codespaces

::: callout-warning

## Out of date

We've made some updates to the icj-project-rig that requires an update there that has not yet been made.

:::

The icj-project-rig can be used in [GitHub Codespaces](https://github.com/features/codespaces), a free virtual machine environment. This might be helpful if you have trouble with your own computer.

This isn't a tutorial on using Codespaces, but it does provide some necessary information if you explore the option. This assumes you already have your own copy of the project and it is pushed to Github. You work out of your own project.

## Install gulp

Once you launch a codespace it will recognize you are in a Node environment but you still need to install some packages the first time you launch it:

1. Once the container is up and running, do `npm install -g gulp` to install gulp.
2. Run `npm ci` to do a clean install on all the other packages in the project.

If you come back to an existing Codespace you should not have to run those again.

## Google auth access

There is one `gulp` command that will not work in Codespaces unless you jump through some extra hoops.

`gulp fetch` is the command that downloads Google Docs and Sheets documents as JSON, as outlined in `project.config.json`. The process expects to find an authorization file on your own computer that we set up in [icj-setting-up Part 2](https://github.com/utdata/icj-setting-up#readme), but that file doesn't exist on the Codespaces virtual machine.

You'll need to set up two environment variables to make it work.

> **NOTE:** It is absolutely imperative that you DO NOT commit the contents of `service_account_key.json` to your branch at all. If someone else were able to see the contents of that file, they could execute any action that service account has in its abilities.
Since `service_account_key.json` is in the `.gitignore` file, you should not be able to check it in, but it is important to remember that for the sake of transparency.

We will be following the process shown [here](https://docs.github.com/en/codespaces/managing-your-codespaces/managing-encrypted-secrets-for-your-codespaces#adding-a-secret)

As you follow those steps you'll need the information below.

### Credential path

- The "Name" of the secret will be `GOOGLE_CREDENTIALS`.
- The "Value" of the secret will be: `$HOME/.config/gcloud/service_account_key.json`

### Credential contents

- The "Name" of the secret will be `GOOGLE_APPLICATION_CREDENTIALS`
- For the "Value" of the secret you need to copy the contents of a file on your local machine. Follow the steps below:

1. Run this command on your local machine, which will copy needed the file to your clipboard:

    ```bash
    pbcopy < $HOME/.config/gcloud/service_account_key.json
    ```

1. Return to your web browser and for the "Value" do *Cmd-v* to paste the contents of your clipboard.

## Load the secrets

When you open your Codespace, you will run the following command.

```bash
npm run codespace-google-auth
```

After doing that, you should be able to run `gulp fetch` to update the data JSON files.
