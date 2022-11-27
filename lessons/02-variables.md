# Lesson 2: Variables

## What is a variable?

A variable is like a box that you can put something in. It enables your program
to keep track of values while it is running that might come from the user, a
file, a database, or some other location. A common use of variables in programs
you might use is to keep track of your name—this is what enables them to have
your name or your picture in the top corner. Learning how to work with
variables—creating them, updating their values, comparing them, and using them
in output—is one of the most common aspects of writing programs.

> A variable is called a "variable" because its value is variable—that is, it
> can change.

## How do you define a variable?

In the early days of JavaScript, there was only one way to define a variable,
and that was with the keyword `var` (short for variable):

```ts
var count = 2
```

However, in modern JavaScript, and especially in TypeScript, we differentiate
between true variables (which are named values that **can** change) and
constants (which are named values that **cannot** change). Specifics on how to
work with each are below. Since we are programming in TypeScript, we should not
be using `var` to declare our variables.

> The reasons for this will become more important in the next lesson, but the
> important takeaway for now is that if there is a value that you know will not
> change, set it as a constant, and set all other values as variables.

### Defining a constant

To define a constant, use the `const` keyword, give it a name, and set a value
after the equals sign. For example:

```ts
const pi = 3.141592
```

### Defining a variable

To define a variable, use the `let` keyword, give it a name, and optionally set
a value after the equals sign. For example:

```ts
let age = 13
```

Unlike constants, you can define a variable without giving it an initial value:

```ts
let age
```

And you can give it a value later:

```ts
age = 13
```

## Outputting variables

Now that you understand what constants and variables are and how to define them,
this line in the TypeScript playground should make sense to you:

```ts
const anExampleVariable = "Hello World"
```

Now, we are going to focus on the next line:

```ts
console.log(anExampleVariable)
```

In order to write output to the "logs" tab of the output area on the right in
the TypeScript playground, you use the `console.log` function. A **function** is
invoked by calling its name followed by parenthesis, optionally with variables
or other values passed to the function inside the parenthesis. Later, we will
learn how to write our own functions, but for the next few lessons, we will be
making use of the `console.log` function.

In addition to being able to pass constants and variables to the `console.log`
function, you can pass other types of values, like numbers:

```ts
console.log(42)
```

or text:

```ts
console.log("Hello world!")
```

You can also output the result of mathematical operations:

```ts
console.log(1 + 2)
console.log(10 - 8)
console.log(3 * 5)
console.log(3 / 4)
```

> In TypeScript, the four main mathematical operators are `+`, `-`, `*`, and
> `/`. `+` is addition and `-` is subtraction, of course, but `*` is
> multiplication and `/` is division.
