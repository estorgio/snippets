[[Return to Index]](../README.md)

# Git

## Table of Contents
- [Setting up SSH credentials](#setting-up-ssh-credentials)
- [Getting Started](#getting-started)
- [Basic Commands](#basic-commands)
  - [Initialize git repository](#initialize-git-repository)
  - [Get current status](#get-current-status)
  - [Add files to staging](#add-files-to-staging)
  - [Remove files from staging](#remove-files-from-staging)
  - [Commit files in staging](#commit-files-in-staging)
  - [Download commits from remote repository](#download-commits-from-remote-repository)
  - [Upload commits to remote repository](#upload-commits-to-remote-repository)
  - [Make a new branch and switch to it](#make-a-new-branch-and-switch-to-it)
  - [List all existing branches](#list-all-existing-branches)
  - [Delete branch](#delete-branch)
  - [Push branch to origin on first create](#push-branch-to-origin-on-first-create)
  - [Merge a branch to another](#merge-a-branch-to-another)
  - [Resolve merge conflicts](#resolve-merge-conflicts)
  - [Abort merge](#abort-merge)
  - [Discard uncommited changes in working directory](#discard-uncommited-changes-in-working-directory)
  - [List all commits in current branch](#list-all-commits-in-current-branch)
  - [Add tags](#add-tags)
  - [Remove last commit](#remove-last-commit)

## Setting up SSH keys
Steps on setting up SSH credentials on a newly installed computer.
- Download and install [Git for Windows](https://git-scm.com/).
- Create `~/.ssh` and `~/.ssh/keys` directories
    ```bash
    mkdir ~/.ssh
    mkdir ~/.ssh/keys
    ```
- Create `config` file
    ```bash
    touch ~/.ssh/config
    ```
- Open `config` file and paste the following:
    ```
    Host github-default-ssh-profile
        HostName github.com
        User git
        IdentityFile ~/.ssh/keys/default.keyfile
        IdentitiesOnly yes
    ```
- Generate an SSH key and place it in `~/.ssh/keys` directory
    ```bash
    ssh-keygen -t rsa -b 4096 -f "~/.ssh/keys/default.keyfile"
    ```
- Copy your public key file and paste it on [GitHub -> Settings -> SSH and GPG keys](https://github.com/settings/keys)
    ```bash
    clip < ~/.ssh/keys/default.keyfile.pub
    ```
- Test connection to remote GitHub server using your SSH profile
    ```bash
    ssh -T github-default-ssh-profile
    ```
- *Optional:* You may also add another profile to `config` if you want to manage multiple SSH keys for different environments
    ```
    Host github-default-ssh-profile
        HostName github.com
        User git
        IdentityFile ~/.ssh/keys/default.keyfile
        IdentitiesOnly yes

    Host just-another-profile
        HostName bitbucket.com
        User git
        IdentityFile ~/.ssh/keys/just-another-profile.keyfile
        IdentitiesOnly yes
    ```


## Getting Started
Steps on how to creating a new git repository.

- Create a new directory for your project
    ```bash
    mkdir new_project
    cd new_project
    ```
- Initialize the local repository and add your files
    ```bash
    git init
    ```
- Add your full name and email (use `--global` flag to make it default)
    ```bash
    git config user.name "John Doe"
    git config user.email "john.doe@gmail.com"
    ```
- If you're on Windows, make sure to set `core.autocrlf` to `input`
    ```bash
    git config --global core.autocrlf input
    ```
- Add initial files to the staging area
    ```bash
    git add .
    ```
- Make initial commit
    ```bash
    git commit -m "Initial commit"
    ```
- Sign-in to GitHub and [create a remote repository](https://github.com/new). Then, add it as the origin for your local repository. Note that `github-default-ssh-profile` must correspond to the name of the an SSH profile entry you added in `~/.ssh/config` file.
    ```bash
    git remote add origin github-default-ssh-profile:<username>/repository.git
    ```
- Verify if remote repository is added properly
    ```bash
    git remote -v 
    ```
- Push initial commit to the remote repository. Only use `git push -u` on first push, subsequent push should only be done with `git push` without flags.
    ```bash
    git push -u origin master
    ```
- Finished! You successfully setup a new git repository for your new project.

[[Go back]](#table-of-contents)

## Basic Commands
Here are some of the commonly used commands for git.

### Initialize git repository
```bash
git init
```
[[Go back]](#table-of-contents)
### Get current status
```bash
git status
```
[[Go back]](#table-of-contents)
### Add files to staging
```bash
git add .
git add <filename>
```
[[Go back]](#table-of-contents)
### Remove files from staging
```bash
git reset HEAD .
git reset HEAD <filename>
```
[[Go back]](#table-of-contents)
### Commit files in staging
```bash
git commit -m "<message>"
```
[[Go back]](#table-of-contents)
### Download commits from remote repository
```bash
git pull origin <branch>
```
[[Go back]](#table-of-contents)
### Upload commits to remote repository
```bash
git push origin <branch>
```
[[Go back]](#table-of-contents)
### Make a new branch and switch to it
```bash
git checkout -b <branch>
```
[[Go back]](#table-of-contents)
### List all existing branches
```bash
git branch -a
```
[[Go back]](#table-of-contents)
### Delete branch
```bash
git branch -d <branch>
```
[[Go back]](#table-of-contents)
### Push branch to origin on first create
```bash
git push -u origin <branch>
```
[[Go back]](#table-of-contents)
### Merge a branch to another
```bash
git checkout <destination_branch>
git merge <source_branch>
```
[[Go back]](#table-of-contents)
### Resolve merge conflicts
```bash
git add .
git add <confict_files>
git commit -m "Merged commit to master"
```
[[Go back]](#table-of-contents)
### Abort merge
```bash
git merge --abort
```
[[Go back]](#table-of-contents)
###  Discard uncommited changes in working directory
```bash
git checkout -- .
git checkout -- <filename>
```
[[Go back]](#table-of-contents)
### List all commits in current branch
```bash
git log
git log --graph --oneline --decorate --all
```
[[Go back]](#table-of-contents)
### Add tags 
```bash
git tag -a <version>  -m <tag_message>
git push --tags
```
[[Go back]](#table-of-contents)
### Remove last commit
```bash
git reset HEAD~
```
[[Go back]](#table-of-contents)