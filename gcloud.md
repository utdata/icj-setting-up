# Using gcloud cli

We end up using the Google Cloud SDK to set up authorization to allow programming access to Google Docs and Sheets. Some useful commands:

- `gcloud auth list` tells you which account you are in and how to set a new active account.
- `gcloud auth revoke` logs you out of your active account. `--all` flag logs you out of all accounts, I think.
- `gcloud projects list` shows all the projects for the account.
- `gcloud config get-value project` shows you which project you are in.
- `gcloud config set project [project-id]` but replace `[project-id]` with the project name.

See Setting Up Part 2 for commands to set up a project and enable the APIs.
