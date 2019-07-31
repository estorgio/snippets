[[Return to Index]](../README.md)

# MongoDB Basics
Important stuff to know about MongoDB

## Table of Contents
- [Basic operations](#basic-operations)
  - [`show dbs`]()
  - [`use <dbname>`]()
  - [`show collections`]()
  - [`find`]()
  - [`findOne`]()
  - [`insertOne`]()
  - [`insertMany`]()
  - [`updateOne`]()
  - [`updateMany`]()
  - [`replaceOne`]()
  - [`deleteOne`]()
  - [`deleteMany`]()

## Basic operations

### `show dbs`
Display a list of databases in the server.

### `use <dbname>`
Selects the current working database.

### `show collections`
Shows a list of collections in the current working database.

### `find(filter, options)`
Returns all matching documents in a collection.

### `findOne(filter, options)`
Returns the first matching document in a collection.

### `insertOne(document, options)`
Inserts a single document in a collection.

### `insertMany(documents, options)`
Inserts multiple documents in a collection.

### `updateOne(filter, data, options)`
Updates the first matching document in a collection.

### `updateMany(filter, data, options)`
Updates all matching documents in a collection.

### `replaceOne(filter, data, options)`
Overwrites the first matching document in a collection with new data.

### `deleteOne(filter, options)`
Deletes the first matching document in a collection.

### `deleteMany(filter, options)`
Deletes all matching documents in a collection.