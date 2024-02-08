# Using JSON Body Data

## Turning on JSON Body Parsing

Before we can use JSON data in our app, we need to set up some `middleware` for our app. Middleware are just functions that get called before reaching our final request handlers that do some kind of task for us. For example logging middleware that logs out some information about the requests being made before passing the request onto the next handler. When middleware passes the request on to the next handler, that handler could be another middleware handler, or it could be our final request handler. For those who like their design patterns, you might recognise this as a [chain of responsibility pattern](https://en.wikipedia.org/wiki/Chain-of-responsibility_pattern).

Express comes with some built in middleware you can use in your application as required. One such middleware handler is one that parses the body of a request that contains JSON and converts it an object for us.

To use this you simply set `app.use(json())` as shown below

``` typescript
import express, { json } from "express";

const app = express();
app.use(json());

// do your usual app setup here

const port = 8080;
app.listen(port, () => {
  console.log(`Server is running on port ${port}`);
});
```

Once we have done this we can just read the body data as if it was an object in Typescript.

## Reading JSON Body data in your app

Reading the body from a request is very simple, the request object passed into your handler function will have a `.body` property on it.

For example

``` typescript
router.post("/", (req, res) => {
  const data = req.body;
  // do something with the data
  res.sendStatus(200);
});
```

## Sending JSON Body data from your app

Sending JSON data is just as simple, on the response object passed into your handler function there is a method called `.json()` that takes any object.

For example

``` typescript
routes.get("/", async (req, res) => {
    const { key } = req.query;
    //get a resource somehow maybe from a database or calculate it or whatever
    const resource = service.getResource(key);
    res.json(resource);
});
```
