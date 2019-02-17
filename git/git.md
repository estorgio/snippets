[[Return to Index]](../README.md)

# Git

## Table of Contents
- [Getting Started](#getting-started)
- [Basic Commands](#basic-commands)


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
TODO: Add Basic Commands

[[Go back]](#table-of-contents)