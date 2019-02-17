[[Return to Index]](../README.md)

# Heroku Deployment Basics
Common Heroku commands for deploying applications.

## Table of Contents
- [Getting Started](#getting-started)
- [Environment Variables](#environment-variables)
  - [Development Setup](#development-setup)
  - [Production Setup](#production-setup)
- [Custom Domain](#custom-domain)
- [View Logs](#view-logs)
- [Run App on Development](#run-app-on-development)

## Getting Started
- Initialize git repository
  ```bash
  git init
  ```
- Create `.gitignore` file and add files/directories to exclude
  ```bash
  echo "node_modules/" >> .gitignore
  echo "*.env" >> .gitignore
  ```
- Create Heroku `Procfile`
  ```bash
  echo "web: node index.js" >> Procfile
  ```
- Add all files to the staging area
  ```bash
  git add .
  ```
- Commit all files
  ```bash
  git commit -m "My first deployment"
  ```
- Create Heroku dyno
  ```bash
  heroku create <appname>
  ```
- Push commit to the Heroku server for deployment
  ```bash
  git push heroku master
  ```
- Open app in the browser
  ```bash
  heroku open
  ```
Deployment complete! Congratulations, you have successfully deployed an app to Heroku.

[[Go back]](#table-of-contents)

## Environment Variables
### Development Setup
Create `.env` file for storing environment variables on development
```bash
echo "MYVAR=my value here" >> .env
```
### Production Setup
Set environment variables in remote server
```bash
heroku config:set MYVAR=newvalue
```

[[Go back]](#table-of-contents)

## Custom Domain
- Add custom domain
  ```bash
  heroku domains:add my-app.estorgio.app
  ```
- Get the DNS target and add it as CNAME on your DNS record
  ```bash
  heroku domains
  ```

[[Go back]](#table-of-contents)

## View Logs
Inspect application logs for debugging and troubleshooting purposes.
```bash
heroku logs --tail
```
[[Go back]](#table-of-contents)

## Run App on Development
Launch your app locally.
```bash
heroku local
```
[[Go back]](#table-of-contents)