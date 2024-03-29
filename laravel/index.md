[[Return to Index]](../README.md)

# Laravel Guide
This guide will walk you through the basics of Laravel 9.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Installation](#installation)
  - [Upgrade](#upgrade)
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
  - [Custom Blade Directives](#custom-blade-directives)
- [Models](#models)
  - [Creating Model](#creating-model)
  - [Setting Up Migration](#setting-up-migration)
  - [Factory](#factory)
  - [Fillable Attributes](#fillable-attributes)
  - [Enable Soft Delete](#enable-soft-delete)
  - [Scopes](#scopes)
- [File upload](#file-upload)
- [Form Validation](#form-validation)
  - [Validating in Controllers](#validating-in-controllers)
  - [Validation with FormRequest Class](#validation-with-formrequest-class)
  - [Displaying Validation Errors](#displaying-validation-errors)
- [Authentication](#authentication)
  - [Sign Up](#sign-up)
  - [Log In](#log-in)
  - [Log Out](#log-out)
  - [Remember Me](#remember-me)
  - [Blade Directives for Authentication](#blade-directives-for-authentication)
  - [Email Verification](#email-verification)
- [Console](#console)
  - [Creating a New Command](#creating-a-new-command)
  - [Editing the Command](#editing-the-command)
  - [Running the Command](#running-the-command)
- [Setting up reCAPTCHA](#setting-up-recaptcha)

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

### Upgrade
To upgrade an existing Laravel project or any Composer dependencies for that matter, run the following command
```bash
$ composer update
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

### Custom Blade Directives
Laravel allows you to specify your own custom directives. To do so you may call the `Blade::directive()` method inside the `AppServiceProvider.php`.
```php
// app/Providers/AppServiceProvider.php
namespace App\Providers;

class AppServiceProvider extends ServiceProvider {
  public function boot() {
    Blade::directive('format_time', function ($expression) {
      return "<?php echo date('F j, Y - g:i A', strtotime($expression)) ; ?>";
    });
  }
}
```
To use the custom directive we just made, prefix the name with an at sign (@) just like you would with regular Blade directives.
```html
<div class="row mb-2">
    <div class="col"><strong>Date added:</strong></div>
    <div class="col">@format_time($product->created_at)</div>
</div>
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

### Scopes
Scopes allows you to encapsulate queries in a method, making the code more readable and reusable.
```php
//app/Models/Product.php
class Product extends Model {

  public function scopeSort($query, array $sort) {
    $field = $sort['field'] ?? 'created_at';
    $order = $sort['order'] ?? 'desc';
    $query->orderBy($field, $order);
  }
}
```
```php
// Sample usage in controller
$products = Product::latest()
            ->sort(['field' => 'name', 'order' => 'desc']);
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

## Form Validation
Laravel provides some options when it comes to validating form content.

### Validating in Controllers
To perform validation on controllers, add `Request` as a dependency on the method and use the `validate()`. From there, you can pass an associative array containing the fields with their corresponding validation rule.
```php
// app/Http/Controllers/UserController.php
use Illuminate\Http\Request;

class UserController extends Controller {
  public function store(Request $request){
    $formFields = $request->validate([
        'username' => 'required|min:4|unique:users,username',
        'email' => 'required|email|unique:users,email',
        'password' => 'required|confirmed|min:8',
    ]);
    // $formFields can now be used, say to be stored in db
  }
}
```
[[Go back]](#table-of-contents)

### Validation with FormRequest Class
Alternatively, you may also use a separate class for form validation. In this case, you can use `FormRequest` class. To create one, use the following command:
```bash
$ php artisan make:request UserRequest
```
A new `FormRequest` class will be created on `app\Http\Requests` director. You can now place you validation rules inside the `rules()` method. 

Also, do not forget to set the return value for `authorize()` to `true`.
```php
namespace App\Http\Requests;
use Illuminate\Foundation\Http\FormRequest;

class UserRequest extends FormRequest {
  public function authorize(){
    return true;
  }
  public function rules() {
    return [
      'username' => 'required|min:4|unique:users,username',
      'email' => 'required|email|unique:users,email',
      'password' => 'required|confirmed|min:8',
    ];
  }
}

```
To use this class, simply replace the `Request` on your controller method's parameter to the name of your class. In this example, it's `UserRequest`. After that, change the `validate()` method call to `validated()` to run the validation rules on our `FormRequest` class.
```php
public function store(UserRequest $request) {
  $formFields = $request->validated();
}
```
[[Go back]](#table-of-contents)

### Displaying Validation Errors
To show validation errors, in the view where the form is to be submitted from, add `@error('fieldname')` Blade directive for each form field. Inside, use `{{ $message }}` to print out the validation error. You can also choose to display previous values by calling `old('fieldname')` method.
```html
<form method="POST" action="/products">
  <div class="form-group">
    <label for="product_name">Product name:</label>
    <input type="text" name="product_name" value="{{ old('product_name') }}">
    @error('product_name')
    <div class="invalid-feedback">{{ $message }}</div>
    @enderror
  </div>
</form>
```
[[Go back]](#table-of-contents)

## Authentication

### Sign Up
```php
public function store(Request $request) {
  $formFields = $request->validate([
    'username' => 'required|min:4|unique:users,username',
    'email' => 'required|email|unique:users,email',
    'password' => 'required|confirmed|min:8',
  ]);

  $formFields['password'] = Hash::make($formFields['password']);

  $user = User::create($formFields);

  auth()->login($user);

  return redirect('/')->with('message', 'Welcome, ' . $user->username);
}
```
[[Go back]](#table-of-contents)

### Log In
```php
public function authenticate(Request $request) {
  $formFields = $request->validate([
    'username' => 'required',
    'password' => 'required',
  ]);

  if (auth()->attempt($formFields)) {
    $request->session()->regenerate();
    return redirect('/')->with('message', 'Welcome back, ' . auth()->user()->username);
  }

  return back()
    ->withErrors(['password' => 'Invalid username or password'])
    ->onlyInput('username');
}
```
[[Go back]](#table-of-contents)

### Log Out
```php
public function logout(Request $request) {
  auth()->logout();
  $request->session()->invalidate();
  $request->session()->regenerateToken();

  return redirect('/login')->with('message', 'You have been logged out.');
}
```
[[Go back]](#table-of-contents)

### Remember Me
```php
// Controller
$remember = $request->has('remember_me');

if (auth()->attempt($formFields, $remember)) {
  $request->session()->regenerate();
  return redirect('/')->with('message', 'Welcome back, ' . auth()->user()->username);
}
```
```php
// Migration
public function up() {
  Schema::create('users', function (Blueprint $table) {
    $table->rememberToken();
  });
}
```
[[Go back]](#table-of-contents)

### Blade Directives for Authentication
```php
@auth
  <p>You are logged in as {{ auth()->user()->username }}</p>
@else
  <p>You are not logged in.</p>
@endauth
```
[[Go back]](#table-of-contents)

### Email Verification
In `routes/web.php`, add the following routes.
```php
Route::get('/verify-account', [UserController::class, 'require_verification'])
  ->middleware('auth')
  ->name('verification.notice');

Route::get('/verify-account/{id}/{hash}', [UserController::class, 'verify_account'])
  ->middleware(['auth', 'signed'])
  ->name('verification.verify');
```
In `app/Http/Controllers/UserController.php`, add the following controller methods.
```php
public function require_verification() {
  return redirect('/');
}

public function verify_account(EmailVerificationRequest $request) {
  $request->fulfill();
  return redirect('/')
    ->with('message', 'Your email has been successfully verified.');
}
```
In `app/Models/User.php`, add the `MustVerifyEmail` interface to the `User` class.
```php
namespace App\Models;
use Illuminate\Contracts\Auth\MustVerifyEmail;

class User extends Authenticatable implements MustVerifyEmail {
  ...
}
```
In `app/Providers/AuthServiceProvider.php`, inside the `boot()` method, specify our custom `Mailable` class to be used for email verification. In this case, it's `EmailVerification`.
```php
class AuthServiceProvider extends ServiceProvider {
  public function boot() {
    // Custom mailable for email verification
    VerifyEmail::toMailUsing(function ($notifiable, $url) {
      return (new EmailVerification($url))
        ->to($notifiable->email);
    });
  }
}
```
Create `EmailVerification` class using `artisan` command.
```bash
$ php artisan make:mail EmailVerification
```
In `app/Mail/EmailVerification.php`, add the following code for the methods.
```php
class EmailVerification extends Mailable {
  // Contains laravel-generated verification link
  public $verify_url;

  public function __construct($verify_url) {
    $this->verify_url = $verify_url;
  }

  public function envelope() {
    return new Envelope(
      subject: 'Verify your email',
    );
  }

  public function content() {
    // Specify which Blade view to use for email content, in this
    // case, it's `resources/views/emails/verify.blade.php`
    return new Content(
      view: 'emails.verify',
    );
  }
}
```
Create `resources/views/emails/verify.blade.php` and add the contents of the email. Note that `$verify_url` corresponds to the public `$verify_url` property in our `EmailVerification` class as all of its public properties are accessible within the Blade view.
```php
<p>Hi,</p>
<p>To verify your account, please use the following link.</p>
<p><a href="{{ $verify_url }}">{{ $verify_url }}</a></p>
<p>Regards,<br>Webmaster</p>
```
Finally, in `app/Http/Controllers/UserController.php` fire the `Registered` event to initiate the email sending process during the sign up process.
```php
use Illuminate\Auth\Events\Registered;

class UserController extends Controller {
  public function store(UserRequest $request){
    $formFields = $request->validated();
    $formFields['password'] = Hash::make($formFields['password']);

    $user = User::create($formFields);

    // Fire the event to initiate the email sending process
    event(new Registered($user));

    auth()->login($user);

    return redirect('/')->with('message', 'Welcome, ' . $user->username);
    return redirect('/');
  }
}
```
[[Go back]](#table-of-contents)


## Console
### Creating a New Command
Laravel allows you to create your own custom artisan commands. To do so, you can type the following command in the terminal:
```bash
$ php artisan make:command HelloWorld
```
[[Go back]](#table-of-contents)

### Editing the Command
All commands created using `make:command` will be placed in `app/Console/Commands` directory. Here is an example `HelloWorld` command we just created.
```php
use Illuminate\Console\Command;

class HelloWorld extends Command {
  protected $signature = 'hello:world';
  protected $description = 'Displays hello world message';

  public function handle() {
    $this->info('Hello World!');
    return Command::SUCCESS;
  }
}
```
[[Go back]](#table-of-contents)

### Running the Command
To run the command we just created, type the following in the terminal:
```bash
$ php artisan hello:world
```
[[Go back]](#table-of-contents)

## Setting up reCAPTCHA
Create `config/recaptcha.php` configuration file.
```php
<?php
return [
    'site_key' => env('RECAPTCHA_SITE_KEY', null),
    'secret_key' => env('RECAPTCHA_SECRET_KEY', null),
    'theme' => env('RECAPTCHA_THEME', 'light'),
];
```
Edit `.env` file and paste in your reCAPTCHA site key and secret key.
```bash
RECAPTCHA_SITE_KEY=""
RECAPTCHA_SECRET_KEY=""
RECAPTCHA_THEME="light"
```
Create a new custom rule class for reCAPTCHA validation.
```bash
$ php artisan make:rule RecaptchaValidate --invokable
```
Use the following implementation for the `__invoke()` method.
```php
<?php
namespace App\Rules;

use Illuminate\Support\Facades\Http;
use Illuminate\Contracts\Validation\InvokableRule;

class RecaptchaValidate implements InvokableRule
{
  public function __invoke($attribute, $value, $fail)
  {
    $response = Http::asForm()->post('https://www.google.com/recaptcha/api/siteverify', [
      'secret' => config('recaptcha.secret_key'),
      'response' => $value,
      'remoteip' => request()->ip(),
    ]);

    $error = $response->json('error-codes');

    if ($error) {
      if (
        in_array('missing-input-response', $error) ||
        in_array('invalid-input-response', $error)
      ) {
        $fail('Please solve the ReCAPTCHA challenge.');
      } else if (
        in_array('missing-input-secret', $error) ||
        in_array('invalid-input-secret', $error)
      ) {
        $fail('The ReCAPTCHA secret key is either missing or invalid.');
      } else if (in_array('bad-request', $error)) {
        $fail('Unable to validate the ReCAPTCHA challenge.');
      } else if (in_array('timeout-or-duplicate', $error)) {
        $fail('The ReCAPTCHA challenge has expired, please try again.');
      }
    } else if (!$response->json('success')) {
      $fail('The ReCAPTCHA challange has failed. Please try again.');
    }
  }
}
```
To be able to validate the reCAPTCHA attempt from the end user, apply our custom rule class `RecaptchaValidate` to the `g-recaptcha-respose` field that was sent from the form.
```php
$request->validate([
  'g-recaptcha-response' => new RecaptchaValidate(),
]);
```
Edit `app/Providers/AppServiceProvider.php` and add our custom Blade directives.
```php
class AppServiceProvider extends ServiceProvider {
  public function boot() {
    ...
    $this->load_recaptcha_directives();
  }

  private function load_recaptcha_directives(){
    Blade::directive('recaptcha_script', function () {
      return '<script src="https://www.google.com/recaptcha/api.js" async defer></script>';
    });

    Blade::directive('recaptcha_field', function () {
      return '<div class="g-recaptcha" data-sitekey="' . config('recaptcha.site_key') . '" ' .
          'data-theme="' . config('recaptcha.theme') . '"></div>';
    });
  }
}
```
Add `@recaptcha_script` custom directive at the `<head>` of the view.
```html
<!DOCTYPE html>
<html lang="en">
<head>
  ...
  @recaptcha_script
</head>
<body>
  ...
</body>
</html>
```
Finally, to render the reCAPTCHA challenge inside your forms, simply use `@recaptcha_field`.
```html
<form method="POST" action="/register">
  @csrf
  <input type="text" name="username">
  <input type="password" name="password">
  @recaptcha_field
  <button type="submit">Register</button>
</form>
```
[[Go back]](#table-of-contents)