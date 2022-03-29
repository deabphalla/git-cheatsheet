# Cheatsheet
  
## Installation and Configuration



To install git on you linux environment you could follow bellow guideline:

**Installation**
```bash
sudo apt update
sudo apt install git
git --version
```
Atfter installing, there are some configuration you need to configure.

**Username configuration**
```bash
git config --global user.name "YOUR USERNAME"
git config --global user.name
```

**Email configuration**
```bash
git config --global user.email “youremail@example.com”
git config --global user.email
```

To view the information that you entered, along with other global options:

**List global config**
```bash
git config --global --list
```

## Remote Repository

A ``remote`` in Git is a common repository that all team members use to exchange their changes. In most cases, such a remote repository is stored on a code hosting service like GitLab, GitHub or on an internal server.

Remote repository connect between local developer's environment via `ssh key` or username and password when you push, pull or clone project.

To generate a new ssh key for your linux:

**Generate SSH Keygen**
```bash
ssh-keygen -t rsa -C "your_email@example.com"
cat .ssh/id_rsa.pub
```

``id_rsa.pub`` is the public ssh key which will be used for comunication or remote access.

## Basic Command Line

**Initialization**

If you have an existing local directory that you want to initialize for version control, use the init command to instruct Git to begin tracking the directory (It will create a `.git` directory that contains the Git configuration files).


```bash
git init
```

**Git Clone**

To clone project from remote repository via HTTPS, using the following command. It will ask you the username and password to process:

```bash
git clone https://gitlab.com/gitlab-org/gitlab.git
```

And to clone project using SSH:

```bash
git clone git@gitlab.com:gitlab-org/gitlab.git
```

With ``git clone`` above it will download a copy of the files in a folder named after the project’s name. You can then navigate to the directory and start working on it locally.

**Checkout Branch**

You are always in a branch when working with Git. There will be always a ``master`` branch which it is the first initialize and to switch between branch:

```bash
git checkout branch_name
git checkout master
```

You can checkout a branch (BranchB) which is a copy of other branch (BranchA), to work from without affecting the original branch. It will directly change you to a new branch (BranchB) you created:

```bash
git checkout -b BranchB BranchA
git checkout -b master master-v3
```

If you use only ``git checkout -b BranchB`` you will create a new branch (BranchB) which is a copy of branch you are working. 

To show list of your branches in your local environment:

```bash
git branch
```

**Status, Diff and Log**

During the development, to view the changed files on your terminal:

```bash
git status
```

And to see what those changes, using ``git diff``:

```bash
git diff
git diff files.rst views.py
git diff templates/header.html
```

Using ``git log`` to display the entire commit history using the default format.

```bash
git log
```

**Add and Commit**

To commit the changed files, you need to add those files first. ``git add .`` is used to add all changed files and you can just add some of them by those files' names, separate with a space.

```bash
git add templates/header.html
git add files.rst views.py
git add .
```

After add files, ``git commit`` to save those changes. You can ``git status`` again to see files that going to commit.

```bash
git commit -m "COMMENT TO DESCRIBE THE INTENTION OF THE COMMIT"
```
**Checkout and Reset**

*Before Add*, to discard changed files, you can use ``git checkout`` following by untracked or changed files or ``git checkout .`` to discard all.

```bash
git checkout templates/header.html
git checkout files.rst views.py
git checkout .
```

*After Added*, using ``git reset`` following by added files to undo.

```bash
git reset templates/header.html
git reset files.rst views.py
git reset .
```
*After committed*, to undo the last commit:

```bash
git reset --hard HEAD
```

**Push and Pull**

``Push``: is used to push your commit code for your local to remote repository.

```bash
git push origin branch_name
```

``Pull``: is used to pull code from remote repository as commit(s) to your local machine. For best practise, always pull your code (make it up to date) before development or checkout branch.
```bash
git pull
git pull origin branch_name
```

``Fetch`` is used to pull code from remote repsitory as changes to your local machine and those code will become your commit if you push.

```bash
git fetch
```

**Merge Request**

``Merge`` is used to merge between two branches and only users who have the right can merge the request.

Link for generating [ssh key]( https://confluence.atlassian.com/bitbucketserver/creating-ssh-keys-776639788.html).
