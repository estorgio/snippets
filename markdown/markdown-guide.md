[[Return to Index]](../README.md)

# Markdown Guide
This document serves as a quick guide to Markdown syntax.

## Table of Contents
- [Heading](#heading)
- [Blockquote](#blockquote)
- [Text Formatting](#text-formatting)
- [Hyperlink](#hyperlink)
- [Image](#image)
- [Inline Code](#inline-code)
- [Block Code](#block-code)
- [Unordered List](#unordered-list)
- [Ordered List](#ordered-list)
- [Horizontal Rule](#horizontal-rule)
- [Table](#table)
- [Task List](#task-list)
- [Escaping characters](#escaping-characters)

## Heading
```
# Header 1
## Header 2
### Header 3
#### Header 4
##### Header 5
###### Header 6
```
[[Go back]](#table-of-contents)

## Blockquote
> This is a quoted paragraph.
```
> This is a quoted paragraph.
```
[[Go back]](#table-of-contents)

## Text Formatting
1. **Bold** - (double asterisks or underscores)
```
This is **bold**.
This is __bold__.
```
2. *Italic* - (single asterisk or underscore)
```
This is *italic*.
This is also _italic_.
```
3. ~~Strikethrough~~ - (double tilde)
```
This is a ~~strikethrough~~.
```
[[Go back]](#table-of-contents)

## Hyperlink
This is a [link](https://google.com).
```
This is a [link](https://google.com).
```
[[Go back]](#table-of-contents)

## Image
```
![alt text](image-url "tooltip")
```
[[Go back]](#table-of-contents)

## Inline Code
This is an `inline` code.
```
This is an `inline` code.
```
[[Go back]](#table-of-contents)

## Block Code
- Use triple backticks.

    ```
    console.log('Hello world');
    ```
- Indent by four spaces.

    ```
        console.log('Hello world');
    ```

- Enable syntax highlighting by specifying the language
    - Code:
    
        ```javascript
        function sayHello(name) {
          console.log(`Welcome, ${name}`);
        }
        sayHello('John');
        ```

    - Preview:
        ```javascript
        function sayHello(name) {
          console.log(`Welcome, ${name}`);
        }
        sayHello('John');
        ```
[[Go back]](#table-of-contents)

## Unordered List
Use dashes or asterisks for each item.
### Code:
```
- First bullet
- Second bullet
  - Nested Item
- Third bullet

* Asterisk A
* Asterisk B
  * Nested Asterisk
* Asterisk C
```
### Preview:
- First bullet
- Second bullet
  - Nested Item
- Third bullet

* Asterisk A
* Asterisk B
  * Nested Asterisk
* Asterisk C

[[Go back]](#table-of-contents)

## Ordered List
### Code:
```
1. First item
2. Second item
3. Third item
```
### Preview:
1. First item
2. Second item
3. Third item

[[Go back]](#table-of-contents)

## Horizontal Rule
Triple dash or underscore.
```
---
___
```
[[Go back]](#table-of-contents)

## Table
### Code:
```
| Name     | Email              |
| -------- | ------------------ |
| John Doe | john.doe@gmail.com |
| Jane Doe | jane.doe@gmail.com |
```
### Preview:
| Name     | Email              |
| -------- | ------------------ |
| John Doe | john.doe@gmail.com |
| Jane Doe | jane.doe@gmail.com |

[[Go back]](#table-of-contents)

## Task List
Used to show a list of tasks with their completion status.
### Code:
```
* [x] First task
* [x] Second task
* [ ] Third task
```
### Preview:
* [x] First task
* [x] Second task
* [ ] Third task

[[Go back]](#table-of-contents)

## Escaping characters
Use backslash to escape markdown-specific characters.
### Code:
```
This *italic text* is not escaped.
This \*italic text\* is escaped.
```
### Preview:
This *italic text* is not escaped.

This \*italic text\* is escaped.

[[Go back]](#table-of-contents)

