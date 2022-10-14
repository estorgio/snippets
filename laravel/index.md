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
- [Controllers](#controllers)
  - [Creating Controllers](#creating-controllers)
  - [Controller Methods](#controller-methods)
  - [Getting Input From User](#getting-input-from-user)
- [Views](#views)
  - [Loading Views](#loading-views)
  - [Accessing Data in Views](#accessing-data-in-views)
  - [Get Asset URL](#get-asset-url)
  - [Partials](#partials)
  - [Components](#components)
  - [Component With Slots](#component-with-slots)
  - [Additional Blade Directives](#additional-blade-directives)
- [Models](#models)
  - [Creating Model](#creating-model)
  - [Setting Up Migration](#setting-up-migration)
  - [Factory](#factory)
  - [Fillable Attributes](#fillable-attributes)
  - [Enable Soft Delete](#enable-soft-delete)
- [File upload](#file-upload)

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

## Controllers
Controllers are classes that implements the logic of the application. All controllers are located at `app/Http/Controllers` directory.

### Creating Controllers
To create a new controller, use the following command:
```bash
# By convention, all controllers must be a singular noun (without 's') 
# and should have "Controller" postfix (ex. BookController, 
# UserController, etc.)
$ php artisan make:controller SampleController
```
A new controller should be generated in `apps/Http/Controllers` directory. Here is a sample boilerplate code for a newly-generated controller:
```php
<?php
namespace App\Http\Controllers;
use Illuminate\Http\Request;

class SampleController extends Controller
{
    //
}
```
[[Go back]](#table-of-contents)

### Controller Methods
All the code inside controllers are organized into methods. Each of these methods perform a specific operation. Most of these operations are similar to the ones listed in [Common Resource Routes](#common-resource-routes) section.

For now, we will display a sample `Hello World` text.
```php
class SampleController extends Controller
{
    public function index()
    {
        return 'Hello world!';
    }
}
```

To make this controller method accessible, edit the `routes/web.php` and add a route for our method.
```php
// Inside `routes/web.php` file
Route::get('/samples', [SampleController::class, 'index']);
```

The route method should now be accessible at `http://localhost/samples` directory
```
Hello world!
```
[[Go back]](#table-of-contents)

### Getting Input From User
There are times that you want to retrieve data from a form in a POST request or a GET url query such as `/?search=apples`. To accomplish this, use `request()` helper function.
```php
class SampleController extends Controller
{
    public function index()
    {
        $query = request(['name', 'age']);
        return "name: " . $query['name'] . ', age: ' . $query['age'];
    }
}
```
You can also use dependency injection to retrieve data from query string.
```php
use Illuminate\Http\Request;

class SampleController extends Controller
{
    public function index(Request $request)
    {
        return "name: " . $request->name . ', age: ' . $request->age;
    }
}
```
URL:
```
http://localhost/samples?name=Bob&age=21
```
Output:
```
name: Bob, age: 21
```
[[Go back]](#table-of-contents)

## Views
### Loading Views
You can load views in Laravel using the `view()` method, with the variables passed on as associative array on the second argument. 
```php
class ProductController extends Controller {
  public function index() {
    // Load 'resources/views/contacts/index.blade.php
    return view('contacts.index', [
      'name' => 'John Doe',
      'contact' => '012345678'
    ])
  }
}
```
[[Go back]](#table-of-contents)

### Accessing Data in Views
To access or print variables passed in the view, use `{{ }}` double curly braces.
```html
<div>Hello, {{ $name }}</div>
```
[[Go back]](#table-of-contents)

### Get Asset URL
To get a link to your assets in public folder, use `asset()`.
```html
<link rel="stylesheet" href="{{ asset('assets/css/styles.css') }}">
```
[[Go back]](#table-of-contents)


### Partials
To insert other views into the current view, use `@include` Blade directive.
```php
@include('_books.index')
```
[[Go back]](#table-of-contents)

### Components
Components are similar to partials but are more sophisticated as you can pass values into them. You can also use them like HTML tags in Blade templates and Laravel will render them properly.

Sample component:
```html
{{ -- 'resources/views/components/customer-info.blade.php' -- }}
@props(['customer'])

<p>Name: {{ $customer->name }}</p><br>
<p>Age: {{ $customer->age }}</p><br>
<p>Address: {{ $customer->address }}</p><br>
```

Using component in another view:
```html
{{ -- 'resources/views/index.blade.php' -- }}
<x-customer-info :customer="$new_customer" />
```
[[Go back]](#table-of-contents)

### Component With Slots
You can also use components like HTML tags and have them output content inside them using `{{ $slot }}` statement. To pass named slots to components, use `<x-slot:myvarname>`.
```html
{{ -- 'resources/views/components/layout.blade.php' -- }}
<html>
  <head>
    <title>Bookmark - {{ $title }}</title>
  </head>
  <body>
    {{ $slot }}
  </body>
</html>
```
```html
<x-layout>
  <x-slot:title>
    Dashboard
  </x-slot>

  <div>All content goes from here.</div>
</x-layout>
```
[[Go back]](#table-of-contents)

### Additional Blade Directives
```php
// Add CSRF token field inside forms
@csrf


// Submitting form with PUT or DELETE action
@method('PUT')
@method('DELETE')


// Displaying validation errors in each form fields
@error('fieldname')
<div class="error-message">{{ $message }}</div>
@enderror


// Loop through arrays
@foreach($items as $item)
  <div>{{ $item->name }}</div>
@endforeach


// Loops through arrays but also display message if empty
@forelse($items as $item)
  <div>{{ $item->name }}</div>
@empty
  <div>There are no items yet!</div>
@endforelse
```
[[Go back]](#table-of-contents)

## Models
### Creating Model
```bash
# Create new model, factory, and seeder
$ php artisan make:model Product -mfs
```
[[Go back]](#table-of-contents)

### Setting Up Migration
Create database schema with migrations. Here you can specify the table attributes as well as their data types.
```php
# database/migrations/2022_10_07_034344_create_products_table.php
return new class extends Migration {
  public function up() {
    Schema::create('products', function (Blueprint $table) {
        $table->id();
        $table->string('name');
        $table->decimal('price', 9, 2);
        $table->integer('quantity');
        $table->string('barcode')->unique();
        $table->timestamps();
        $table->softDeletes();
    });
  }
}
```
[[Go back]](#table-of-contents)

### Factory
Factories are used to generate dummy data.
```php
# database/factories/ProductFactory.php
class ProductFactory extends Factory {
    public function definition() {
        return [
            'name' => fake()->words(2, true),
            'price' => fake()->randomFloat(2, 1, 300),
            'quantity' => fake()->randomNumber(2),
            'barcode' => fake()->unique()->randomNumber(8, true),
          ];
    }
}
```
[[Go back]](#table-of-contents)

### Fillable Attributes
In your model, specify which attributes can be mass-assigned during insert operations.
```php
# app/Models/Product.php
class Product extends Model {
  protected $fillable = ['name', 'price', 'quantity', 'barcode'];
  ...
}
```
[[Go back]](#table-of-contents)

### Enable Soft Delete
Soft deletes allows you to mark deleted items without physically deleting records in the database.
```php
# database/migrations/2022_10_07_034344_create_products_table.php
return new class extends Migration {
  public function up() {
    Schema::create('products', function (Blueprint $table) {
        ...
        $table->softDeletes(); # Adds deleted_at attribute
    });
  }
}
```
```php
# app/Models/Product.php
class Product extends Model {
  use HasFactory, SoftDeletes;  # Insert SoftDeletes trait here
}

```
[[Go back]](#table-of-contents)

## File Upload
  - Edit `.env` config file and change the `FILESYSTEM_DISK`
    ```
    FILESYSTEM_DISK=public
    ```
  - Add symbolic link in public directory
    ```bash
    $ php artisan storage:link
    ```
  - In the view, change the form's `enctype` value to `multipart/form-data`
    ```html
    <form action="/products" method="POST" enctype="multipart/form-data">
    ```
  - Add file upload field in the form
    ```html
    <div class="form-group @error('image') has-danger @enderror">
      <label for="image" class="form-label mt-4">Product Image</label>
      <input type="file" class="form-control @error('image') is-invalid @enderror" name="image">
      @error('image')
        <div class="invalid-feedback">{{ $message }}</div>
      @enderror
    </div>
    ```
  - Accept file on the controller
    ```php
    if ($request->hasFile('image')) {
      $formFields['image'] = $request->file('image')->store('images');
    }
    ```
[[Go back]](#table-of-contents)