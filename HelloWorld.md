# Hello World

## Setting up a Node Project

Node comes with it's own package manager, the _node package manager_ or _npm_ for short.

As well as managing the packages in your project _npm_ can do some extra things. Importantly for us, you can use it to set up a blank project.

Use you terminal and navigate to the directory you wish to put your project in. Once you are there, you can put in the command

``` bash
npm init
```

_npm_ will then ask you a series of questions about your project (you can just press enter to get the default answer if you aren't sure how to answer). Once you have done this, you will have a _project.json_ file in your directory. This file keeps a record of the packages you are using in your project as well as any scripts for _npm_ to run. We will talk about scripts more later but you will see the default test script in this file.

Additionally if you want to just accept the default answers when creating a new project you can use the _-y_ flag.

```bash 
npm init -y
```

You should remember the _npm_ command, you'll be using it a lot in this course and any time you work with a node project.

## Your First Node Program

Hello World is a typical starting point for many developers learning a new language (and even the starting point for some projects). We will continue the tradition by writing a new file called _hello.js_ with the following content

``` javascript
console.log("Hello World")
```

You can run this by typing the following command into your terminal

``` bash
node hello.js
```

This will run you JavaScript file and print Hello World to the terminal.
