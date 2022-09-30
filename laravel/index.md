[[Return to Index]](../README.md)

# Laravel Guide
This guide will walk you through the basics of Laravel 9.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Common directories and files](#common-directories-and-files)

## Prerequisites
Before proceeding, please make sure you have `composer` installed on your system.
- [Download Composer](https://getcomposer.org/download/)

[[Go back]](#table-of-contents)

## Installation
To create a new Laravel project, open the terminal and run the `composer create-project` command
```bash
# Replace MyNewlaravelProject with your project's name
$ composer create-project laravel/laravel MyNewLaravelProject
```
[[Go back]](#table-of-contents)

## Common directories and files
Here are some of the commonly used directories and files paths
```bash
# Routes
$ code routes/web.php

# Models
$ cd app/Models

# Controllers
$ cd app/Http/Controllers

# Views
$ cd resources/views

# Component-based views
$ cd resources/views/components

# View partials
$ cd resources/views/partials

# Database migrations
$ cd database/migrations

# Database seeders
$ cd database/seeders

# Factories for seeders
$ code database/factories/DatabaseSeeder.php

# Public directory for Apache
$ cd public/

# Storage for uploaded files
$ cd storage/app/public

# Uploaded files directory symbolic linked in public
$ cd public/storage
```
[[Go back]](#table-of-contents)