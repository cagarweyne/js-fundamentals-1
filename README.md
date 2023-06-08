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
