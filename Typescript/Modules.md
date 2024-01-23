# Modules

All your packages you install into your project will be in the form of modules. They live in your node_modules directory. This is where node will look when importing something from a module, unless it is a user created module. Since you'll be using modules a lot, we will look into them a little bit here.

## Importing a Module

The first thing you are going to want to do with a module is import it. This easily done by using the __import__ keyword

``` typescript
import express from "express";
```

This imports the default module into your code, you can also import a particular part of a module by using {}

``` typescript
import { join } from "path";
```

It is also possible to import both the default module as well as anything extra you wish to use

``` typescript
import express, { json, urlencoded } from "express";
```

As you can imagine you can also import things from your own modules. When you import from your own module, you have to specify a path in the _from_ part of the import line.

```typescript
import start from "./start";
```

which will import the default module from a file in the same directory called _start.ts_.

## Writing your own Module

Since you can import your own modules, it stands to reason you can also write your own module. A module is nothing more than a TypeScript file (one ending in .ts) that contains the keyword __export__ somewhere in it.

### export

You can use the export keyword to make any variable or type available for import.

I will just give you an example of a function exported from a file called _hello.ts_

```typescript
//hello.ts
export const sayHello = ():string=>"Hello World";
```

Then we import this in our _main.ts_ file by using an import statement

```typescript
//main.ts
import {sayHello} from "./hello.ts";
console.log(sayHello());
```

To compile and run this you would use the following commands

``` bash
npx tsc
node dist/main.js
```

### export default

You might have noticed that we needed to use {} to import, that is because the function isn't the default export. We could make it the default export by adding the __default__ keyword and a small change.

```typescript
//hello.ts
const sayHello = ():string=>"Hello World";
export default sayHello;
```

You can now change main.ts to be the following

```typescript
//main.ts
import sayHello from "./hello.ts";
console.log(sayHello());
```

You don't need a separate line for interfaces or classes, for example

```typescript
//Card.ts
export default class Card{
    isFaceUp:boolean;
    constructor(public pip:Pip,public suit:Suit){
        this.isFaceUp = false;
    }
    turnFaceUp(){
        this.isFaceUp = true;
    }
}
```

which we can import into our _main.ts_ like this

```typescript
//main.ts
import Card from "./Card.ts";
console.log(new Card("four","clubs"));
```

You can also export type alias, for example

``` typescript
//Suit.ts
type Suit = "clubs"|"diamonds"|"hearts"|"spades";
export default Suit;
```

As an exercise, see if you can make the Card class better so that it can only take a valid suit name as the argument for suit rather than string. Can you do the same for the pip value also? Can you put them in separate files and import them as needed?
