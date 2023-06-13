# JavaScript Fundamentals

# How to run JavaScript code 

JavaScript is a scripting language which means that you don't need any extra tools such as a compiler to run i. In fact all we need is the browser, and a HTML file. Let's add a simple 'Hello World!' output using JavaScript. 

We'll first need to create a simple HTML page: 

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Page Title</title>
</head>
<body>
  <script>
    // Your JavaScript goes here!
    console.log("Hello, World!")
  </script>
</body>
</html>
```
Inside the body tags we're going to declare an openig and closing script tag `script`. Now inside this script tag we can start to write our JavaScript inside it. Now to run this code we're going to to use the live server feature in VS Code, if you followed from the Bootstrap course, you will have already added this plugin to VS Code. In case you don't have it, simply search for 'live server' in the extensions tab in VS Code and then install and enable it. 

Simply click on the liveserver link at the bottom of the Visual Studio window and it should launch the web page in your default browser. Going forward, all the example will be using Google Chrome, I highly recommend that you use this browser. 

When you open the page you won't actually see anything, it will just be a blank white page! In order to see the output from our JavaScript code that we wrote, you need to open the console in the JavaScript dev tools in the browser. 

The quickest way to open the console is to right click anyhwhere on the page and then select `inspect`, this will open the dev tools panel and then simply select the console tab. A quick, as a web developer you'll spend quite a lot of time in the dev tools! So go ahead and take a few minutes to familiarise yourself with the layout. 

Once you have the console open, you should see the message that we wrote in our JavaScript printed to the console. We've just written our first piece of JavaScript code!

# Variables 

You can think of variables as simply “storage containers” for data in your code. In modern JavaScript there are two ways we can create a variable, using the `const` and `let` keywords. Now, it's worth mentioning that there is also a third way that we can create variables, and that's using the `var` keyword. However, this is a method that is now not used as widely, and you will find it being used in older JavaScript code and tutorials on the web. Let's now look at how we can declare  variable starting with `let`. 

## Using `let`

The statement below creates (in other words: _declares_) a variable with the name “message”:
```javascript
let message;
```
Now, we can put some data into it by using the assignment operator  = :
```javascript
message = 'Hello';
```
The string is now saved into the memory area associated with the variable. We can access it using the variable name:

```js
console.log(message)
```
This outputs the value that is stored inside the `message` variable: 
```
Hello
```
To be concise, we can combine the variable declaration and assignment into a single line:

```js
let message = 'Hello!'; 
console.log(message); // Hello!
```
### Declare multiple variables in one line

We can also declare multiple variables in one line:

```javascript
let user = 'Mohamed', age = 25, message = 'Hello';
```
This might seem shorter, but it is not recommend it. For the sake of better readability, please use a single line per variable. The multiline variant is a bit longer, but easier to read:

```js
let user = 'John'; 
let age = 25; 
let message = 'Hello';
```
Some people also define multiple variables in this multiline style:

```js
let user = 'John',   
	age = 25,   
	message = 'Hello';
```

Or even in the “comma-first” style:

```js
let user = 'John' 
	, age = 25 
	, message = 'Hello';
```
Technically, all these variants do the same thing. So, it’s a matter of personal taste.

### `var` instead of `let`

As I mentioned already, you may also find another keyword: `var` instead of `let`:
```js
var message = 'Hello';
```
The `var` keyword is _almost_ the same as `let`. It also declares a variable, but in a slightly different, “old-school” way.

There are subtle differences between `let` and `var`, but they do not matter for us yet. We’ll cover them in detail later on.

### Copying variables 

We can also declare two variables and copy data from one into the other. For example: 

```js 
let hello = 'Hello world!'; 
let message; 
message = hello; // now two variables hold the same data 
console.log(hello); // Hello world! 
console.log(message); // Hello world!
```
However, if you declare two variables with the same name then this triggers and error:

```js
let message = "This"; 
let message = "That";
```
If you do this you will get the following error: 

```
SyntaxError: 'message' has already been declared
```
As the message clearly says, that the variable `message` has already been declared and cannot be redeclared in the same script twice. So, we should declare a variable once and then refer to it without `let`.

### Variable naming 

There are two limitations on variable names in JavaScript:

1.  The name must contain only letters, digits, or the symbols `$` and `_`.
2.  The first character must not be a digit.

Examples of valid names:

```js
let userName; let test123;
```
When the name contains multiple words, [camelCase](https://en.wikipedia.org/wiki/CamelCase) is commonly used. That is: words go one after another, each word except first starting with a capital letter `longName`:

```js
let myVeryLongName = "very long name"
```

The dollar sign `'$'` and the underscore `'_'` can also be used in names. They are regular symbols, just like letters, without any special meaning. For example: 

```js
let $ = 1; // declared a variable with the name "$" 
let _ = 2; // and now a variable with the name "_" 
console.log($ + _); // 3
```
Examples of incorrect variable names:

```js
let 1a; // cannot start with a digit 
let my-name; // hyphens '-' aren't allowed in the name
```

Also, case matters - the variables `apple` and `APPLE` are two completely different variables. Another thing to keep in mind when creating variables is to not used JavaScript's reserved keywords. These include keywords like: 

- `let`
- `const`
- `for`
- `if` etc 

These are just some examples of the reserved keywords that you cannot use as variable names, please refer to the [list of reserved words](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#Keywords) keywords as they are used by the JavaScript language itself. 

## Using `const`

The second way that we can declare a variable in JavaScript is to use the `const` keyword instead of `let`: 

```js
const message = 'Hello';

console.log(message);
```
When we are sure that a variable will never change, we can declare it with `const` to guarantee and clearly communicate that fact to everyone. So essentially, the deference is with using `const` instead of `let` is that a variable declared with `const` cannot be redeclared. For example, the following will throw an error in JavaScript: 

```js
const message = 'Hello';

message ='Goodbye!' // Uncaught TypeError: Assignment to constant variable. 
```
So, whenever you have a variable that will not be changed in the future, you use a `const` and when you need to replace the value in the variable further down the code, you should declare it via the `let` keyword.

### Uppercase constants 

There is a widespread practice to use constants as aliases for difficult-to-remember values that are known prior to execution. Such constants are named using capital letters and underscores. For instance, let’s make constants for colors in hexadecimal format:
```js
const COLOR_RED = "#F00"; 
const COLOR_GREEN = "#0F0"; 
const COLOR_BLUE = "#00F"; 
const COLOR_ORANGE = "#FF7F00"; 

// ...when we need to pick a color 
let color = COLOR_ORANGE; 
console.log(color); // #FF7F00
```
It's worth noting that using upppercase as the name of the variable does not actually do anything special, rather it's a convention that's used to indicate a variable that does not change. Assigning the color values as upppercase has some benefits: 

-   `COLOR_ORANGE` is much easier to remember than `"#FF7F00"`.
-   It is much easier to mistype `"#FF7F00"` than `COLOR_ORANGE`.
-   When reading the code, `COLOR_ORANGE` is much more meaningful than `#FF7F00`.

Please remember that capital-named constants are only used as aliases for “hard-coded” values.

### Naming variables correctly 

Talking about variables, there’s one more extremely important thing. A variable name should have a clean, obvious meaning, describing the data that it stores. Variable naming is one of the most important and complex skills in programming. A quick glance at variable names can reveal which code was written by a beginner versus an experienced developer.

Please spend time thinking about the right name for a variable before declaring it. Doing so will repay you handsomely.

Some good-to-follow rules are:

-   Use human-readable names like `userName` or `shoppingCart`.
-   Stay away from abbreviations or short names like `a`, `b`, `c`, unless you really know what you’re doing.
-   Make names maximally descriptive and concise.

Sounds simple? Indeed it is, but creating descriptive and concise variable names in practice is actually quite difficult and takes practice. 

## Variables Summary 

We can declare variables to store data by using the `var`, `let`, or `const` keywords.

-   `let` – is a modern variable declaration.
-   `var` – is an old-school variable declaration. Normally we don’t use it at all, but we’ll cover subtle differences from `let` in the chapter [The old "var"](https://javascript.info/var), just in case you need them.
-   `const` – is like `let`, but the value of the variable can’t be changed.

Variables should be named in a way that allows us to easily understand what’s inside them.

## Exercise 

### Task 1

1.  Declare two variables: `admin` and `name`.
2.  Assign the value `"John"` to `name`.
3.  Copy the value from `name` to `admin`.
4.  Show the value of `admin` using `alert` (must output “John”).

### Solution 
```js
let admin, name; // can declare two variables at once 
name = "John"; 
admin = name; 
console.log( admin ); // "John"
```
### Task 2

1.  Create a variable with the name of our planet. How would you name such a variable?
2.  Create a variable to store the name of a current visitor to a website. How would you name that variable?

### Solution 

```js 
// 1
let ourPlanetName = "Earth";
// 2
let currentUserName = "John";
```
# Numbers 

Numbers are the building blocks of programming logic! In fact, it’s hard to think of any useful programming task that doesn’t involve at least a little basic math, so knowing how numbers work is quite important.

## Adding

With JavaScript we can do anything that we can do with a calculator, let's start with adding two numbers together: 

```js
let sum = 100 + 50; 

console.log(sum); // 150 
```
Likewise we can use variables to store the values and then add them together:
```js 
let a = 100; 
let b = 5; 

let sum = a + b; 
console.log(sum); // 150 
```
We can also have expressions: 

```js 
let a = 2; 
let result = (100 + 50) * a;

console.log(result) // 300
```
Note here that the order of operations follows what you've learned in Mathematics, which is the brackets is calculated first then multiplied the value in the variable `a`. The numbers in an arithmetic operation are called **operands**. So, in our previous examples, the 50 and the 100 are operands. The operation (to be performed between the two operands) is defined by an **operator** in our previous examples the operand was a + but this can be a -, * or divide (/).

## Subtracting 

We can also subtract two operands and get the difference by using the - operator in JavaScript: 

```js
let x = 100;
let y = 10; 

let diff = x - y;
console.log(diff) // 90
```

## Multiplying 

For multipliying numbers we simply use the asterisk (*) to denote this as the operator: 

```js
let x = 100;
let y = 10; 

let product = x * y;
console.log(product) // 1000
```
## Dividing 

The **division** operator (`/`) divides numbers:

```js
let x = 100;
let y = 10; 

let quotient = x / y;
console.log(quotient) // 10
```

## Remainder 

The **modulus** operator (`%`) returns the division remainder. I.e., in mathematics, the result of a **modulo operation** is the **remainder** of an arithmetic division:

```js
let x = 5;  
let y = 2;  
let remainder = x % y;

console.log(remainder) // 1
```

## Incrementing

The **increment** operator `++` increments numbers:

```js
let x = 5;  
x++;

console.log(x) // 6
```
In the example above we placed the `++` after the variable, but if we can place it before the variable like this: 

```js
let x = 5;  
++x;

console.log(x) // 6
```
This behaves the same way as before, but one thing to note about placing the `++` after the variable and then assigning to another variable: 

```js
let counter = 1;
let a = counter++; 

console.log(a); // 1
```
You might be wondering why `a` contains the value 1 and not 2, that's beause the _postfix_ form `counter++` increments `counter` but returns the _old_ value prior to incrementing. So, the `console.log` shows `1`.

## Decrementing

Likewise we can decrement numbers using the `--` operator:

```js
let x = 5;  
x--;

console.log(x) // 4
```

## Exponentiation

To raise a number to the power of any given value we can use the **exponentiation** operator `**`:

```js
let x = 5;  
let y = x ** 2;

console.log(y) // 25 
```

## Assignment operators

Assignment operators are operators that assign a value to a variable. We have already used the most basic one, =, loads of times it assigns the variable on the left the value stated on the right:

```js
let x = 3; // x contains the value 3
let y = 4; // y contains the value 4
x = y; // x now contains the same value y contains, 4
```
But there are some more complex types, which provide useful shortcuts to keep your code neater and more efficient.

### Plus equals `+=`

The plus equals increments a number by the given value, for example if we want to increment the number by 1 we would write: 

```js
let x = 3;

x +=1;

console.log(x) // 4
```
The expression `x +=1` increments the value in `x` by and then assigns the returned value, which is 1, back to the `x` variable. We don't necessarily have to increment by only 1 each time, we can specify any amouny we like, let's say that we want to increment by 5 each time: 

```js
let x = 3;

x +=5;

console.log(x) // 8
```
This now adds 5 each time we increment the value in `x` variable using the plus equals (`+=`) operator. 

### Minus equals `-=`

Conversely we can do the opposite of incrementing a value by a given number using the operator `-=`: 

```js
let x = 10;

x -=1;

console.log(x) // 9
```
This decrements the value by 1, again we can specify any number that we wish to decrement each time and it doesn't have to be 1. 

Important note: Increment/decrement can only be applied to variables. Trying to use it on a value like `5++` will give an error.

### Multiply equals 

We can also multiply the number by a given value and then have that value returned and reassigned to the variable: 

```js 
let x = 10;

x *= 2;
console.log(x) // 20
```
### Divide equal `/=`

The divide equals `/=` does the opposite of the multiply and it divides the number by the given value and then assigns the result back to the variable: 

```js
let x = 10;

x /= 2;
console.log(x) // 5
```

## Comparison operators 

Sometimes we will want to run true/false tests, then act accordingly depending on the result of that test — to do this we use **comparison operators**.

- === Strict equality (5 === 5)
- `!==` Strict-non-equality (3 ! == 2)
- `<` Less than (3 < 7)
- `>` Greater than (10 > 8)
- `<=` Less than or equal to (4<=4)
- `>=` Greater than or equal to (5 >= 5)

You will be familiar with all of these comparison operators from Math class, except for the triple equality operator === and the strict non equality operaor `!==`. We'll go through how these work in JavaScript. 

### Strict Equality 

The strict equality operator compares two values are exactly equal, for example: 

```js
5 === 5 // returns `true`

5 === 1 // returns 'false'
```
We use the triple equality operator in JavaScript because we want to check that both the values being compared are of the same type and are equal to each other. For example, the following check with strict equality operator return false because the values are not of the same type: 

```js 
5 === '5' // returns `false`
```
This might seem odd to you at first but the strict equality operator not only checks that the values are equal, it first checks to see that they are of the same type, that is they are both either a number or a string. In our case above, the firts value is of a Number type and the second value is wrapped in quotes and this is interpreted to be a String by JavaScript. So, the strict equality check fails here, they are not of the same type. 

That is why it's called the strict Equality check, it is strict in that it not only checks the values are the same but they are also of the same type. 

In some JavaScript code you might come across just two equals == instead of three: 

```js 
5 == '5' // returns `true`
```
Now this might be somewhat confusing to you, we just learned about strict equalit operator and how it works, now we have two equals and this seems to be opposite of the strict triple equals! What's happening here is that the JavaScript runtime is converting the string to a number, this is sometimes called coercing, and then it runs the comparison which is why it retuns true. 

### Strict non equality

Similar to how the strict equality operator with the triple equals operates, we have the strict non equality operator `!==` this checks if a value is strictly not equal to another value, that is it checks first of they are NOT of the same type and they are not equal, only then does it return true. For exampe:

```js
5 !== 3 // returns 'true'

5 !== '5' // returns 'false'
```
Similar to how the strict equality operator has a less strict version with just the double equals == the strict non equality also has a version with just a single equals: `!=`. This is again works in a similar fashion and it tries to coerce one of the values by converting its type. For example: 

```js 
5 !== '5' // returns 'true'
5 != '5' // returns 'false'
```
In the second example, you can see that we are getting false, because the non strict version converts the string to a number and then checks they are not equal that's why it returns false. Whereas in the first example it's more strict and checks that first they are not of the same type and then sees that it's a string and a number and immediately returns true. 

We'll revisit the strict and non strict operators later on, but for now just now that the strict versions tend to result in fewer errors, so you should always use them.

## Unary, Binary and Operand 

There are some terms that we need to understand before we continue working with numbers in programming. We mentioned previously what an operand is, but we'll go through it again along with Unary and Binary. 

- _An operand_ – is what operators are applied . For instance, in the multiplication of `5 * 2` there are two operands: the left operand is `5` and the right operand is `2`. Sometimes, people call these “arguments” instead of “operands”.
- An operator is _unary_ if it has a single operand. For example, the unary negation `-` reverses the sign of a number for example `-1`. The minus us a single unary operand in this case, becuase it only has 1 operand which is the number 1. 
- An operator is _binary_ if it has two operands for example two numbers. The same minus operator can also be in binary form as well:
```js
let x = 1;
let y = 3; 
console.log( y - x ); // 2, binary minus subtracts values
```
In the examples above we have two different operators that share the same symbol: the negation operator, a unary operator that reverses the sign, and the subtraction operator, a binary operator that subtracts one number from another.

## String concatenation with binary `+`

Let’s meet the features of JavaScript operators that are beyond the school arithmetics. Usually, the plus operator `+` sums numbers. But, if the `+` is applied to strings, it merges (concatenates) them:

```js
let s = "my" + "string"; 
console.log(s); // mystring
```
Note that if any of the operands is a string, then the other one is converted to a string too. For example: 

```js 
let x = 5;
let y = '5'; 

let result = x + y;
console.log(result) // 55
```
It doesn’t matter whether the first operand is a string or the second one.

## Numeric conversion with unary `+`

You can use the unary `+` operator to convert a non number value to a number:
```js
let x = '5'; // string number 

console.log(+x) // returns 5

// Converts non-numbers
console.log( +true ); // 1 
console.log( +"" ); // 0

// No effect on numbers 
let x = 1; 
console.log( +x ); // 1 
let y = -2; 
console.log( +y ); // -2
```
Notice that when applied to numbers it has no effect, but when applied to non numbers it converts to numbers. It might seem strange but when `+` is applied to `true` which is a boolean value it converts to 1, and conversely when applied to `false` it converts it to 0. In general, 0 can be converted to `false` and 1 can be converted to `true` in JavaScript.

The need to convert strings to numbers arises very often. For example, if we are getting values from HTML form fields, they are usually strings. What if we want to sum them? The binary plus would add them as strings:

```js
let apples = "2"; 
let oranges = "3"; 
console.log( apples + oranges ); // "23", the binary plus concatenates strings
```
If we want to treat them as numbers, we need to convert and then sum them:

```js
// both values converted to numbers before the plus
console.log( +apples + +oranges );
```
The abundance of pluses may seem strange. But from a programmer’s standpoint, there’s nothing special: unary pluses are applied first, they convert strings to numbers, and then the binary plus sums them up.

Why are unary pluses applied to values before the binary ones? As we’re going to see, that’s because of their _higher precedence_.

## Operator precedence

If an expression has more than one operator, the execution order is defined by their _precedence_, or, in other words, the default priority order of operators.

From school, we all know that the multiplication in the expression `1 + 2 * 2` should be calculated before the addition. That’s exactly the precedence thing. The multiplication is said to have _a higher precedence_ than the addition.

Parentheses override any precedence, so if we’re not satisfied with the default order, we can use them to change it. For example `(1 + 2) * 2`. In this expression the brackets are calculated first and then the result from the bracket is used to multiply by 2. 

There are many operators in JavaScript. Every operator has a corresponding precedence number. The one with the larger number executes first. Here are a few of the operators and their precedence number in JavaScript:

- (14) unary plus`+`
- (14) unary negation `-`
- (13) exponentiation `**`
- (12) multiplication `*`
- (12) division `/`
- (11) addition `+`
- (11) subtraction `-`
- (2) assignment =

As we can see, the “unary plus” has a priority of `14` which is higher than the `11` of “addition” (binary plus). That’s why, in the expression `"+apples + +oranges"`, unary pluses work before the addition.

## Assignment 

Let’s note that an assignment = is also an operator. It is listed in the precedence table with the very low priority of 2. That’s why, when we assign a variable, like:
```js
let x = 2 * 2 + 1;
console.log(x) // 5
```

The calculations are done first and then the = is evaluated, storing the result in `x`.

### Assignment returns a value

The fact of = being an operator, not a “magical” language construct is interesting. All operators in JavaScript return a value. That’s obvious for `+` and `-`, but also true for =. The call `x = value` writes the `value` into `x` and then returns it. Here’s a demo that uses an assignment as part of a more complex expression:

```js
let a = 1; 
let b = 2; 
let c = 3 - (a = b + 1);
console.log( a ); // 3 
console.log( c ); // 0
```

In the example above, the result of expression `(a = b + 1)` is the value which was assigned to `a` (that is `3`). It is then used for further t subtract it from 3, which gives 0 and that is what is assigned to the variable `c`.

This might look a bit complex, but is actually valid code and one that you might come across in JavaScript libraries source code. However, this does not mean you should write code like this, you should always aim to write clear and readable code. 

### Chaining assignments

Another interesting feature is the ability to chain assignments:

```js
let a, b, c; 
a = b = c = 2 + 2;
console.log( a ); // 4 
console.log( b ); // 4 
console.log( c ); // 4
```

Chained assignments evaluate from right to left. First, the rightmost expression `2 + 2` is evaluated and then assigned to the variables on the left: `c`, `b` and `a`. At the end, all the variables share a single value.

Once again, for the purposes of readability it’s better to split such code into few lines:

```js
c = 2 + 2; b = c; a = c;
```
This is easier to read, especially when eye-scanning the code fast.

## Exercises 

1. What are the final values of all variables `a`, `b`, `c` and `d` after the code below?
```javascript
let a = 1, b = 1;

let c = ++a; // ?
let d = b++; // ?
```
Solution: 
-   `a = 2`
-   `b = 2`
-   `c = 2`
-   `d = 1`

```js
let a = 1;
let b = 1;  
console.log( ++a ); // 2, prefix form returns the new value 
console.log( b++ ); // 1, postfix form returns the old value  
console.log( a ); // 2, incremented once 
console.log( b ); // 2, incremented once
```
2. What are the values of `a` and `x` after the code below?
```js
let a = 2; 
let x = 1 + (a *= 2);
```
Solution:
-   `a = 4` (multiplied by 2)
-   `x = 5` (calculated as 1 + 4)

# Knowledge check

1. Name the three ways to declare a variable
2. What rules should you follow when naming variables?
3. What happens when you add numbers and strings together?
4. How does the Modulo (%), or Remainder, operator work?
5. Explain the difference between == and ===
6. How do you increment and decrement a number?
7. Explain the difference between prefixing and postfixing increment/decrement operators.
8. What is operator precedence and how is it handled in JS?
9. What does unary plus operator do to string representations of integers? eg. +”10”

# Part 2 

# JavaScript data types

We're going to continue our journey learning the JavaScript fundamentals, and in this tutorial we're going to learn about strings and conditional logic in JavaScript. 

But before we dive into the specifics of strings and conditionals, we're first going to look at the different data types that are available in JavaScript. Now, a data type is the type of data that you can do things with in JavaScript, for example we've been looking at how to add, multiply and divide numbers in JavaScript. 

For this we've been using numbers and naturally this means that the data type for numbers in JavaScript is Number. In all there are 7 data types in JavaScript, these are: 

1. Number 
2. BigInt
3. String 
4. Boolean 
5. Null 
6. Undefined
7. Objects 

## Number 

We've already looked at this number type quite extensively when we looked at using JavaScript for math calculations such as adding, multiplying, dividing etc. The _number_ type represents both integer and floating point numbers.

```js
let n = 123; n = 12.345;
```
Besides regular numbers, there are so-called “special numeric values” which also belong to this data type: `Infinity`, `-Infinity` and `NaN`.

`Infinity` represents the mathematical [Infinity](https://en.wikipedia.org/wiki/Infinity) ∞. It is a special value that’s greater than any number. We can get it as a result of division by zero:
```js
console.log( 1 / 0 ); // Infinity
```
Or you can just reference it directly:

```js
console.log( Infinity ); // Infinity
```

`NaN` represents a computational error, which stands for Not a Number. It is a result of an incorrect or an undefined mathematical operation, for instance:

```js
console.log( "not a number" / 2 ); // NaN, such division is erroneous
```
Now any further mathematical operation on `NaN` returns `NaN`:

```js
console.log( NaN + 1 ); // NaN 
console.log( 3 * NaN ); // NaN 
console.log( "not a number" / 2 - 1 ); // NaN
```
So, if there’s a `NaN` somewhere in a mathematical expression, it propagates to the whole result. 

## BigInt

In JavaScript, the “number” type cannot safely represent integer values larger than `9007199254740991`. `BigInt` type was recently added to the language to represent integers of arbitrary length.

A `BigInt` value is created by appending `n` to the end of an integer:

```js
// the "n" at the end means it's a BigInt 
const bigInt = 1234567890123456789012345678901234567890n;
```
As `BigInt` numbers are rarely needed, we won' go into them in detail, but if you need such big numbers then you can read more about it here <a href="https://javascript.info/bigint" target="_blank">BigInt</a>. Read it when you need such big numbers.

## String 

A string in JavaScript must be surrounded by quotes:

```js
let str = "Hello"; 
let str2 = 'Single quotes are ok too'; 
let phrase = `can embed another ${str}`;
```

In JavaScript, there are 3 types of quotes:

1.  Double quotes: `"Hello"`.
2.  Single quotes: `'Hello'`.
3.  Backticks: `` `Hello` ``.

Double and single quotes are “simple” quotes. There’s practically no difference between them in JavaScript.

Backticks are “extended functionality” quotes. They allow us to embed variables and expressions into a string by wrapping them in `${…}`, for example:

```js
let name = "John"; 
// embed a variable 
console.log( `Hello, ${name}!` ); // Hello, John! 
// embed an expression 
console.log( `the result is ${1 + 2}` ); // the result is 3
```
The expression inside `${…}` is evaluated and the result becomes a part of the string. We can put anything in there: a variable like `name` or an arithmetical expression like `1 + 2` or something more complex.

Please note that this can only be done in backticks. Other quotes don’t have this embedding functionality!

```js
console.log( "the result is ${1 + 2}" ); // the result is ${1 + 2} (double quotes do nothing)
```
We'll look at strings in more detail in just a moment. 

## Boolean 

The boolean type has only two values: `true` and `false`. This type is commonly used to store yes/no values: `true` means “yes, correct”, and `false` means “no, incorrect”.

For instance:

```js
let isGreater = 4 > 1; 
console.log( isGreater ); // true (the comparison result is "yes")
```

We'll look at booleans in more detail later on in the conditional section. 

## Null 

The next type is `null`, which is a special value and forms a separate type of its own which contains only the `null` value:

```js 
let age = null;
```
In JavaScript, `null` is not a “reference to a non-existing object” or a “null pointer” like in some other languages.

It’s just a special value which represents “nothing”, “empty” or “value unknown”. The code above states that `age` is unknown.

## Undefined 

Another special value `undefined` also stands apart. It makes a type of its own, just like `null`. The meaning of `undefined` is “value is not assigned”. If a variable is declared, but not assigned, then its value is `undefined`:
```js
let age; 
console.log(age); // shows "undefined"
```
You can also explicitly assign `undefined` to a variable:

```js
let age = 100; // change the value to undefined 
age = undefined; 
console.log(age); // "undefined"
```
It's not recommend to do this intentionally with `undefined`. Normally, one uses `null` to assign an “empty” or “unknown” value to a variable, while `undefined` is reserved as a default initial value for unassigned things.

## Objects 

Another special type is the object type, All other types are called “primitive” because their values can contain only a single thing (be it a string or a number or whatever). In contrast, objects are used to store collections of data and are more complex entities.

For example, we can create a `person` object like this: 

```js
const person = {
	name: 'Mohamed'
	age: 27, 
	city: 'London'
}
```
Objects deserve a special treatment. We’ll deal with them later in detail, after we learn more about primitives.

## Typeof operator 

We've seen some operators when we looked at the math operations, when it comes to data types there is one useful operator that you can use to determine the data type of a particular value in JavaScript and that is the `typeof` operator. 

The `typeof` operator returns the type of the operand. It’s useful when we want to process values of different types differently or just want to do a quick check. A call to `typeof x` returns a string with the type name:

```js
typeof undefined // "undefined" 
typeof 0 // "number" 
typeof 10n // "bigint" 
typeof true // "boolean" 
typeof "foo" // "string" 
typeof Math // "object" 
typeof null // "object" 
typeof console.log // "function" 
```

1.  `Math` is a built-in object that provides mathematical operations. Here, it serves just as an example of an object.
2.  The result of `typeof null` is `"object"`. That’s an officially recognized error in `typeof`, coming from very early days of JavaScript and kept for compatibility. Definitely, `null` is not an object. It is a special value with a separate type of its own. The behavior of `typeof` is wrong here.
3.  The result of `typeof console.log` is `"function"`, because `console.log` is a function. We’ll study functions in detail later on. 

# Strings 

Next, we'll turn our attention to strings — this is what pieces of text are called in programming. We'll look at all the common things that you really ought to know about strings when learning JavaScript, such as creating strings, escaping quotes in strings, and joining strings together.

## Creating strings 

To start with, enter the following lines:

```js
const string = "text in programming is called strings";
console.log(string);
```
Just like we did with numbers, we are declaring a variable, initializing it with a string value, and then returning the value. The only difference here is that when writing a string, you need to surround the value with quotes.

If you don't do this, or miss one of the quotes, you'll get an error. Try entering the following lines:
```js
const badString1 = This is a test; 
const badString2 = 'This is a test; 
const badString3 = This is a test'; 
```
The strings that are declared here will all create an error, for the first string `badString1`, it does not have quotes at all and this creates an error. For the second and third variables it's missing the end and starting quotes. 

These lines don't work because any text without quotes around it is assumed to be a variable name, property name, a reserved word, or similar. If the browser can't find it, then an error is raised (e.g. "missing; before statement"). 

If the browser can see where a string starts, but can't find the end of the string, as indicated by the 2nd quote, it complains with an error (with "unterminated string literal"). If your program is raising such errors, then go back and check all your strings to make sure you have no missing quote marks.

## Single quotes Vs Double quotes 

In JavaScript, you can choose single quotes or double quotes to wrap your strings in. Both of the following will work okay:

```js
const single = 'Single quotes.';
const double = "Double quotes";
console.log(single);
console.log(double);
```
There is very little difference between the two, and which you use is down to personal preference. You should choose one and stick to it, however; differently quoted code can be confusing. 

So, in the above example we have single and double quoted strings, in our code we should only stick to one, that is either use single or double quotes for all of the strings that we have in our code. 

There are times where we'll need to mix and match single and double quotes for example: 

```js
const sglDbl = 'Would you eat a "fish supper"?';
console.log(dblSgl); // Would you eat a "fish supper"?
```
In this example we have mixed both single and double quotes because we have a quote within the string itself. In this situation we have used singe quotes to wrap the entire text and then used double quotes to wrap the text that we want to highlight as quoted text. 

Also, when we want to use apostrophes to denote first person speech we'll run into problems, for example: 

```js
// this raises error: Uncaught SyntaxError: Unexpected identifier 'm'
const singleQuotes = 'I'm feeling blue.'; 
console.log(singleQuotes);
```
The above text in our variable is perfectly fine outside of JavaScript, however when we try to assign this to the variable we get an error. This is because we are using 3 single quotes and the browser thinks that afer the second single quote the string has been closed off and the next character `m` is some sort of undefined variable. 

So, you can't include the same quote mark inside the string if it's being used to contain them. to fix this problem we can either escape the apostrophe, we'll look at escape characters next, or you can contain the string with double quotes: 

```js
const singleQuotes = "I'm feeling blue."; 
console.log(singleQuotes);
```
## Escaping characters in a string

To fix the error with using the same single quote apearing in the text like this: 

```js
// this raises error: Uncaught SyntaxError: Unexpected identifier 'm'
const singleQuotes = 'I'm feeling blue.'; 
console.log(singleQuotes);
```
We can use an escape character we need to escape the problem quote mark. Escaping characters means that we do something to them to make sure they are recognized as text, not part of the code. In JavaScript, we do this by putting a backslash `\` just before the character. Try this:

```js
// this raises error: Uncaught SyntaxError: Unexpected identifier 'm'
const singleQuotes = 'I\'m feeling blue.'; 
console.log(singleQuotes);
```
This works even though the single containing quote appears in the text itself, however this time we are escaping it using the backslash `\` character. You can escape other characters in the same way, e.g. `\"`, and there are some special codes to see the available escape characters see: <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#escape_sequences" target="_blank">Escape sequences</a> for more details.

## Concatenating strings

Concatenate just means "join together". To join together strings in JavaScript you can use a different type of string, called a _template literal_.

A template literal looks just like a normal string, but instead of using single or double quote marks (`'` or `"`), you use backtick characters (`` ` ``):

```js
const greeting = `Hello`;
```
This can work just like a normal string, except you can include variables in it, wrapped inside `${ }` characters, and the variable's value will be inserted into the result:

```js
const name = "Mohamed";
const greeting = `Hello, ${name}`;
console.log(greeting); // "Hello, Mohamed"
```
You can use the same technique to join together two variables:
```js
const one = "Hello, ";
const two = "how are you?";
const joined = `${one}${two}`;
console.log(joined); // "Hello, how are you?"
```
### Concatenation in context

Let's have a look at concatenation being used in action: 
```js
const name = prompt("Enter your name");
alert(`Hello ${name}`)
```
The above code uses the JavaScript builtin `prompt` function, we'll learn about creating our own custom functions later on, to get the user's name. When the user enters their name it stores that value in the `name` variable, we can then use template strings to greet the user by their name. 

Again, we are using another builtin in function `alert` to show an output message to the user with the greeting. 

### Concatenation using "+"

You can also concatenate strings using the `+` operator:

```js
const greeting = "Hello";
const name = "Abdi";
console.log(greeting + ", " + name); // "Hello, Abdi"
```
However, template literals usually give you more readable code:

```js
const greeting = "Hello";
const name = "Abdi";
console.log(`${greeting}, ${name}`); // "Hello, Abdi"
```

### Multiline strings

Template literals respect the line breaks in the source code, so you can write strings that span multiple lines like this:

```js
const output = `I like the car.
I gave it a score of 90%.`;
console.log(output);

/*
I like the song.
I gave it a score of 90%.
*/
```
To have the equivalent output using a normal string you'd have to include line break characters (`\n`) in the string:

```js 
const output = "I like the car.\nI gave it a score of 90%.";
console.log(output);

/*
I like the song.
I gave it a score of 90%.
*/
```

### Including expressions in strings

You can include JavaScript expressions in template literals, as well as simple variables, and the results will be included in the result:

```js
const subject = "Mathematics";
const score = 9;
const highestScore = 10;
const output = `I like the Mathematics ${subject}. I got a score of ${
  (score / highestScore) * 100
}%.`;
console.log(output); // "I like the Mathematics. I gave it a score of 90%."
```

Template literals are  a really powerful feature within strings in JavaScript and you can read more about different use cases here on MDN: <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals" target="_blank">template literals</a>

## Numbers Vs Strings 

So what happens when we try to combine a string and a number? Let's try it in our console:

```js
const name = "Front ";
const number = 242;
console.log(`${name}${number}`); // "Front 242"
```

You might expect this to return an error, but it works just fine. Trying to represent a string as a number doesn't really make sense, but representing a number as a string does, so the browser converts the number to a string and concatenates the two strings.

If you have a numeric variable that you want to convert to a string but not change otherwise you can use the `toString()` method that is available on all numbers in JavaScript to achieve this: 

```js 
const myNum = 123;
const myString = myNum.toString();
console.log(typeof myString2); // string
```
Conversely, the `Number` object converts anything passed to it into a number, if it can. For example: 
```js
const myString2 = "123";
const myNum2 = Number(myString2);
console.log(typeof myNum2); // number 
```
We've some terminology like the Number object, don't worry about these for now we'll learn all about objects and methods, which are just functions attached to objects, later on.

## String methods 

I mentioned briefly in the last step about the builtin `toString()` method that is available on all numbers in JavaScript and how we can use it to convert a number to a string in JavaScript. Now, we haven't really talked about what methods are in JavaScript, but they're essentially bit of functionality that is built into the language or into specific data types. 

We'll go into depth about objects and methods later on, but for now, all you need to know is that they are builtin features that we can use to manipulate a particular data type like strings. 

### Getting string length 

Now in JavaScript the string is an object and as we'll see objects have properties and methods. So this means that we can access the properties on a give string like how many characters are in a particular string for example: 

```js
let text = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";  
let length = text.length;
console.log(length); // 26
```
The `length` property is available in all strings and we can use it to get the length of any string. Note that this length will also include any empty spaces. For example: 

```js
let greet = 'Hello ';
console.log(greet.length) // 6
```
### Extracting String Parts

We can also extract parts of a string using some of the builtin methods that JavaScript makes available to us. In JavaScript there are 3 ways we can extract a part of a string: 

1. Slice 
2. Substring 
3. substr

We're only going to focus on `slice` and `substr` as `substring` is almost identical to `slice` with a slight difference. But you can look this up on your own if you want to see how it works. 

#### Slice

Returns the part of the string from `start` to (but not including) `end`. For instance:

```js
let str = "stringify"; 
console.log( str.slice(0, 5) ); // 'strin', the substring from 0 to 5 (not including 5)
console.log( str.slice(0, 1) ); 
// 's', from 0 to 1, but not including 1, so only character at 0
```
In the first example we get back `strin` that's because the strings are 0 index based. This means that instead of starting at 1 it starts at 0, so the first character `s` is sitting at the position 0, character `t` is sitting at 1 and so on. 

Now for the `slice` method it returns the starting position which is 0, in our string it's the letter `s` and it returns all of the characters upto and including `n`. Even though we specified 5 as the end of the part we want to return, we don't actually get the letter `g` included in the part that is returned. 

Now this is how the `slice()` method works if you specify 5 it will return everything but not including the character sitting at position 5. So if we wanted to return the letter `g` along with `strin` we would update our second value that we pass to the slice method: 

```js
let str = "stringify"; 
console.log( str.slice(0, 6) );
```
This will return `string` and so if we want the next character we have to add one and so on. If there is no second argument, then `slice` goes till the end of the string:

```js
let str = "stringify"; 
console.log( str.slice(2) ); // 'ringify', from the 2nd position till the end
```
Now in this example we are getting back `ringify`, since we haven't specified an end position. Negative values for `start/end` are also possible. They mean the position is counted from the string end:

```js
let str = "stringify"; 
// start at the 4th position from the right, end at the 1st from the right 
console.log( str.slice(-4, -1) ); // 'gif'
```
This one needs to thinking, when we supply negative values it starts from the end of the string instead of the beginning. So it will start from the last character `y`. Also, it will not be 0 index based, that is it just starts from 1 - so `y` is at position `-1`, `f` is at `-2`, `i` is at `-3`, `g` is at `-4`. 

So this means it will start at `-4`, that is letter `g` and then it will end at `-1` that is letter `y`, but if you remember it won't actually include this letter, so it just returns `f` and the letters `gif`. 

#### Subst

This method returns the part of the string from `start`, with the given `length`. In contrast with the previous method, this one allows us to specify the `length` instead of the ending position:

```js
let str = "stringify"; 
console.log( str.substr(2, 4) ); // 'ring', from the 2nd position get 4 characters
```
The first argument may be negative, to count from the end:

```js
let str = "stringify"; 
console.log( str.substr(-4, 2) ); // 'gi', from 4th position get 2 characters
```

### replace 

The `replace()` method replaces a specified value with another value in a string:
```js
let text = "Please visit Riyadh!";  
let newText = text.replace("Riyadh", "Fullstack");
console.log(newText); // PLease visit Fullstack!
```
- The `replace()` method does not change the string it is called on.
- The `replace()` method returns a new string.
- The `replace()` method replaces **only the first** match

### Converting to Upper and Lower Case

There are situtaions where you want to convert a string to either upper case or lower case and because this is a common requirement JavaScript has builtin support for this with the `toUpperCase()` and `toLowerCase()` methods: 

```js
let text1 = "Hello World!";  
let text2 = text1.toUpperCase();
console.log(text2) // HELLO WORLD!
```
If we wanted to get the lowercase values for all of the string we can use the `toLowerCase` method instead: 

```js 
let text1 = "Hello World!";  
let text2 = text1.toLowerCase();
console.log(text2) // hello world!
```

### Trim 

The `trim()` method removes whitespace from both sides of a string:

```js 
let text1 = "      Hello World!      ";  
let text2 = text1.trim(); 
console.log(text) // Hello World!
```
### Extracting String Characters

There are 3 methods for extracting string characters:

-   `charAt(_position_)`
-   `charCodeAt(_position_)`
-   Property access [ ]

### charAt()

The `charAt()` method returns the character at a specified index (position) in a string:

```js
let text = "HELLO WORLD";  
let char = text.charAt(0);
console.log(char) // H
```

### charCodeAt()

If we wanted to the character code instead of the actual character itself we can use the `charCodeAt()` method:
```js
let text = "HELLO WORLD";  
let charCode = text.charCodeAt(0);
console.log(charCode); // 72
```
The `charCodeAt()` method returns the unicode of the character at a specified index in a string: The method returns a UTF-16 code (an integer between 0 and 65535).

### Property Access

You can also get at a particular character using the property access method: 

```js
let text = "HELLO WORLD";  
let char = text[0];
console.log(char); // H
```
This is similar to using the `charAt()` method only this time we're accessing it as property with the bracket notation. 

## Strings are immutable

Strings can’t be changed in JavaScript. It is impossible to change a character. Let’s try it to show that it doesn’t work:

```js
let str = 'Hi'; 
str[0] = 'h'; // re-assign with lower case h 
console.log( str[0] ); // doesn't work
```
It doesn't throw an error when you try to re-assign the letter, it just doesn't work. The usual workaround is to create a whole new string and assign it to `str` instead of the old one. For iexample:

```js
let str = 'Hi'; 
str = 'h' + str[1]; // replace the string 
console.log( str ); // hi
```
we've only just scracthed the surface when it comes to the available string methods at our disposal, you can have a look at all of the available methods on this <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String" target="_blank">MDN link</a>. 

# Conditionals 

So far we've only looked at variables, how to do calculations and create strings in JavaScript. We're now going to change gears and look at how conditionals work in JavaScript.  The essence of programming is teaching the computer how to make decisions in order to do more involved things. Conditionals are how we do that.

## Comparisons 

We looked at comparison operators earlier when we learned about how numbers work in JavaScript, we're now going to look at them in more depth. We know many comparison operators from maths. 

In JavaScript they are written like this: 

- Greater/less than: `a > b`, `a < b`. 
- Greater/less than or equals: `a >= b`, `a <= b`. 
- Equals: `a == b`, please note the double equality sign == means the equality test, while a single one a = b means an assignment. 
- Not equals: In maths the notation is `≠`, but in JavaScript it’s written as` a != b`.

## Boolean is the result

All comparison operators return a boolean value, either `true` or `false`:

-   `true` – means “yes”, “correct” or “the truth”.
-   `false` – means “no”, “wrong” or “not the truth”.

For example:

```js
console.log( 2 > 1 ); // true (correct) 
console.log( 2 == 1 ); // false (wrong) 
console.log( 2 != 1 ); // true (correct)
```

A comparison result can be assigned to a variable, just like any value:

```js
let result = 5 > 4; // assign the result of the comparison 
console.log( result ); // true
```

## String comparison

To see whether a string is greater than another, JavaScript uses an internal unicode encoding table. In other words, strings are compared letter-by-letter. For example:

```js
console.log( 'Z' > 'A' ); // true 
console.log( 'Glow' > 'Glee' ); // true 
```
The algorithm to compare two strings is simple:

1.  Compare the first character of both strings.
2.  If the first character from the first string is greater (or less) than the other string’s, then the first string is greater (or less) than the second. We’re done.
3.  Otherwise, if both strings’ first characters are the same, compare the second characters the same way.
4.  Repeat until the end of either string.
5.  If both strings end at the same length, then they are equal. Otherwise, the longer string is greater.

In the first example above, the comparison `'Z' > 'A'` gets to a result at the first step. This is because the letter `Z` comes after the letter `A` and therefore it's greater than `A`. However, the same cannot be said for `Z` > `a`, this will return false, since all lowercase letters are greater than their uppercase counterparts.  

The second comparison `'Glow'` and `'Glee'` needs more steps as strings are compared character-by-character:

1.  `G` is the same as `G`.
2.  `l` is the same as `l`.
3.  `o` is greater than `e`. Stop here. The first string is greater.

## Comparison of different types

When comparing values of different types, like numbers and string numbers, JavaScript converts the values to numbers. For example:

```js
console.log( '2' > 1 ); // true, string '2' becomes a number 2 
console.log( '01' == 1 ); // true, string '01' becomes a number 1
```
Now, it's worth noting that using the == equal to check for equality will try to convert the types if they're not of the same type, and that's what's happening here. `01` get converted to a number and then it gets compared to 1, which returns `true`.

For boolean values, `true` becomes `1` and `false` becomes `0`. For example: 

```js 
console.log( true == 1 ); // true 
console.log( false == 0 ); // true
```
Again, JavaScript is making a conversion to convert the `1` to `true` and `0` to `false`, hence why it returns true for each comparison. However, if we were to do this with the === (tripe equal) instead we would get `false` for both: 

```js 
console.log( true === 1 ); // false 
console.log( false === 0 ); // false
```
This is because the triple equals === checks to see if they are of the same type first, we have a boolean and a number, so it immediately returns false and does not do any type conversions. 

## Strict equality

A regular equality check == has a problem. It cannot differentiate `0` from `false` as we've already seen:

```js
console.log( 0 == false ); // true
```
The same thing happens when we compare an empty string: 

```js 
console.log('' == false); // true 
```
With the == (double equals) an empty string is converted to `false` and then we have `false ==false` which returns `true`. This behavour can causes some serious problems in your code and it's usually very hard to track down. 

Now, generally you if two different values are of different types then comparing them should always return false, since they're not of the same type to begin with - how can the comparison continue? 

The strict equality operator === checks the equality without type conversion. It is different from the normal equality operator just two == it has three === equals. In other words, if `a` and `b` are of different types, then `a === b` immediately returns `false` without an attempt to convert them:

```js
console.log( 0 === false ); // false, because the types are different
```
There is also a “strict non-equality” operator `!==` analogous to `!=`. For example: 

```js
// with strict non-equality
0 !== false; // true 
// non-strict equality
0 != false; // false 
```

The strict equality operator is a bit longer to write, but makes it obvious what’s going on and leaves less room for errors. In your code, you should always use the strict equality operator - === for equality checks or !== for non equality checks. This way you can be confident that JavaScript under the hood will not make convertions and return unexpected results. 

### Exercises

What will be the result for these expressions?
```js
5 > 4 
"apple" > "pineapple" 
"2" > "12"
```
Solution:

1.  Obviously, true.
2.  Dictionary comparison, hence false. `"a"` is smaller than `"p"`.
3.  Again, dictionary comparison, first char `"2"` is greater than the first char `"1"`.

## `if`, `else if`, `if`

Conditional statements are used to perform different actions based on different conditions. Very often when you write code, you want to perform different actions for different decisions. You can use conditional statements in your code to do this. In JavaScript we have the following conditional statements:

-   Use `if` to specify a block of code to be executed, if a specified condition is true
-   Use `else` to specify a block of code to be executed, if the same condition is false
-   Use `else if` to specify a new condition to test, if the first condition is false
-   Use `switch` to specify many alternative blocks of code to be executed

### `if` statement 

Use the `if` statement to specify a block of JavaScript code to be executed if a condition is true the syntax is as follows: 

```
if (condition) {  
  //  block of code to be executed if the condition is true}
```
Example: 
```js
const hour = 15;
let greeting = '';
if (hour < 18) {  
  greeting = "Good day";  
}

console.log(greeting); // Good  day
```
The result of greeting will be `Good day`. 

### `else` Statement

Use the `else` statement to specify a block of code to be executed if the condition is false. The syntax for an `else` block is: 

```
if (condition) {  
  //  _block of code to be executed if the condition is true} 
else {  
  //  block of code to be executed if the condition is false}
```
Continuing with the hour greeting, if the hour is greater than 18 we want to assign `Good evening`:

```js
const hour = 19;
let greeting = '';
if (hour < 18) {  
  greeting = "Good day";  
} else {  
  greeting = "Good evening";  
}

console.log(greeting); // Good  evening
```

Let's look at another example, imagine a child being asked for help with a chore by their mother or father. The parent might say "Hey sweetheart! If you help me by going and doing the shopping, I'll give you some extra allowance so you can afford that toy you wanted." 

In JavaScript, we could represent this like so:
```js
let shoppingDone = prompt('Is shopping done?'); // only 'yes' or 'no' allowed
let childsAllowance;

if (shoppingDone === 'yes') {
  childsAllowance = 10;
} else {
  childsAllowance = 5;
}

console.log(childsAllowance);
```
### `else if` statement 

The last example provided us with two choices, or outcomes — but what if we want more than two? There is a way to chain on extra choices/outcomes to your `if...else` — using `else if`. 

Each extra choice requires an additional block to put in between `if () { }` and `else { }` — check out the following more involved example, which could be part of a simple weather forecast application:

```js
const choice = prompt(`
Select the weather type today:
1. Sunny
2. Rainy
3. Snowy
4. Overcast
`);

if (choice === '1') {
alert('It is nice and sunny outside today. Wear shorts! Go to the beach, or the park, and get an ice cream.');

} else if (choice === '2') {
alert('Rain is falling outside; take a rain coat and an umbrella, and don\'t stay out for too long.');

} else if (choice === '3') {
alert('The snow is coming down — it is freezing! Best to stay in with a cup of hot chocolate, or go build a snowman.');

} else if (choice === '4') {
alert('It isn\'t raining, but the sky is grey and gloomy; it could turn any minute, so take a rain coat just in case.');

} else {
alert('You didn\'t make a valid choice!');
}
```
Here we are testing for 4 conditions, if it's sunny, rainy, snow or overcast. Now, in the flow of the execution the computer will look at the choice entered by the user and then it will check againts the first `if` statement, if it it doesn't match, then it goes to the next `else if` statement and so on. 

If the user selects a value that is not in range, that is 1 - 4, then the code in the else block will be executed. This means that the `else` statement here is a 'catch-all' statement that is executed whenever any of the previous conditions could not be fulfilled. 

## Testing for boolean values implicitly 

We wanted to make a special mention of testing boolean (`true`/`false`) values, and a common pattern you'll come across again and again. 

Any value that is not `false`, `undefined`, `null`, `0`, `NaN`, or an empty string (`''`) actually returns `true` when tested as a conditional statement, therefore you can use a variable name on its own to test whether it is `true`, or even that it exists (that is, it is not undefined.) So for example:

```js
let cheese = 'Cheddar';

if (cheese) {
  console.log('Yay! Cheese available for making cheese on toast.');
} else {
  console.log('No cheese on toast for you today.');
}

// Output: Yay! Cheese available for making cheese on toast.
```
The output here will be that `Yay! Cheese available for making cheese on toast.` is logged to the console. This is because the variable `cheese` evalutes to `true` inside the parenthesis as it contains a string value and in otherwords it's _"truthy"_. 

However, if the variable container the value `null`:

```js
let cheese = null;

if (cheese) {
  console.log('Yay! Cheese available for making cheese on toast.');
} else {
  console.log('No cheese on toast for you today.');
}

// Output: Yay! No cheese on toast for you today.
```
The output is now coming from the else block because `null` evalutes to `false` in the `if` conditional check inside the parentheses. This is also called _"falsy"_ value, again any variable that contains or an expression that produces any of: 

- `false`
- `undefined`
- `null`
- `NaN`

Will evaluate to `false`, these are called falsy values and the code block after the conditional check is not executed as we have just seen. 

## Nesting if...else

It is perfectly OK to put one `if...else` statement inside another one — to nest them. For example, we could update our weather forecast application to show a further set of choices depending on what the temperature is:

```js
if (choice === '1') {
  if (temperature < 86) {
    alert(`It is ${temperature} degrees outside — nice and sunny. Let's go out to the beach, or the park, and get an ice cream.`);
  } else if (temperature >= 86) {
    alert(`It is ${temperature} degrees outside — REALLY HOT! If you want to go outside, make sure to put some sunscreen on.`);
  }
}
else if (choice === '2') {
	alert('Rain is falling outside; take a rain coat and an umbrella, and don\'t stay out for too long.');
}
...
```
Even though the code all works together, each `if...else` statement works completely independently of the other one.

## Logical operators 

There are three logical operators in JavaScript: `||` (OR), `&&` (AND), `!` (NOT). Although they are called “logical”, they can be applied to values of any type, not only boolean. Their result can also be of any type. Let’s see the details.

### `||` (OR)

The “OR” operator is represented with two vertical line symbols:

```js
let result = a || b;
```
In classical programming, the logical OR is meant to manipulate boolean values only. If any of its arguments are `true`, it returns `true`, otherwise it returns `false`.

In JavaScript, the operator is a little bit trickier and more powerful. But first, let’s see what happens with boolean values.

There are four possible logical combinations:

```js
console.log( true || true ); // true 
console.log( false || true ); // true 
console.log( true || false ); // true 
console.log( false || false ); // false
```
As we can see, the result is always `true` except for the case when both operands are `false`. If an operand is not a boolean, it’s converted to a boolean for the evaluation. For instance, the number `1` is treated as `true`, the number `0` as `false`:

```js
if (1 || 0) { 
// works just like if( true || false ) 
console.log( 'truthy!' ); 
}
```
Most of the time, OR `||` is used in an `if` statement to test if _any_ of the given conditions is `true`. For example:

```js
let hour = 9;

if (hour < 10 || hour > 18) {
	console.log( 'The office is closed.' ); 
}
```
We can pass more conditions:

```js
let hour = 12; 
let isWeekend = true; 
if (hour < 10 || hour > 18 || isWeekend) { 
	console.log( 'The office is closed.' ); // it is the weekend 
}
```
### OR "||" finds the first truthy value

The logic described above is somewhat classical. Now, let’s bring in the “extra” features of JavaScript. The extended algorithm works as follows. Given multiple OR’ed values:

```js
result = value1 || value2 || value3;
```

The OR `||` operator does the following:

-   Evaluates operands from left to right.
-   For each operand, converts it to boolean. If the result is `true`, stops and returns the original value of that operand.
-   If all operands have been evaluated (i.e. all were `false`), returns the last operand.

A value is returned in its original form, without the conversion.

In other words, a chain of OR `||` returns the first truthy value or the last one if no truthy value is found. For instance:

```js 
console.log( 1 || 0 ); // 1 (1 is truthy)

console.log( null || 1 ); // 1 (1 is the first truthy value) 

console.log( null || 0 || 1 ); // 1 (the first truthy value) 

console.log( undefined || null || 0 ); // 0 (all falsy, returns the last value)
```
This leads to some interesting usage compared to a “pure, classical, boolean-only OR”.

1. **Getting the first truthy value from a list of variables or expressions.**

For instance, we have `firstName`, `lastName` and `nickName` variables, all optional (i.e. can be undefined or have falsy values). Let’s use OR `||` to choose the one that has the data and show it (or `"Anonymous"` if nothing set):

```js
let firstName = ""; 
let lastName = ""; 
let nickName = "SuperCoder"; 
console.log( firstName || lastName || nickName || "Anonymous"); // SuperCoder
```
If all variables were falsy, `"Anonymous"` would show up.

2. **Short-circuit evaluation.**

Another feature of OR `||` operator is the so-called “short-circuit” evaluation. It means that `||` processes its arguments until the first truthy value is reached, and then the value is returned immediately, without even touching the other argument.

The importance of this feature becomes obvious if an operand isn’t just a value, but an expression with a side effect, such as a variable assignment or a function call. In the example below, only the second message is printed:
```js
true || console.log("not printed"); 
false || console.log("printed");
```
### && (AND)

The AND operator is represented with two ampersands `&&`:

```js
result = a && b;
```
In classical programming, AND returns `true` if both operands are truthy and `false` otherwise:

```js
console.log( true && true ); // true 
console.log( false && true ); // false 
console.log( true && false ); // false 
console.log( false && false ); // false
```
An example with `if`:

```js
let hour = 12; 
let minute = 30; if (hour == 12 && minute == 30) { 
	console.log( 'The time is 12:30' ); 
}
```
Just as with OR, any value is allowed as an operand of AND:

```js
if (1 && 0) { // evaluated as true && false 
	console.log( "won't work, because the result is falsy" ); 
}
```

### AND “&&” finds the first falsy value

Given multiple AND’ed values:

```js
result = value1 && value2 && value3;
```

The AND `&&` operator does the following:

-   Evaluates operands from left to right.
-   For each operand, converts it to a boolean. If the result is `false`, stops and returns the original value of that operand.
-   If all operands have been evaluated (i.e. all were truthy), returns the last operand.

In other words, AND returns the first falsy value or the last value if none were found. The rules above are similar to OR. The difference is that AND returns the first _falsy_ value while OR returns the first _truthy_ one.

Examples:

```js
// if the first operand is truthy, // AND returns the second operand: 
console.log( 1 && 0 ); // 0 
console.log( 1 && 5 ); // 5 // if the first operand is falsy, // AND returns it. The second operand is ignored 
console.log( null && 5 ); // null 
console.log( 0 && "no matter what" ); // 0
```
We can also pass several values in a row:
```js
console.log( 1 && 2 && 3 ); // 3, the last one
```
#### Precedence of AND `&&` is higher than OR `||`

The precedence of AND `&&` operator is higher than OR `||`. So the code `a && b || c && d` is essentially the same as if the `&&` expressions were in parentheses: `(a && b) || (c && d)`.

### Replace `if` with `&&`

Sometimes it's possible to replace `if` with `&&` for example: 

```js
let x = 1; 
(x > 0) && console.log( 'Greater than zero!' );
```
The action in the right part of `&&` would execute only if the evaluation reaches it. That is, only if `(x > 0)` is true.

So we basically have an analogue for:

```js
let x = 1; if (x > 0) {
	console.log( 'Greater than zero!' );
}
```
Although, the variant with `&&` appears shorter, `if` is more obvious and tends to be a little bit more readable. So we recommend using every construct for its purpose: use `if` if we want `if` and use `&&` if we want AND.

### ! (NOT)

The boolean NOT operator is represented with an exclamation sign `!`. The syntax is pretty simple:

```js
result = !value;
```
The operator accepts a single argument and does the following:

1.  Converts the operand to boolean type: `true/false`.
2.  Returns the inverse value.

For instance:

```js
console.log( !true ); // false 
console.log( !0 ); // true
```
A double NOT `!!` is sometimes used for converting a value to boolean type:

```js
console.log( !!"non-empty string" ); // true 
console.log( !!null ); // false
```
That is, the first NOT converts the value to boolean and returns the inverse, and the second NOT inverses it again. In the end, we have a plain value-to-boolean conversion. There’s a little more verbose way to do the same thing – a built-in `Boolean` function:

```js
console.log( Boolean("non-empty string") ); // true 
console.log( Boolean(null) ); // false
```
The precedence of NOT `!` is the highest of all logical operators, so it always executes first, before `&&` or `||`.

## Logical operators: Real world examples

If you want to test multiple conditions without writing nested `if...else` statements, logical operators can help you.

### AND Example

To give you an AND example, we can rewrite our prevous weather example snippet to this:

```js
let choice = 'sunny';
let temperatur = 79;

if (choice === 'sunny' && temperature < 86) {
  alert(`It is ${temperature} degrees outside — nice and sunny. Let's go out to the beach, or the park, and get an ice cream.`);
} else if (choice === 'sunny' && temperature >= 86) {
  alert(`It is ${temperature} degrees outside — REALLY HOT! If you want to go outside, make sure to put some sunscreen on.`);
}
```

The first code block will only be run if `choice === 'sunny'` _and_ `temperature < 86` return `true`. The second cod block only runs when the `choice === 'sunny'` _and_ `temperature` is equal to or greater than 86, this covers all scenarios when the choice is sunny and a temperature reading is given. 

### OR Example 

Let's look at a quick OR example:

```js
let iceCreamVanOutside = true; 
let houseStatus = 'all good';
if (iceCreamVanOutside || houseStatus === 'on fire') {
  console.log('You should leave the house quickly.');
} else {
  console.log('Probably should just stay in then.');
}
```
In this example based on the variable values we'll get: `You should leave the house quickly.` as the output. Since `iceCreamVanOutside` is set to true and hence it's a truthy value, which means with the OR check it returns that immediately and code in the `if` block is executed. 

### NOT Example

The last type of logical operator, NOT, expressed by the `!` operator, can be used to negate an expression. Let's combine it with OR in the above example:

```js
let iceCreamVanOutside = true; 
let houseStatus = 'all good';

if (!(iceCreamVanOutside || houseStatus === 'on fire')) {
  console.log('Probably should just stay in then.');
} else {
  console.log('You should leave the house quickly.');
}
```
In this snippet, if the OR statement returns `true`, the NOT operator will negate it so that the overall expression returns `false`. This means that the code in the `else` block is executed. 

### Combine logical statements 

You can combine as many logical statements together as you want, in whatever structure. The following example executes the code inside only if both OR statements return true, meaning that the overall AND statement will return true:

```js
let x = 5; 
let y = 7;
let z = 9;
let loggedIn = true;
let userName = 'Mohamed';


if ((x === 5 || y > 3 || z <= 10) && (loggedIn || userName === 'Steve')) {
  console.log('Both statements true');
}
```

### Common mistakes with OR operator 

A common mistake when using the logical OR operator in conditional statements is to try to state the variable whose value you are checking once, and then give a list of values it could be to return true, separated by `||` (OR) operators. For example:

```js
if (x === 5 || 7 || 10 || 20) {
  // run my code
}
```
In this case, the condition inside `if ()` will always evaluate to true since 7 (or any other non-zero value) always evaluates to `true`. This condition is actually saying "if x equals 5, or 7 is true — which it always is". This is logically not what we want! To make this work you've got to specify a complete test on either side of each OR operator:

```js
if (x === 5 || x === 7 || x === 10 || x === 20) {
  // run my code
}
```
## Ternary Operator 

There is one final bit of syntax you need to learn before we do some exercises. The ternary or conditional operator is a small bit of syntax that tests a condition and returns one value/expression if it is true, and another if it is false — this can be useful in some situations, and can take up a lot less code than an `if...else` block if you have two choices that are chosen between via a true/false condition. The pseudocode looks like this:

```
condition ? run this code : run this code instead
```

So let's look at a simple example:
```js
let isMorning = true;
const greeting = isBirthday
  ? console.log('Good Morning')
  : console.log('Good Evening');
```
Here we have a variable called `isMorning` — if this is `true`, we give our guest a good morning message; if not, we give a good evening message.

The above ternary expression can be rewritten with `if..else` block: 
```js
let isMorning = true;
if (isMorning) {
	console.log('Good Morning');
} else {
	console.log('Good Evening');
}
```
However, with the ternary operator it's more terse. The ternary operator is not just for setting variable values; you can also run functions, or lines of code — anything you like. The following live example shows a simple theme chooser where the styling for the site is applied using a ternary operator.

This example shows how we can use it to select a dark or light theme for a web page: 

```html 
<!DOCTYPE html>
<html lang="en-us">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width">
    <title>More color choices!</title>
  </head>
  <body>
    <label for="theme">Select theme: </label>
    <select id="theme">
      <option value="white">White</option>
      <option value="black">Black</option>
      <option value="purple">Purple</option>
      <option value="yellow">Yellow</option>
      <option value="psych">Psychedelic</option>
    </select>

    <h1>This is my website</h1>

    <script>
		const select = document.querySelector('select');
		const html = document.querySelector('html');
		document.body.style.padding = '10px';
		
		function update(bgColor, textColor) {
		  html.style.backgroundColor = bgColor;
		  html.style.color = textColor;
		}
		
		select.addEventListener('change', () => select.value === 'black'
		  ? update('black', 'white')
		  : update('white', 'black')
		);
    </script>
  </body>
</html>
```
Here we've got a [`<select>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select) element to choose a theme (black or white), plus a simple [`<h1>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/Heading_Elements) to display a website title. We also have a function called `update()`, which takes two colors as parameters (inputs). Don't worry too  much about functions, we're goig to learn about functions later on. We just need to focus on the ternary operator. 

The website's background color is set to the first provided color, and its text color is set to the second provided color.

Finally, we've also got an [onchange](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/change_event) event listener that serves to run a function containing a ternary operator. Again we're going to learn all about handlng events in an upcoming tutorial. It starts with a test condition — `select.value === 'black'`. 

If this returns `true`, we run the `update()` function with parameters of black and white, meaning that we end up with a background color of black and a text color of white. If it returns `false`, we run the `update()` function with parameters of white and black, meaning that the site colors are inverted.

## Ternary Exercise 

Link to code files in Code pen: https://codepen.io/abdi221/pen/wvXNgrG?editors=1010

For the final task you are given four variables:

-   `machineActive` — contains an indicator of whether the login machine is switched on or not (`true`/`false`).
-   `pwd` — Contains the user's login password.
-   `machineResult` — begins uninitialized, but is later used to store a response that will be printed to the output panel, letting the user know whether the machine is switched on.
-   `pwdResult` — begins uninitialized, but is later used to store a response that will be printed to the output panel, letting the user know whether their login attempt was successful.

We'd like you to create an `if...else` structure that checks whether the machine is switched on and puts a message into the `machineResult` variable telling the user whether it is on or off.

If the machine is on, we also want a second conditional to run that checks whether the `pwd` is equal to `cheese`. If so, it should assign a string to `pwdResult` telling the user they logged in successfully. If not, it should assign a different string to `pwdResult` telling the user their login attempt was not successful. We'd like you to do this in a single line, using something that isn't an `if...else` structure.

Solution

For the final task we have to offer in this set, we need you to first write an `if ... else` statement that checks whether `machineActive` is `true`. If so, set `machineResult` to a string telling the user they can successfully log in. If not, set it to a message telling them they need to activate the machine before they can log in.

Inside the `if` part of the structure, you need to write a ternary operator that checks whether `pwd` is equal to `cheese`. If so, it assigns a string saying that the login was successful; if not assign a string saying the log in failed. The result should be assigned to a variable called `pwdResult`.

Your solution should look something like this:

```js
let machineActive = true;
let pwd = 'cheese';

let machineResult;
let pwdResult;

if (machineActive) {
  machineResult = 'Machine is active. Trying login.'
  pwdResult = pwd === 'cheese' ? 'Login successful.' : 'Password incorrect; login failed.'
} else {
  machineResult = 'Machine is inactive. Activate and try logging in again.';
}
```

## Logical Exercises 

The following exercises will test your understanding of logical operators, however they use the `alert()` function as part of the test conditions, and what you need to know is that `alert()` will simply alert the value given inside the parenthesis and not actually return any value. We'll learn all about functions late ron, but just know that all functions will return a value, if the function does not explicitly return a value it returns `undefined`. 

So, back to our `alert` function, it will not return an actual value, which means that it will return `undefined` and `undefined` is a falsy value. With this note, you can now tackle the logical exercise questions. 

1. What is the code below going to output?

```js
console.log( null || 2 || undefined );
```
Solution:

The answer is `2`, that’s the first truthy value.

2. What will the code below output?
```js
console.log( alert(1) || 2 || alert(3) );
```
Solution: 

The answer: first `1`, then `2`.

The call to `alert` does not return a value. Or, in other words, it returns `undefined`. It however just alerts `1` to the user in a dialog box. 

1.  The first OR `||` evaluates its left operand `alert(1)`. That shows the first message with `1`.
2.  The `alert` returns `undefined`, so OR goes on to the second operand searching for a truthy value.
3.  The second operand `2` is truthy, so the execution is halted, `2` is returned and then shown by the outer alert.

There will be no `3`, because the evaluation does not reach `alert(3)`.

3. What is this code going to show?

```js
alert( 1 && null && 2 );
```
Solution: 

The answer: `null`, because it’s the first falsy value from the list.

4. What will this code show?
```js
alert( alert(1) && alert(2) );
```
Solution: 
The answer: `1`, and then `undefined`. The call to `alert` returns `undefined` (it just shows a message, so there’s no meaningful return).

Because of that, `&&` evaluates the left operand (outputs `1`), and immediately stops, because `undefined` is a falsy value. And `&&` looks for a falsy value and returns it, so it’s done.

5. What will the result be?

```js
alert( null || 2 && 3 || 4 );
```
Solution:
The answer: `3`.
The precedence of AND `&&` is higher than `||`, so it executes first.

The result of `2 && 3 = 3`, so the expression becomes:

`null || 3 || 4`

Now the result is the first truthy value: `3`.

6. Which of these `alert`s are going to execute? What will the results of the expressions be inside `if(...)`?
```js
if (-1 || 0) alert( 'first' ); 
if (-1 && 0) alert( 'second' ); 
if (null || -1 && 1) alert( 'third' );
```
Solution:
The answer: the first and the third will execute. Details:
```js
// Runs. // The result of -1 || 0 = -1, truthy 
if (-1 || 0) alert( 'first' ); 

// Doesn't run // -1 && 0 = 0, falsy 
if (-1 && 0) alert( 'second' ); 

// Executes // Operator && has a higher precedence than || // so -1 && 1 executes first, giving us the chain: // null || -1 && 1 -> null || 1 -> 1 
if (null || -1 && 1) alert( 'third' );
```

## Conditional Exercises 

### Simple Calendar

Link to code files on Code pen: https://codepen.io/abdi221/pen/RwJvamE

In this example, you are going to help us finish a simple calendar application. In the code you've got:

-   A [`<select>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select) element to allow the user to choose between different months.
-   An `onchange` event handler to detect when the value selected in the `<select>` menu is changed.
-   A function called `createCalendar()` that draws the calendar and displays the correct month in the [`<h1>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/Heading_Elements) element.

We need you to write a conditional statement inside the `onchange` handler function, just below the `// ADD CONDITIONAL HERE` comment. It should:

1.  Look at the selected month (stored in the `choice` variable. This will be the `<select>` element value after the value changes, so "January" for example.)
2.  Set a variable called `days` to be equal to the number of days in the selected month. To do this you'll have to look up the number of days in each month of the year. You can ignore leap years for the purposes of this example.

Hints:

-   You are advised to use logical OR to group multiple months together into a single condition; many of them share the same number of days.
-   Think about which number of days is the most common, and use that as a default value.

Solution: 

```js
let days = 31;

if(choice === 'February') {

	days = 28;

} else if(choice === 'April' || choice === 'June' || choice === 'September' || choice === 'November') {
	days = 30;
}
```
### Which Season? 

Link to code files on Code pen: https://codepen.io/abdi221/pen/mdKvrbP?editors=1010

In this task you are provided with two variables:

-   `season` — contains a string that says what the current season is.
-   `response` — begins uninitialized, but is later used to store a response that will be printed to the output panel.

We want you to create a conditional that checks whether `season` contains the string "summer", and if so assigns a string to `response` that gives the user an appropriate message about the season. If not, it should assign a generic string to `response` that tells the user we don't know what season it is.

To finish off, you should then add another test that checks whether `season` contains the string "winter", and again assigns an appropriate string to `response`.

Solution

in this task you are supposed to create your own basic `if ... else` statement that tests whether the season is summer or not, and stores an appropriate response in the `response` variable, which is then printed out in the results panel. The `else` clause should print some kind of generic response.

To finish off, you need to add an `else if` clause to also check whether it is winter, and if so, put an appropriate response inside `response`.

The finished code should look something like this:

```js
let season = 'summer';
let response;

if (season === 'summer') {
  response = 'It\'s probably nice and warm where you are; enjoy the sun!';
} else if(season === 'winter') {
  response = 'I hope you are not too cold. Put some warm clothes on!';
} else {
  response = 'I don\'t know what the season is where you are. Hope you are well.';
}
```
### Game Score

Link to code files on Code pen: https://codepen.io/abdi221/pen/VwdgKMj?editors=1010

For this task you are given three variables:

-   `machineActive` — contains an indicator of whether the answer machine is switched on or not (`true`/`false`)
-   `score` — Contains your score in an imaginary game. This score is fed into the answer machine, which provides a response to indicate how well you did.
-   `response` — begins uninitialized, but is later used to store a response that will be printed to the output panel.

You need to create an `if...else` structure that checks whether the machine is switched on and puts a message into the `response` variable if it isn't, telling the user to switch the machine on.

Inside the first, you need to nest an `if...else if...else` that puts appropriate messages into the `response` variable depending on what the value of score is — if the machine is turned on. The different conditional tests (and resulting responses) are as follows:

-   Score of less than 0 or more than 100 — "This is not possible, an error has occurred."
-   Score of 0 to 19 — "That was a terrible score — total fail!"
-   Score of 20 to 39 — "You know some things, but it\'s a pretty bad score. Needs improvement."
-   Score of 40 to 69 — "You did a passable job, not bad!"
-   Score of 70 to 89 — "That\'s a great score, you really know your stuff."
-   Score of 90 to 100 — "What an amazing score! Did you cheat? Are you for real?"

Try updating the live code below to recreate the finished example. After you've entered your code, try changing `machineActive` to `true`, to see if it works.

Solution

Task 2 tests some more complex conditionals, like not equal, less than, greater than, etc., along with a nested structure.

You are given two variables containing an indicator of the answer machine being switched on or not (`true`/`false`), and a score. You are also given an uninitialized `response` variable.

You need to create one `if ... else` structure that checks whether the machine is switched on and puts a message into the `response` variable if it isn't, telling the user to switch the machine on.

Inside the `if` part, you need to nest an `if ... else if` structure that puts appropriate messages into the `response` variable depending on different scores. The conditional operator tests should look like this:

* `score < 0 || score > 100` - "This is not possible, an error has occurred." This could also be done just by an `else` clause, as the scores between 0 and 100 are all covered by the other clauses. But it's nice to be exact.
* `score >= 0 && score < 20` - "That was a terrible score — total fail!"
* `score >= 20 && score < 40` - "You know some things, but it\'s a pretty bad score. Needs improvement."
* `score >= 40 && score < 70` — "You did a passable job, not bad!"
* `score >= 70 && score < 90` — "That\'s a great score, you really know your stuff."
* `score >= 90 && score <= 100` — "What an amazing score! Did you cheat? Are you for real?"

The finished code should look something like this:

```js
let response;
let score = 75;
let machineActive = false;

if (machineActive) {
  if (score < 0 || score > 100) {
    response = 'This is not possible, an error has occurred.';
  } else if(score >= 0 && score < 20) {
    response = 'That was a terrible score — total fail!';
  } else if(score >= 20 && score < 40) {
    response = 'You know some things, but it\'s a pretty bad score. Needs improvement.';
  } else if(score >= 40 && score < 70) {
    response = 'You did a passable job, not bad!';
  } else if(score >= 70 && score < 90) {
    response = 'That\'s a great score, you really know your stuff.';
  } else if(score >= 90 && score <= 100) {
    response = 'What an amazing score! Did you cheat? Are you for real?';
  }
} else {
  response = 'The machine is turned off. Turn it on to process your score.';
}
```
# Switch statements 

In addition to `if...else`, JavaScript has a feature known as a switch statement. switch is a type of conditional statement that will evaluate an expression against multiple possible cases and execute one or more blocks of code based on matching cases. 

The switch statement is closely related to a conditional statement containing many else if blocks, and they can often be used interchangeably.

We will learn how to use the `switch` statement, as well as how to use the related keywords `case`, `break`, and `default`. Finally, we’ll go through how to use multiple cases in a `switch` statement.

The `switch` statement evaluates an expression and executes code as a result of a matching case. The basic syntax is similar to that of an `if` statement. It will always be written with `switch () {}`, with parentheses containing the expression to test, and curly brackets containing the potential code to execute.

Below is an example of a `switch` statement with two `case` statements, and a fallback known as `default`.

```js
switch (expression) {
	case x:
		// execute case x code block
		break;
	case y:
		// execute case y code block
		break;
	case z:
		// execute case z code block
		break;
	default:
		// execute default code block
}
```
From the logic above here, this is the sequence of events that will take place:

- The expression is evaluated.
- The first `case`, `x`, will be tested against the expression. If it matches, the code will execute, and the `break` keyword will end the `switch` block.
- If it does not match, `x` will be skipped and the `y` case will be tested against the expression. If `y` matches the expression, the code will execute and exit out of the `switch` block.
- If it does not match, `y` will be skipped and the `z` case will be tested against the expression. If `z` matches the expression, the code will execute and exit out of the `switch` block.
- If none of the cases match, the `default` code block will run.

## Working example 

We're now going to use a working example to understand how the `switch` statement works, for this we're going to make use of the builtin JavaScript date features. We can get the current day of the week by using the `new Date()` method. 

This returns the current date as an object, we'll learn about objects later on, and from this object we can get the day of the week by using the `getDay()` method. 

Don't worry too much about the date object and how it works, again we're going to learn all about objects later on. 

So, to get the day we're going to use the date object and then assign that to a variable: 

```js
const day = new Date().getDay();
```
The `day` variable contains a number for each day of the week. We will find the current day of the week with the `new Date()` method, and `getDay()` to print a number corresponding to the current day. `0` stands for Sunday, all the way through `6` which stands for Saturday. 

The program will run in order from top to bottom looking for a match, and once one is found, the `break` command will halt the `switch` block from continuing to evaluate statements:

```js
// Set the current day of the week to a variable, with 0 being Sunday and 6 being Saturday
const day = new Date().getDay();

switch (day) {
	case 0:
		console.log("It's Sunday, time to relax!");
		break;
	case 1:
		console.log("Happy Monday!");
		break;
	case 2:
		console.log("It's Tuesday. You got this!");
		break;
	case 3:
		console.log("Hump day already!");
		break;
	case 4:
		console.log("Just one more day 'til the weekend!");
		break;
	case 5:
		console.log("Happy Friday!");
		break;
	case 6:
		console.log("Have a wonderful Saturday!");
		break;
	default:
		console.log("Something went horribly wrong...");
}
```
Output: 

```
'Have a wonderful Saturday!'
```
This code was tested on a Saturday, which corresponds to `4`, therefore the console output was `Have a wonderful Saturday!`. Depending on what day of the week you are testing the code, your output will be different. 

We've included a `default` block at the end to run in case of an error, which in this case should not happen as there are only 7 days of the week. 

## Multiple cases 

You may encounter code in which multiple cases should have the same output. In order to accomplish this, you can use more than one `case` for each block of code.

In order to test this, we are going to make a small application matching the current month to the appropriate season. First, we will use the `new Date()` method to find a number corresponding to the current month, and apply that to the `month` variable:

```js
const month = new Date().getMonth();
```
The `new Date().getMonth()` method will output a number from `0` to `11`, with `0` being January and `11` being December. At the time of this publication, the month is September, which will correspond to `8`.

Our application will output the four seasons with the following specifications for simplicity:

-   **Winter**: January, February, and March
-   **Spring**: April, May, and June
-   **Summer**: July, August, and September
-   **Autumn**: October, November, and December

```js
// Get number corresponding to the current month, with 0 being January and 11 being December
const month = new Date().getMonth();

switch (month) {
	// January, February, March
	case 0:
	case 1:
	case 2:
		console.log("Winter");
		break;
	// April, May, June
	case 3:
	case 4:
	case 5:
		console.log("Spring");
		break;
	// July, August, September
	case 6:
	case 7:
	case 8:
		console.log("Summer");
		break;
	// October, November, December
	case 9:
	case 10:
	case 11:
		console.log("Autumn");
		break;
	default:
		console.log("Something went wrong.");
}
```
Now depending on when you run the code, it will output a season based on the month. When this code is run it outputs: 
```
Autumn
```
`switch` evaluates an expression and outputs different values based on matching results. You can read more about switch on MDN: <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/switch"  target="_blank">Switch</a>. 

## Switch Exercise 

Link to code files on Code pen: https://codepen.io/abdi221/pen/MWXLJWJ?editors=1010

In this task you need to take the code we wrote for the ternary task, and rewrite the inner `if...else if...else` to use a `switch` statement instead.

In this example, you are going to take the ternary operator example we saw earlier and convert the ternary operator into a switch statement to allow us to apply more choices to the simple website. Look at the `select`— this time you'll see that it has not two theme options, but five. You need to add a switch statement just underneath the `// ADD SWITCH STATEMENT` comment:

-   It should accept the `choice` variable as its input expression.
-   For each case, the choice should equal one of the possible `<option> value`s that can be selected, that is, `white`, `black`, `purple`, `yellow`, or `psychedelic`.
-   For each case, the `update()` function should be run, and be passed two color values, the first one for the background color, and the second one for the text color. Remember that color values are strings, so they need to be wrapped in quotes.

Solution: 
```js
const choice = select.value;

switch(choice) {

	case 'black':
		update('black','white');
		break;
	case 'white':
		update('white','black');
		break;
		case 'purple':
		update('purple','white');
	break;
		case 'yellow':
		update('yellow','darkgray');
	break;
		case 'psych':
		update('lime','purple');
	break;
	}
}

function update(bgColor, textColor) {

html.style.backgroundColor = bgColor;

html.style.color = textColor;

}
```
# Knowledge check 

1. Which data type does the number `65` belong to? 
2. Which data type does `true` belong to? 
3. Which data type is NOT primitive?
4. What is the difference between single, double, and backtick quotes for strings? 
5. What is the term for embedding variables/expressions in a string? 
6. Which type of quote lets you embed variables/expressions in a string? 
7. How do you embed variables/expressions in a string? 
8. How do you escape characters in a string? 
9. What is the difference between the slice and substr string methods? 
10. What are the three logical operators and what do they stand for? 
11. What are the comparison operators? 
12. What are truthy and falsy values? 
13. What are the falsy values in JavaScript? 
14. What are conditionals? 
15. What is the syntax for an if/else conditional? 
16. What is the syntax for a switch statement? 
17. What is the syntax for a ternary operator? 
18. What is conditional nesting?

