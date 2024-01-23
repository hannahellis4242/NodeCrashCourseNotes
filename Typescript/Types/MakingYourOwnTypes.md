# Making Your Own Types

## Interfaces

You can use interfaces to ensure an object conforms to a particular shape. This can be useful when you have a function that uses particular properties of a class and you want TypeScript to ensure that those exist. It's also useful when you are defining a data model in your code.

Interfaces can also ensure that any class that implements it also defines some member functions (also known as methods).

Lets take a look at an interface

``` typescript
interface Animal{
    name:string;
    isAquatic:boolean;
    makeNoise():string;
}
```

You can see that this interface ensures that anything that implements it must have a name property that is a string, an isAquatic property that is a boolean and a function makeNoise.

Interfaces can have optional parameters too. These are shown by either making the type a union with undefined or using a question mark.

For example a model repressing an exam result, it could be that the exam hasn't yet been graded, so the score should be optional.

``` typescript
interface ExamResult{
    studentId:string;
    subject:string;
    score?:number;
}
```

### Using interfaces

You can define an value to conform to an interface by using the interface name in place of the type when you define it. You can also do the same thing with function arguments

``` typescript
const statement = (animal:Animal):string => `The ${animal.name} says ${animal.makeNoise()}`

const fox : Animal = { 
    name:"fox",
    isAquatic:false,
    makeNoise:()=>"what"
    };

console.log(statement(fox));
```

## Classes

Classes allow you to create objects that conform to a particular shape and define functions on them. For example

``` typescript
class Card{
    isFaceUp:boolean;
    constructor(public pip:Pip,public suit:Suit){
        this.isFaceUp = false;
    }
    turnFaceUp(){
        this.isFaceUp = true;
    }
}
```

You can create an instance of a class by using the __new__ keyword. You access members by using a . and then the name of the variable. You can access functions this way too. As an example.

``` typescript
const card = new Card("king","spades");
console.log(card.isFaceUp);
card.turnFaceUp();
console.log(card.isFaceUp);
```

> Note: The code above shows that const is only referentially constant. Ie only the reference to the card is constant, but the card itself can change.

Classes can also be made to conform to an interface by using the __implements__ keyword

``` typescript
class Dog implements Animal{
    name:string,
    isAquatic:boolean,
    constructor(){
        this.name = "dog"
        this.isAquatic = false;
    }
    makeNoise(){
        return "woof";
    }
}
```

You get your typical inheritance relationships too, a class can extend an existing class with the __extends__ keyword.

``` typescript
class Chihuahua extends Dog{
    constructor(){
        super()
    }
    makeNoise(){
        return "yap";
    }
}
```

