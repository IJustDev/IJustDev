# Nodejs

NodeJs is a runtime environment for javascript. That means that javascript does not need a browser to run. With Nodejs, javascript can be run on your local PC. Hidden from the user, Javascript gets compiled to machine code.

## Modules
Module in Node.js is a simple or complex functionality organized in single or multiple JavaScript files which can be reused throughout the Node.js application.

Each module in Node.js has its own context, so it cannot interfere with other modules or pollute global scope. Also, each module can be placed in a separate .js file under a separate folder.

Node.js implements CommonJS modules standard. CommonJS is a group of volunteers who define JavaScript standards for web server, desktop, and console application. 

[Copied from tutorials-teacher][tutorials-teacher-node-modules] 

Look at following example:

### Example of modules
```javascript
// fileTwo.js
module.exports = function() {
    console.log("Hello world");
}

```

```javascript
// fileOne.js
const variableName = require('./fileTwo')

// The variable variableName becomes the function, exported in fileTwo.js
// This means that if you call variableName like this: variableName(). The program will print "Hello World"
variableName()
```

## What is npm?
NPM stands for `node package manager`. It makes use of the [modules](#modules) functionality in node.

If you run following command, a folder named `node_modules` will be created in your current directory.

```sh
$ npm i <package_name>
# for example
# $ npm i express
```

If you were to run the example `npm i express` a subdirectory called `node_modules/express` will be created. It will contain several
Javascript files that look alike the contents of [`fileTwo.js`](#example-of-modules)

Besides `npm i` there are other commands as shown in [this cheatsheet][npm-cheatsheet]. One of them: `npm init` which will be used for the [Getting Started part](#getting-started)


## Setting up
### Windows
1. Download https://nodejs.org/en/

### Linux
```sh
$ sudo apt-get install nodejs-legacy
```

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
