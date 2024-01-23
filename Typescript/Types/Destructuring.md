# Destructuring

Destructuring allows you to access elements or properties without having to use a dot. It's very useful for functions that take in objects but you only want to use some of the properties of that object.

## Destructuring an Array

You can destructure an array by using square brackets, like this

``` typescript
const xs = [1,2,3,4,5];
const [a,b,c,d,e] = xs;
console.log(c);
```

you can also use something called a rest parameter, that gives you the rest of the elements in the array as an array

``` typescript
const xs = [1,2,3,4,5];
const [head,...tail] = xs;
console.log(head);
console.log(tail);
```

You can use this to destructure an array passed into an object like this

``` typescript
const getFirst = <T>([head,...]:T[]):T|undefined => head
```

> Note: I used a generic type in the function above. You should look at these later once you understand everything else as they are useful when you have a function that should accept any type but you want to ensure type safety. If you find it confusing just remove the __\<T\>__ and replace all the places you see a __T__ with a number or some other type you like. Oh look, you just learned how generics work.

## Destructuring an Object

You can destructure an object by using {}

``` typescript 
const favourites = {
    myFavouriteNumber:42,
    myFavouritePhase:"Hello World",
    myFavouriteBoolean:true,
};

const {myFavouriteNumber,myFavouritePhase} = favourites;
console.log(myFavouritePhase);
```

Again like array destructing you can use this in a function

``` typescript
interface Favourites{
    aNumber:number;
    aString:string;
    aBoolean:boolean;
}
const favourites = {
    aNumber:42,
    aString:"Hello World",
    aBoolean:true,
};

const describe = ({aNumber,aString}:Favourites):string => `number = ${aNumber}\nphrase = ${aString}``;
```
