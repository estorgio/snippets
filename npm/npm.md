[[Return to Index]](../README.md)

# NPM Cheat Sheet
This is a guide for some of the commonly used commands in `npm`.

## Table of Contents
- [Display help](#display-help)
- [Initialize](#initialize)
  - [Initialize `package.json`](#initialize-package.json)
  - [Initialize `package.json` with defaults](#initialize-package.json-with-defaults)
- [Default configuration](#default-configuration)
  - [List configs](#list-configs)
  - [Change author name and license](#change-author-name-and-license)
  - [Alias to npm config set](#alias-to-npm-config-set)
  - [Delete defaults](#delete-defaults)
- [Packages](#packages)
  - [Install package](#install-package)
  - [Install dev package](#install-dev-package)
  - [Install packages globally](#install-packages-globally)
  - [Install specific version of a package](#install-specific-version-of-a-package)
  - [Install dependencies](#install-dependencies)
  - [Install dependencies for production](#install-dependencies-for-production)
  - [List packages](#list-packages)
  - [List packages at particular depth](#list-packages-at-particular-depth)
  - [List outdated packages](#list-outdated-packages)
  - [Update package](#update-package)
  - [Remove package](#remove-package)
  - [Global packages directory](#global-packages-directory)
- [NPM Scripts](#npm-scripts)

## Display Help
```bash
npm help
```

[[Go back]](#table-of-contents)

## Initialize
### Initialize `package.json`
```bash
npm init
```

### Initialize `package.json` with defaults
```bash
npm init -y
npm init --yes
```

[[Go back]](#table-of-contents)

## Default Configuration
### List configs
```bash
npm config get
npm config get <field>
```
### Change author name and license
```bash
npm config set init-author-name "John Doe"
npm config set init-license "MIT"
```
### Alias to `npm config set`
```bash
npm set
```
### Delete defaults
```bash
npm config delete <field>
```

[[Go back]](#table-of-contents)

## Packages
### Install package
```bash
npm i <package>
npm install --save <package>
```
[[Go back]](#table-of-contents)
### Install dev package
```bash
npm i -D <package>
npm install --save-dev <package>
```
[[Go back]](#table-of-contents)
### Install packages globally
```bash
npm i -g <package>
npm install --global <package>
```
[[Go back]](#table-of-contents)
### Install specific version of a package
```bash
npm i <package>@1.2.3
npm install <package>@1.2.3
```
[[Go back]](#table-of-contents)
### Install dependencies
```bash
npm i
npm install
```
[[Go back]](#table-of-contents)
### Install dependencies for production
```bash
npm i --production
npm install -- production
```
[[Go back]](#table-of-contents)
### List packages
```bash
npm list
```
[[Go back]](#table-of-contents)
### List packages at particular depth
```bash
npm list --depth <number>
```
[[Go back]](#table-of-contents)
### List outdated packages
```bash
npm outdated
```
[[Go back]](#table-of-contents)
### Update package
```bash
npm update <package>
```
[[Go back]](#table-of-contents)
### Remove package
```bash
npm un <package> 
npm rm <package> 
npm uninstall <package> 
npm remove <package>
```
[[Go back]](#table-of-contents)
### Global packages directory
```bash
npm root -g
```
[[Go back]](#table-of-contents)

## NPM Scripts
Sample `scripts` section of a `package.json` file.
```json
"scripts": {
  "server": "live-server",
  "<scriptname>": "<scriptcommand>"
}
```
To run NPM scripts above
```bash
npm run server
npm run <scriptname>
```
[[Go back]](#table-of-contents)
