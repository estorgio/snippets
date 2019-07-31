[[Return to Index]](../README.md)

# Golang Tutorial
This is a short guide on Golang

## Table of Contents
- [Setting up Development Environment](#setting-up-development-environment)
- [Basic Hello World app](#basic-hello-world-app)
- [Initialize](#initialize)
  - [Initialize `package.json`](#initialize-package.json)
  - [Initialize `package.json` with defaults](#initialize-package.json-with-defaults)

## Setting up Development Environment
- Download and install the [Golang compiler](https://golang.org/dl/)
- Set up workspace directory
  ```
  /go
    /bin
    /pkg
    /src
      /github.com
        /YourUsername
          /project1
          /project2
          /project3
  ```
- Set up environment variables
  ```bash
  # Path to Go workspace
  export GOPATH=/c/Users/YourName/go
  export PATH=$PATH:/c/Users/YourName/go/bin
  ```
- Install [Go extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.Go) for VSCode.

[[Go back]](#table-of-contents)

## Basic Hello World app
- File `main.go`
  ```golang
  package main

  import "fmt"

  func main() {
    fmt.Println("Hello world")
  }
  ```
- Run the code
  ```bash
  $ go run main.go
  Hello world
  ```

[[Go back]](#table-of-contents)