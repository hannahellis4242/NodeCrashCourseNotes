# Methods in Express

In the [Hello Express](../HelloExpress.md) section we saw a very basic Express app, which looked something like this

``` typescript
import express from "express";

const app = express();

app.use("/", (_, res) => res.send("Hello World"));

const port = 8080;
app.listen(port, () => {
  console.log(`Server is listening on port ${port}`);
});
```

Here we used a the `use` method on the app object to set a handler function for the `\` route. The `use` method just sets that handler for all REST methods for the given route. However Express lets you set individual handler functions for each method of a route by using the corresponding method on the app.

For example a get method would look like this.

``` typescript
import express from "express";

const app = express();

app.get("/", (_, res) => res.send("Hello World"));

const port = 8080;
app.listen(port, () => {
  console.log(`Server is listening on port ${port}`);
});
```

If you try this it won't act any differently in your browser because your browser uses the get method to get the webpage information. If instead we used just the post method

``` typescript
import express from "express";

const app = express();

app.post("/", (_, res) => res.send("Hello World"));

const port = 8080;
app.listen(port, () => {
  console.log(`Server is listening on port ${port}`);
});
```

you would see the browser wouldn't be able to load the website because there isn't a handler for the get method now.

All the http methods have a corresponding method on the app object.
