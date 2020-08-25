# NodeJs

NodeJs is a tool that allows developers to run javascript natively (without a browser). This also enables functionalities like using the camera, displaying windows, writing real games, so on and so forth.

## Setting up
### Windows
1. Download https://nodejs.org/en/

### Linux
```sh
$ sudo apt-get install nodejs-legacy
```

## Modules
Modules in NodeJs are objects that cluster a set of functions, classes or variables, that later can be used (via requiring) by another developer.
In other words they are [libraries][libraries], a developer can access later on.

You can create a module that contains only one method that prints out `hello world` as shown in the example below.

```javascript
// module.js
module.exports = function() {
    console.log("Hello world");
}

```

If you want to import these function from a module then you need to `require` it.

```javascript
// app.js
const variableName = require('./fileTwo')

// The variable variableName becomes the function, exported in fileTwo.js
// This means that if you call variableName like this: variableName(). The program will print "Hello World"
variableName()
```

## What is npm?
NPM is an acronym for `node package manager`. It makes use of the [modules](#modules) functionality in node [described earlier in this document](#modules). And allows developers to share their code without much effort and in almost no time. Resulting in really fast development and maintainability.

Since all modules in node are plain Javascript files, `npm` is able to download the requested modules from a registry and install it to an special folder called `node_modules`.
The folder will be automatically created upon calling `npm i`.

```sh
$ npm i <package_name>
# for example
# $ npm i express
```

The subfolder inside `node_modules` called like the <package_name> will be created once you've run the command above => `node_modules/<package_name>`.

Besides `npm i` there are other commands as shown in [this cheatsheet][npm-cheatsheet]. One of them: `npm init` which will be used for the [Getting Started part](#getting-started)

## Getting started

### First Step - without modules
For a simple example app, create an `index.js` file with following contents:
```javascript
console.log("Hello World");
```

and run it via:
```sh
$ node index.js
```

### Second Step - with modules
An npm project is created by running `npm init`. It resolves in creating an json file with your inputs in your current directory named `package.json`. If you don't want to get asked more than in an Subway use the `--yes` flag -> `npm init --yes`. An default package.json will be created for you.

Feel free to have a look at it by either opening it with your favourite editor or by using `cat package.json`.

> 'cat' is an program that prints out file contents. It accepts multiple filenames as parameters.
> cat filename1.txt filename2.txt would therefore print out the contents of both files ordered by parameter order.

Now install the express package by calling
```sh
$ npm i express
```

The `package.json`'s content should be updated and the section `dependencies` now contains `"express": "VERSION_HERE"`.

Now create a file called `index.js` and append following content.
```javascript
const express = require("express");

express().listen(3000, function() {
    console.log("Running Webserver on port 3000");
});
```
> Above file will create a webserver with the [express][express] framework.

## Further Reading
- [modules][tutorials-teacher-node-modules]

[tutorials-teacher-node-modules]: https://www.tutorialsteacher.com/nodejs/nodejs-modules
[npm-cheatsheet]: https://devhints.io/npm
[express]: https://github.com/express/express
[libraries]: https://en.wikipedia.org/wiki/Library_(computing)
