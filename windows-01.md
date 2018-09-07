# Windows

I'll be honest ... We may have extra stumbling blocks with course material using Windows. I'm less familiar with it, and haven't had a chance yet to explore and tailor the course for Windows users. It is NOT impossible ... plenty of folks do development on Windows, and it is getting easier every day. Just be prepared to troubleshoot many of your own problems.

Everything listed here is free unless otherwise noted.

## At the beginning of the semester

### Text editor

- Install [VS Code](https://code.visualstudio.com/docs/setup/windows). The installation process should add it to your `%PATH%`.
- (There are other good code editors like [Atom](https://atom.io/) and [Sublime](https://www.sublimetext.com/3), but I'll use VS Code in class.)

### Version control system

- Install [Git](https://git-scm.com/download/win), our source code version control program. This will allow us to save our code in steps. This will also install Git Bash, which will be your terminal app.
- Configure your [Git profile](https://help.github.com/articles/setting-your-username-in-git/#platform-windows) so you don't have to type you password all the time.
- After setting up Git Bash, you [configure your VS Code integrated terminal](https://code.visualstudio.com/docs/editor/integrated-terminal#_windows). I _think_ the easiest way is to go to View > Command Pallete and type in `Select Default Shell` and find it, but I haven't tried it.

### Set up Github

If you don't already have a Github account, go to [github.com/](http://github.com/) and create an account. Two important things to note:

- Choose your username carefully. Don't use upper case characters or special characters because this will become part of a URL later. Don't make the name specific to this class. This is your personal Github profile FOREVER.
- USE YOUR UNIVERSITY EMAIL IF YOU HAVE ONE. You might want to apply for the [Student developer pack](https://help.github.com/articles/applying-for-a-student-developer-pack/), which will get you private repositories.

### Saving your Github credentials

There are ways you can tell your computers to save your Github username/password. If you are using your own machine, I suggest this first one, setting up SSH keys. If that proves difficult, try the second option.

- I use these directions to create [SSH keys](https://help.github.com/articles/connecting-to-github-with-ssh/) on my machine so I'm never asked for a password. It is not as scary as it looks, though there is some command-line foo to execute.
- Or, you can at least reduce the number of times you have to enter your Github name/password by [caching your password](https://help.github.com/articles/caching-your-github-password-in-git/). We'll have to use this method for lab computers.

### Testing Part 1

We need to make sure everything is set correctly before moving on. So here is how to check:

Before doing this, open a new Git Bash window:

- Do `cd ~` to make sure you are in your home directory.
- Do `git config user.name` and you should get a response that is your name.
- Do `git config user.email` and you should get back your email address.
- Do `code ./` and it should launch VS Code in your home directory.

In the list of Documents, there should be two things:

1. A folder called `bash-git-promopt`.

![git-bash-prompt](images/git-bash-prompt-installed.png)

2. A file called `.bash_profile` with the bash-git-prompt info:

![git-bash-prompt](images/bash_profile-example.png)
