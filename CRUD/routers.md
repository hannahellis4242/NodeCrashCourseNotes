# Routers

While you can write all your routes out and set the handlers in your main code file, for a large application it can get very large very quickly. It is common to split up your app using routers.

## What is a router

A router can be thought of as a smaller subsection of your app that lives under it's own resource. For example if you have several urls that all start with the same path

- `\example\places`
- `\example\names`
- `\example\pets`

could all go into one router and the main code would use that router under `\example`.

``` typescript
import express from "express";
import exampleRouter from "./routes/example"

const app = express();

app.use("/example", exampleRouter);

const port = 8080;
app.listen(port, () => {
  console.log(`Server is listening on port ${port}`);
});
```

this is telling express for any routes that begin with `/example` that their handler is inside the exampleRouter.

The code in `routes/example.ts` will then look like this

``` typescript
import { Router } from "express";

const exampleRouter = Router();
exampleRouter.get("/places", (_, res) => res.send("places"));
exampleRouter.get("/names", (_, res) => res.send("names"));
exampleRouter.get("/pets", (_, res) => res.send("pets"));

export default exampleRouter;
```

which looks like the typical app setup you might be familiar with by now.

Another typical situation with routers is having one router per page of a web app that uses forms. The router deals with the get and post requests for a page, allowing the main file just to set the url for the page.

``` typescript
// main.ts
import express from "express";
import page from "./routes/page"

const app = express();

app.use("/page", page);

const port = 8080;
app.listen(port, () => {
  console.log(`Server is listening on port ${port}`);
});
```

``` typescript
// page.ts
import { Router } from "express";

const page = Router();
start.get("/", (_, res) => res.render("start"));
start.post("/", (req, res) => {
  //do the processing of the form input here

  //redirect to the next page
  res.redirect("/nextPage");
});

export default start;
```
