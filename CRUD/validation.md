# Validating Inputs

So there's lots of ways you could validate user input manually, such as checking if a query parameter was set or not with a guard.

``` typescript
routes.get("/", async (req, res) => {
    const { key } = req.query;
    if( ! key ){
        res.status(400).send("No key given");
        return ;
    }
    //key definitely exists past this point

    //get a resource somehow maybe from a database or calculate it or whatever
    const resource = service.getResource(key);
    res.json(resource);
});
```

However I wanted to take the opportunity to introduce you to a package that makes run time type checking a lot better.
