# Introducing TypeScript

You may have noticed in the hello world example that it was a JavaScript file, which makes sense with Node being a JavaScript engine. However due to Node's increasing popularity, there have been other languages built on top of it. One language is TypeScript.

TypeScript extends JavaScript to offer type safety as well as other features (many but not all of these additional features have made their way into JavaScript due to the growing usage of TypeScript).

## Why TypeScript

So if Node is a JavaScript Engine, you might be asking why I am using TypeScript for this course and not just raw JavaScript.

Largely it is personal preference, and increasingly JavaScript is taking on features of TypeScript to the point it is now almost completely preference of which you use. However for me the added type system that TypeScript gives you is enough to sway me towards TypeScript.

Additionally if you know TypeScript then you know JavaScript. TypeScript is a superset of JavaScript. That means that valid JavaScript is also valid TypeScript, and so you are learning two languages for the price of one. Neat huh?

Also TypeScript is still used on client projects, so it's worth knowing just for that.

## Hello TypeScript

We are once again going to write the hello world program, but this time in TypeScript.

You might be asking me now, if valid JavaScript is valid TypeScript, haven't we already written the Hello World Program? You would be correct to say this, and you will see later there's no difference in the code at all. The aim of this section is getting used to using the TypeScript.

Since Node is a JavaScript engine, it doesn't know how to run TypeScript natively. Our TypeScript code will need to be translated into JavaScript for node to run it. However to get the type safety checking that is TypeScript's hallmark, we need to compile. So which is it? Compile or translate?

The answer is both. TypeScript does a process called transpiling. It both compiles your code (ie runs checks to ensure your code is valid TypeScript) and translates your code into raw JavaScript.

To make use of the TypeScript transpiler we will need to use the TypeScript package as a development dependency in our project. Development dependencies are ones that are used purely by developers to test, build or deploy their code, but are not used by the code itself at runtime. To install the package we will type the following command into our terminal

``` bash
npm install --save-dev typescript
```

>Note: the --save-dev tells npm to save the package as a development dependency. There are short forms for both the install command and the --save-dev flag (i and -D respectively) that you will see in later commands.

### Dealing with dependencies more generally

This is a good time to mention that JavaScript packages don't come with their types defined. This includes Node's core libraries too. Luckily for us using TypeScript, there are packages that contain just the types for JavaScript packages. These usually begin with _@types_. It's a good idea if you're going to be using Node to run your TypeScript code to also include _@types/node_ as a development dependency by using the command below.

``` bash
npm i -D @types/node
```

>Note : I have used the short form here with i being the same as install and -D being the same as --save-dev

If you look at your _package.json_ file now, you will see there is now a devDependencies object in it, and that object contains the dependencies you just added using the _npm install_ command. You will also notice there is a _package-lock.json_ file too. This is just like your package file except it also contains a list of all the things your dependencies also depend upon. The lock file tells npm which versions of every dependency it should use, and helps to keep things consistent within your project.

Additionally you will notice a directory called _node_modules_, this is the directory where all the dependency code is kept so that the node engine can access the code to run them with your code.

### Reinstalling dependencies

It is sometimes required to reinstall all your dependencies from scratch when updates come out. You can do this by deleting both the node_modules directory and the lock file then running

``` bash
npm i
```

If you don't specify any particular package to install, the install command will look for a lock file to find the list of dependencies to install, if it cannot find a lock file, then it will generate one from your existing package.json file.

## Hello TypeScript Continued

Now that you have TypeScript installed, it is time to set it up. The TypeScript transpiler uses a file called _tsconfig.json_ to control where it will look for files to compile and where it will put the resulting JavaScript and also to configure other features. You can create the default configuration file by typing the following command into your terminal.

``` bash
npx tsc --init
```

Here we have used the _node package runner_ (or _Node Package eXecutor_) to run the node package _tsc_.

_tsc_ is the TypeScript Compiler. _tsc_ will transpile your TypeScript code into JavaScript. It just gets called a compiler despite also doing translation.

_tsc_ has various flags, but here we are using the --init flag to tell it to generate the initial (or default) configuration file for us.

Once you have run this command, you will see a _tsconfig.json_ file in your project directory.

### Tweaking the Config

The most of the defaults in the configuration are suitable for our project, we just have to change two things. Firstly we need to change the _rootDir_ to be _./src_, so that _tsc_ knows to read from the /src directory within our project. Secondly we should change the _outDir_ to be _./dist_ so that _tsc_ knows we want it to create the dist directory within our project and to put the JavaScript files it creates there.

Once this is all done, we just need to create a src directory, and move our hello world code into it (as well as change the extension). So you should end up with a src folder with a file called hello.ts in it.

Now we are ready to compile, and since we're likely to do this a lot, it's a good time to introduce npm scripts.

### Compilation Script

In your package.json file you will see a scripts object. You can go ahead now and change it to say the following

``` json
"scripts": {
    "build": "tsc",
    "start": "node dist/hello.js"
},
```

Once you have the script you can compile your code by using the npm run command

``` bash
npm run build
```

this script will then invoke npx to run the command that follows build in your package.json file. ie in this case it will do the same as

``` bash
npx tsc
```

which will compile your code and put the resulting code in the dist directory.

You should now have a dist directory with a hello.js file in it. You can run this either with node as so

``` bash
node dist/hello.js
```
or you can use the npm script

``` bash
npm start
```

> Note: We didn't use the run command here as start is one of the special commands that npm doesn't require you to run with run. There are two special commands, start and test. You can run these with run also, but because they are special commands you do not need to.

Both of these will give you the now familiar text on the screen of "Hello World"

Feel free to experiment with this a little in your own time. For example printing your name instead of world or maybe printing something like "1 + 2 = 3" (ie using an actual calculation in there). We will cover some of this later.