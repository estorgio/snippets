[[Return to Index]](../README.md)

# Git

## Table of Contents
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
- Add initial files to the staging area
    ```bash
    git add .
    ```
- Make initial commit
    ```bash
    git commit -m "Initial commit"
    ```
- Sign-in to GitHub and [create a remote repository](https://github.com/new). Then, add it as the origin for your local repository.
    ```bash
    git remote add origin git@github.com:<username>/repository.git
    ```
- Verify if remote repository is added properly
    ```bash
    git remote -v 
    ```
- Generate SSH keys if you don't have one
    ```bash
    ssh-keygen -t rsa -b 4096 -f "<username-here>@github.com.keyfile"
    ```
- Launch SSH agent. You have to do this every time you open a new terminal window.
    ```bash
    eval $(ssh-agent -s)
    ssh-add
    ssh-add "<username-here>@github.com.keyfile"
    ```
- Copy public key and paste it on [GitHub -> Settings -> SSH and GPG keys](https://github.com/settings/keys)
    ```bash
    clip < "<username-here>@github.com.keyfile"
    ```
- Test connection to remote GitHub server
    ```bash
    ssh -T git@github.com
    ```
- Push initial commit to the remote repository. Only use `git push -f -u` on first push, subsequent push should only be done with `git push` without flags.
    ```bash
    git push -f -u origin master
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