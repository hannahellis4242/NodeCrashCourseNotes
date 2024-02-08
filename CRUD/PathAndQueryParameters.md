# Path and Query Parameters

Sometimes when you make a request you need to send some data with the request to ensure you are targeting the correct resource.

For example if you want information about a product on a retail site, then there must be a way for the server to know what product you are interested in. Often this would be a product number or a product id.

There are two main ways in which you can send data with a request.

## Path Parameters

The parameter could appear in the path. For example you could imagine the url into a retail website could look something like this
> retail/product/A21B4536-983B-4B86-950E-C7AD4C94DA36

The `A21B4536-983B-4B86-950E-C7AD4C94DA36` part is what we would call a path parameter.

Express handles these in the following way

``` typescript
app.get("/product/:id",(req,res)=>{
    const {id} = req.params;
    const product = service.getProductWithId(id);
    if(!product){
        res.sendStatus(404);
        return;
    }
    res.json(product)
})
```

> Note : The property name of the parameter will be the same as the parameter specified in the path.

You can have more than one path parameter in your path, for example

``` typescript
app.get("rental/user/:userId/product/:productId",(req,res)=>{
    const {userId,productId} = req.params;
    const rental = service.getRental(userId,productId);
    if(!rental){
        res.sendStatus(404);
        return;
    }
    res.json(rental)
})
```

## Query Parameters

A query parameter is any parameter that appears after the ? in the url. They get sent as a set of key value pairs. 

Going back to our retail site example, the url with a query parameter might look like this
> retail/product?id=A21B4536-983B-4B86-950E-C7AD4C94DA36

Express handles query parameters in the following way

``` typescript
app.get("/product/",(req,res)=>{
    const { id } = req.query;
    if( !id ){
        res.sendStatus(400);
        return;
    }
    const product = service.getProductWithId(id);
    if(!product){
        res.sendStatus(404);
        return;
    }
    res.json(product)
})
```

> Note : The property name of the parameter will be whatever was supplied in the url

You can have more than one query parameter in your url, for example a url could look like this

> /rental?user=3ED5401F&product=21075505D548

and the corresponding code might look something like this

``` typescript
app.get("/rental",(req,res)=>{
    const {user,product} = req.query;
    if( ! user ){
        res.status(400).send("no user given");
        return;
    }
    if( ! product ){
        res.status(400).send("no product given");
        return;
    }
    const rental = service.getRental(user,product);
    if(!rental){
        res.sendStatus(404);
        return;
    }
    res.json(rental)
})
```
