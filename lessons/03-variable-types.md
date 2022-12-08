# Lesson 3: Variable Types

## What are variable types?

Going back to the metaphor from lesson 2 of a variable being like a box, types
are like rules for what can be put in the box. In the previous lesson, we
created variables using the `let` keyword, and sometimes gave them initial
values, but otherwise didn't set any rules about what kind of values they could
hold.

Fundamentally, a program is a set of instructions to the computer, and the more
rules you can establish for how that program should run, the less of a chance
there is that the program will encounter a problem, known as a "bug." For
example, if we defined a variable but didn't define any rules about how it
should operate, we could do this:

```ts
let age = "banana"
```

As a human, we can read that expression and understand that it is absurd and is
likely to result in a bug, but a computer doesn't know any better. A computer
might later run this code:

```ts
let currentYear = 2022
console.log("Your birth year is:")
console.log(currentYear - age)
```

Of course, attempting to subtract `banana` from `2022` will not yield a number,
and anything else in the program that expects `age` to be a number will fail.

To solve this problem, TypeScript has added a types system on top of
JavaScript, which enables you as the programmer to tell the computer what data
type your variables are allowed to hold, so the computer can tell you if you
have created a bug by assigning the wrong type of value to your variable.

## How do I give a variable a type?

### Data types and constants

First, a word on constants. TypeScript is pretty smart, and it knows that the
value of a constant can't change, so it is able to **infer** the type of a
constant without being told. For instance, if you define a constant for your
birth year:

```ts
const myBirthYear = 1983
```

TypeScript is able to know that the data type is a number, because the value
was set when the constant was declared, and the value of a constant is not
allowed to be changed. This is why any values you know won't change should be
declared as constants, because it saves the trouble of defining a data type.

### Variable data types

To define a data type on a variable, you add a colon (`:`) after the variable
name, then specify the type of value that variable is allowed to contain.

```ts
let myAge: number = 39
```

Later, if you try to give that variable a value that isn't allowed, the
TypeScript compiler will tell you that it isn't allowed before your program
even runs so that you can fix your mistake:

```ts
myAge = "banana"
```

> This code yields an error that says "Type 'string' is not assignable to type
> 'number'." It also includes an error code, which in this case is `2322`.

## What data types are available?

### Primitive data types

TypeScript has three basic data types, called **primitives**. These are:

- `string`
- `number`
- `boolean`

#### String

A string is any bit of text, which may or may not include numbers, punctuation,
or anything else you can type on a keyboard. Strings are enclosed in quotes,
which can be either double quotes (`"`) or single quotes (`'`). You can use
either, although you will need to use the same character to end a string as you
did to start it (for example, `'my string"` is invalid).

The following are all valid strings:

- `"Hello World!"`
- `'foo bar baz'`
- `"42"`

For example, to declare a variable to hold the user's name:

```ts
let userName: string = "Testy McTesterson"
```

#### Number

Numbers are basically anything you can type into a calculator. They can be
whole numbers, like `42`, or fractional numbers, represented as decimals, like
`3.141592`. The results of division operations are stored as decimals as well
(for example, `3 / 4` is stored as `0.75`).

For example, to declare a variable to hold the current year:

```ts
let currentYear: number = 2022
```

#### Boolean

Boolean simply means `true` or `false`. We will cover boolean logic in the next
lesson, but for now, know that you can store these two values in a special type.

For example, to declarea variable that tracks whether the user likes chocolate:

```ts
let userLikesChocolate: boolean = true
```

### Complex data types

#### Arrays

Arrays are lists, and lists can have types as well. Simple array types are
defined as the type of values the array can contain followed by square brackets
(`[]`). 

For example, to define a shopping list:

```ts
let myShoppingList: string[] = ["apples", "bananas", "cucumbers"]
```

Or to define the ages of the members of a family:

```ts
let myFamilysAges: number[] = [5, 7, 10, 12, 36, 39]
```

#### Objects

Objects are data that has properties, and each property has a value. For
example, we could create an object to describe a person, and the person
object would have properties like name, age, hair color, and the like.

In order to define an object in TypeScript, you have to declare an
`interface` for the object that describes what properties it has and
what types those properties are. Then, you can create a variable that has
the interface's type so that TypeScript understands what kind of object
you are using.

For example, you can create an `interface` to describe an object like this:

```ts
interface Person {
    age: number;
    hairColor: string;
    name: string;
}
```

Then, you can create a variable of type `Person` and assign values to each
property:

```ts
let harry: Person = {
    age: 11,
    hairColor: 'brown',
    name: 'Harry Potter',
}
```

All objects are defined by enclosing their contents in curly braces (`{}`)
and specifying a key, followed by a colon (`:`), followed by a value, followed
by a comma. In the example above, we set `age` to `11`, `hairColor` to `brown`,
etc. Objects can be much more complicated than this, but we'll get into that
later. For now, know that you can create an object that has properties with
values, and you define a custom type for the object with `interface`.

### Union Types

Sometimes, a variable can contain more than one type of value. You can specify
more than one type and join them into a "union" type using the pipe character
(`|`). For example, if you wanted to define a variable that could accept a
number or a string, you can define it like this:

```ts
let myStringOrNumber: string | number
myStringOrNumber = 2
myStringOrNumber = "banana"
```
