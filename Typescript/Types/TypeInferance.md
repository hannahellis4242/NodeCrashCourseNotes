# Type Inference

TypeScript can work out for itself what type a variable should be when it is initialised, so you don't have to always include a type annotation when creating new variables, so long as you initialise the variable too.

For example, this works

``` typescript
const theAnswer = 42;
```

but this won't

``` typescript
let theQuestion ;
theQuestion = "Life, the Universe and Everything";
```

as TypeScript can't look ahead to see what the variable type should be.

This works for objects and arrays too.

Try it with this array and see what type you get back

``` typescript
const array = ["Hello World",42] ;
```
