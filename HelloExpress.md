# Hello Express

Now we have some of the basics of TypeScript down, we can begin to look at using our first run time dependency.

## Express

Express is a web framework for Node. While node does have it's own built in way to deal with incoming http requests, it's better to let a framework take care of all the heavy lifting for you, freeing you up to worry about how your web application will work.

You can find out more about Express on [npm](https://www.npmjs.com/package/express).

## Your first Express Application

So we will go ahead and install express as a run time dependency in our project.

``` bash
npm i express
```

Since we are using Typescript and express isn't a typescript project we will need to import the types as a development dependency.

``` bash
npm i -D @types/express
```

### Short aside about data types

You might wonder how I knew that Express isn't a TypeScript package and how I know it had types available for us to use.
If you look back at it's page on npm you will see it has a little logo next to it.

- TypeScript projects get a TS logo. These projects have their types built into the project.
- JavaScript projects with data types under the _@types_ project get a DT logo. This means you will need to import the types separately like we have done for Express.
- No logo means it is a JavaScript project without any data types. You are sadly on your own if you want to use these projects in your application.

So now we have that out the way, we can get back on writing our app in _main.ts_

``` typescript
import express from "express";

const app = express();

app.use("/", (_, res) => res.send("Hello World"));

const port = 8080;
app.listen(port, () => {
  console.log(`Server is listening on port ${port}`);
});
```

Compile and run this application.

Now using your favourite browser navigate to
> localhost:8080

You should see blank page with the words "Hello World" on it.

Well done, you have written, compiled and run your first web application.

## Stopping your app

You can stop your application by pressing control and c in your terminal.
