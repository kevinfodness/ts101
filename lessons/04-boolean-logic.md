# Lesson 4: Boolean Logic

## What does "boolean" mean?

"Boolean," named after the 19th century mathematician George Boole, is an expression that can be evaluated to either
`true` or `false`. In TypeScript, this can literally be the value `true` or `false`, and you can define a variable or
a constant to hold one of these values. However, these values can also be derived by comparison.

## What is "boolean logic?"

Boolean logic is where you write an expression to compare the value of a variable against something else, which could be
a constant or another variable, to see if it meets certain conditions. For example, let's say we were writing a program
where a user is able to log in with a password. We would need to see if the user entered the proper password by
comparing what the user entered to the stored value of the correct password. We can do this as follows:

```ts
const correctPassword = 'banana'
const userPassword = window.prompt('Please enter your password.')
const validUser = userPassword === correctPassword
```

> Please note that this is a simple example to show how comparisons work. In practice, passwords would not be stored in
> code, especially code that could be visible to a user who might be trying to guess the password, and they would never
> be stored in "plain text"—the password would be obscured.

After the code above is run, the constant `validUser` will be `true` if the user entered the correct password and
`false` otherwise. The program can then use the value of this constant to make decisions about whether to allow the user
to access password-protected functionality or to show them an error message about entering the wrong password.

## How do I write boolean logic?

Boolean logic is written using two values and an operator. One of the values is on the left hand side of the operator,
and one of the values is on the right hand side. Values can be constants, variables, or literal values. For example,
all of the following boolean logic comparisons are valid:

```ts
const value = window.prompt('Enter a letter.')
const letterB = 'b'
let letterC: string = 'c'
const equalsA = value === 'a'
const equalsB = value === letterB
const equalsC = value === letterC
```

So far, we've been using one comparison operator, `===` (pronounced "triple equals"). Let's explore all of the operators
that can be used in boolean logic.

### Equal To (`===`)

Determines whether the value on the left hand side is equal to the value on the right hand side, and checks to ensure
that both values are of the same type.

```ts
2 === 2 // true
'2' === '2' // true
2 === '2' // false
'banana' === 'banana' // true
'apple' === 'banana' // false
```

#### Why `===`?

`===` is used to test for equality, because it checks to see whether values are not only the same, but of the same type.
A single equals sign (`=`) is used for **assignment**, or setting a variable to some value, like:

```ts
let letterC: string = 'c'
```

This means that we need a different operator for checking for equality.

Originally, the double equals (`==`) was used to test for equality. However, the double equals operator does a naïve
equality check and does not perform type checks. For example, `2 == '2'` would return `true`, even though one of the
values being compared is a number, and the other is a string. `2 === '2'` would return `false`, because although the
values appear to be the same, the types are not. In TypeScript, we should always use the triple equals operator to
check for equality because it performs type checks as well as value checks.

### Not Equal To (`!==`)

Determines whether the value on the left hand side is not equal to the value on the right hand side, or is of a
different type. It is the exact opposite of `===`.

```ts
2 !== 2 // false
'2' !== '2' // false
2 !== '2' // true
'banana' !== 'banana' // false
'apple' !== 'banana' // true
```

### Less Than (`<`)

Determines whether the value on the left hand side is less than the value on the right hand side.

```ts
2 < 3 // true
3 < 3 // false
4 < 3 // false
```

### Greater Than (`>`)

Determines whether the value on the left hand side is greater than the value on the right hand side.

```ts
2 > 3 // false
3 > 3 // false
4 > 3 // true
```

### Less Than or Equal To (`<=`)

Determines whether the value on the left hand side is less than or equal to the value on the right hand side. This is
like a combination of the less than operator (`<`) and the equality operator (`===`).

```ts
2 <= 3 // true
3 <= 3 // true
4 <= 3 // false
```

### Greater Than or Equal To (`>=`)

Determines whether the value on the left hand side is greater than or equal to the value on the right hand side. This is
like a combination of the greater than operator (`>`) and the equality operator (`===`).

```ts
2 >= 3 // false
3 >= 3 // true
4 >= 3 // true
```

## Combining Boolean Logic Checks

Often, you will want to perform more than one logic check at a time. For instance, you may want to check if both the
user-provided username **and** password are correct before granting access to something, or to see if a value is
within a particular range. Alternately, you may want to check if one of a number of conditions is true. To perform
these checks, you need to use the operators `&&` (and) and `||` (or).

### The And Operator (`&&`)

Used to validate that the boolean condition on the left hand side and the boolean condition on the right hand side both
evaluate to true. Can be chained together to make longer comparisons.

```ts
2 < 3 && 3 < 4 // true
2 < 3 && 3 > 4 // false
2 < 3 && 3 < 4 && 4 < 5 // true
2 < 3 && 3 < 4 && 4 > 5 // false
2 > 3 && 3 > 4 // false
```

### The Or Operator (`||`)

Used to validate that the boolean condition on the left hand side or the boolean condition on the right hand side
evaluates to true. Will return true if one or the other or both evaluate to true, but will return false if they both
return false. Can be chained together to make longer comparisons.

```ts
2 < 3 || 3 < 4 // true
2 < 3 || 3 > 4 // true
2 < 3 || 3 < 4 || 4 < 5 // true
2 < 3 || 3 < 4 || 4 > 5 // true
2 > 3 || 3 > 4 // false
```

## Grouping Boolean Logic Checks

Boolean logic checks can be grouped together, which is particularly useful when mixing the `&&` and `||` operators.
Grouping boolean checks is a lot like grouping and order in Algebra, where the `&&` operation happens first, then the
`||` operation. For example, say we wanted to see whether a pet is either a dog or a cat and has a name of "Bob":

```ts
petType === 'cat' || petType === 'dog' && petName === 'Bob'
```

This expression will work as you expect as long as the pet's name is "Bob," but it goes awry if the pet's name is
something else and it's a pet cat. In that case, due to the order of operations:

```ts
const petType = 'cat'
const petName = 'Jeremy'
petType === 'cat' // true
petType === 'dog' // false
petName === 'Bob' // false
true || false && false // false && false gets evaluated first:
true || false // this yields `true`, which isn't what we want
```

To avoid this problem, you can group boolean logic using parenthesis, like this:

```ts
(petType === 'cat' || petType === 'dog') && petName === 'Bob'
```

To be safe, when using a combination of `||` and `&&` operators in the same comparison, always use parenthesis to group
the comparisons that you want to execute first. This type of logic bug is difficult to find and fix, so it's best to be
explicit when writing the code in the first place.
