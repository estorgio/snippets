[[Return to Index]](../README.md)

# Laravel Guide
This guide will walk you through the basics of Laravel 9.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Common directories and files](#common-directories-and-files)
- [Routing](#routing)
  - [Router Methods](#router-methods)
  - [Common Resource Routes](#common-resource-routes)
  - [Router Parameter Constraints](#router-parameter-constraints)
  - [Fallback Route](#fallback-route)
  - [Route Groups](#route-groups)

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

## Routing
To add routes, simply open and edit `routes/web.php` file. Here are some sample routes:
```PHP
// Show hello world
Route::get('/', function () {
    return 'Hello world';
});


// Subdirectory
Route::get('/books', function () {
    return 'This is books directory';
});


// Display a view
Route::get('/', function () {
    return view('welcome');
});

// Display a view with status code
Route::get('/', function () {
    return response()
      ->view('welcome', [], 404);
});


// For views inside directories, use dot notation
Route::get('/books', function () {
    return view('books.show');  // resources/views/books/show.blade.php
});


// Using controllers for routes
Route::get('/', [SampleController::class, 'methodname']);


// Specifying route parameters with curly braces
Route::get('/books/{id}', [BooksController::class, 'show']);


// Multiple route parameters
Route::get('/books/{bookname}/chapter/{chapter}', 
  function ($bookname, $chapter) {
    return 'Book name: ' . $bookname . '<br>' . 'Chapter: ' . $chapter;
  });


// Routes only accessible for authenticated users
// using middleware('auth')
Route::post('/sensitive', [SenstiveController::class, 'show'])
  ->middleware('auth');


// Routes only accessible for guess (non-authenticated) users
Route::get('/login', [UserController::class, 'login'])
  ->name('login')
  ->middleware('guest');
```
[[Go back]](#table-of-contents)

### Common Resource Routes
Here are some conventions when designing resource routes.
- `index` - list all items
- `show` - show single item
- `create` - display form to add new item
- `store` - receives data from `create` and stores it in the database
- `edit` - display form to edit existing item
- `update` - receives data from `edit` and saves changes to the database
- `destroy` - delete item 

[[Go back]](#table-of-contents)

### Router Methods
Here are some available router methods.
```php
Route::get($uri, $callback);
Route::post($uri, $callback);
Route::put($uri, $callback);
Route::patch($uri, $callback);
Route::delete($uri, $callback);
Route::options($uri, $callback);
```
[[Go back]](#table-of-contents)

### Router Parameter Constraints
You can apply restrictions as to what value can be passed in router parameters by using constraints.
```php
// Using RegEx
Route::get('/user/{name}', function ($name) {
  })->where('name', '[A-Za-z]+');


// Using helper methods
Route::get('/user/{id}/{name}', function ($id, $name) {
  })
  ->whereNumber('id')
  ->whereAlpha('name');

// Another helper
Route::get('/test/{value}', function ($value) {
  })
  ->whereIn('value', ['true', 'false']);
```
Available helper methods:
  - `whereNumber($param)` - only numbers
  - `whereAlpha($param)` - only letters
  - `whereAlphaNumeric($param)` - numbers and letters
  - `whereIn($param)` - selected values

[[Go back]](#table-of-contents)

### Fallback Route
This route will execute when no other routes matched. Should only be placed at the end of the `routes/web.php` file.
```php
Route::fallback(function () {
    return response('This is a sample 404 page', 404);
});
```
[[Go back]](#table-of-contents)

### Route Groups
Route groups are a great way to organize your routes and improve code readability.
```php
// Group routes by controller
Route::controller(BookController::class)
  ->group(function () {
      Route::get('/books', 'index');
      Route::post('/books/{id}', 'show');
  });


// Route prefixes
Route::prefix('books')
  ->group(function () {
      Route::get('/{id}', function () {
          // Matches The "/books/{id}" url
      });
      Route::get('/create', function () {
          // Matches The "/books/create" url
      });
  });
```
[[Go back]](#table-of-contents)