# Built In Types

## Primitive Types

TypeScript has three primitive types

- string : a type for any kind of text such "Hello World" or "42"
- number : a type for any number such as 42, -3 or 3.14159
- boolean : a type that can only have two values, true or false.

As an example here are a few variables of the above types defined

``` typescript
const text : string = "Hello World!";
const e : number = 2.718281828459;
const isTrue : boolean = true;
```

> Note: const is the keyword to tell TypeScript that you don't want the value of the variable to change. If you wanted a variable you could change then you'd use the keyword _let_ instead.

## Arrays

An array is a collection of elements that can be of any type. For example

``` typescript
const names : string[] = ["Alice","Bob","Charlie","David","Edward","Fred"];
```

You can make an array of any type by putting square brackets after the type.

Arrays have many methods on them, including but not limited to, push, concat, map, filter and fold.

### Objects

Objects are at their most basic collection of key value pairs.
For example

``` typescript
const person = { name:"Alice" , age:34 };
```

Objects can also be made from Classes and can be checked to conform to a particular interface if it is required. We shall talk interfaces and classes later. Additionally objects can take functions as values to their parameters.

## Functions

It might be odd to think of functions as types, but in TypeScript functions are first class objects just as they are in any functional programming language (this is why you can do functional programming with JavaScript and TypeScript). I won't get too much into this here, but this means you can pass functions as arguments to functions and you can return functions from functions also.

There are two kinds of functions in TypeScript.

### JavaScript Style Functions

These functions are obviously functions as they are defined with the keyword _function_. They can have arguments and return types. For example

``` typescript
function countLetters(str:string):number{
    return str.length;
}
```

You have to be careful when using these types of functions with objects as they have a built in _this_ value which references the object the function is used with.

### Arrow (anonymous) Functions

These functions can be used inline or they can be assigned to variables, they aren't so obvious but are the preferred way to define a free function in TypeScript because unlike JavaScript style functions they don't have a built in _this_ reference.

You can recognise an arrow function because it uses an __=>__ (aka an arrow). For example

``` typescript
const countLetters = (str:string):number => {
    return str.length;
}
```

Additionally you don't need to use a return in an arrow a function if you can write the body as a single statement, for example

``` typescript
const countLetters = (str:string):number => str.length;
```

In the case of both types of function you call them by using the name (in the case of arrow functions the name is the name of the variable that they have been assigned to) and () to pass arguments.


``` typescript
const numberOfLetters = countLetters("Hello World");
```

## Null and Undefined

TypeScript has two "nothing" types with subtlety different meanings (although you might notice that these differences haven't reached the designers of various packages so you have to watch out for this).

### null

A null value is very literally "nothing", and represents when there is a valid nothing value. Since most types don't have a valid nothing value, you might not see null very often.

### undefined

An undefined value is more for the times when a variable cannot take a defined value, either because it was not set with one initially, or the variable itself doesn't exist on an object or it has been assigned undefined directly. This tends to be used in cases where there is a valid case that something could not have a definition. For example you could imagine a square root function giving back an undefined value if given a negative number. Undefined is generally preferred over null.

If you have a null or undefined value you can define a default value using the || operator.

``` typescript
const maybeAValue : string | undefined = undefined;
const value = maybeAValue || "default value";
console.log(value);
```

## Any and Unknown

Sometimes there are cases where you don't know what the type of a variable is. For these cases you have the any and unknown types.

### any

The any type is the most permissive type, as it will turn off TypeScripts type checking for any variable of this type. If you see a variable of this type then most likely it was an intentional choice by the developer or it might have been used to aid in upgrading JavaScript code to TypeScript. Either way, it's an indication that you should be careful because you won't have the compiler helping you.

This is also how TypeScript interacts with JavaScript, since to TypeScript all JavaScript types are any.

### unknown

If a type is unknown, then we literally do not know what type it is, and it could have any value. This another rare type as generally the type is known, however it does come up when handling exceptions.

## Union

Typescript also has union types, these are types that are created from other types. For example you might have a variable that can be a number or a boolean. You can express this with TypeScript like this

``` typescript
const nameOrBool : string | boolean = true;
```

You might see this used with the undefined type a lot when it's possible a function can "fail", as an example

``` typescript
const mySqrt = (x:number):number|undefined =>{
    if( x < 0 ){
        return undefined;
    }
    return Math.sqrt(x);
}
```

Additionally you might see union types used with a type alias, for example

``` typescript
type Suit = "clubs"|"diamonds"|"hearts"|"spades";
```
