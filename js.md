# JavaScript

### JS CheatSheet

<details><summary></summary>

### JS CheatSheet

### connect script

```html
<head>
  ...
  <script src="./js/index.js" defer></script>
</head>
<body>
  ...
</body>
```

---

### `document` `.querySelector()`

```html
<body>
  <main class="main" id="main" data-js="main">...</main>
</body>
```

```js
const mainElement = document.querySelector('[data-js="main"]');
```

---

### `.addEventListener`

```js
const button = document.querySelector('[data-js="button"]');
button.addEventListener("click", () => {});
```

---

### `.classList.`

```js
const main = document.querySelector('[data-js="main"]');
const button = document.querySelector('[data-js="button"]');
button.addEventListener("click", () => {
  main.classList.add("page--primary"); // add|remove|toggle|...
});
```

---

### `.createElement`

```js
const article = document.createElement("article");
const button = document.createElement("button");
```

ist dann erstmal in der variablen gespeichert  
jetzt:  
`.classList.add()`  
`.textContent`
`container` `.append()`

---

### `.append`

```js
document.body.append(article); // placing the created article at the end of the body
article.append(button); // placing the created button into the article
```

---

### prevent default

```js
const form = document.querySelector('[data-js="form"]');

form.addEventListener("submit", (event) => {
  event.preventDefault();
});
```

</details>

<!-- ---------- ---------- ---------- ---------- ---------- ---------- -->
<!-- ---------- ////////// ---------- ---------- ////////// ---------- -->
<!-- ---------- ---------- ---------- ---------- ---------- ---------- -->

## JS Basics

<details>
<summary>ConnectJavascript | QuerySelector | AddEventListener | AddRemoveToggle-Classes</summary>

## JS Basics

### connect a JavaScript file

The `<script>`-Tag has two attributes:  
`src="./index.js"` sets the URL to Javascript file _index.js_  
`defer` tells browser to **delay the loading of script** until _all HTML elemens_ are loaded

```html
<head>
  ...
  <script src="./js/index.js" defer></script>
</head>
<body>
  ...
</body>
```

---

### log/print to console

In JavaScript we can print text to the console of the web browser. We can use this for debugging or error logging for example.

```js
console.log("Hello World!"); // logs into console
console.clear(); // clears console
console.error("Error!"); // logs as error into console
```

---

### selecting HTML Elements: `querySelector()`

before adding interactivity, we need to select the necessary HTML-Elements:

```html
<body>
  <main class="main" id="main" data-js="main">...</main>
</body>
```

> 🧩 Best practise: to select the above `main` section within JavaScript:  
> Use _data-\*_ attribute like the `data-js`:

`const mainElement = document.querySelector('[data-js="main"]');`

> ❌ Other CSS Selectors work as well, but the _data-\*_ attribute selector schould be preferred.  
> Here are the others:
>
> ```js
> const mainElement = document.querySelector("main"); // tag as identifier
> const mainElement = document.querySelector(".main"); // class as identifier -> .
> const mainElement = document.querySelector("#main"); // id as identifier -> #
> ```
>
> 💡 We try to keep it seperated: Classes for CSS // _data-\*_ attributes for JavaScript

---

### adding interaction: `.addEventListener()`

We can listen to events like **clicks** on an Element and Execute code, when the event is triggered.  
The _method_ `addEventListener` reacts to events.

```html
<button type="button" data-js="button">Log into console</button>
```

```js
const button = document.querySelector('[data-js="button"]');
button.addEventListener("click", () => {});
```

- First you **specify** the kind of event, e.g. _click_ , _mouseover_ or [more event-types](https://developer.mozilla.org/en-US/docs/Web/Events#event_listing)
- Then you **define** what _code to execute_ when the event is _triggered_
- Code to execute between `{}` in this e.g. `console.log()`

```js
const button = document.querySelector('[data-js="button"]');
button.addEventListener("click", () => {
  console.log("Yeah");
});
```

---

### add/remove/toggle classes: `.classList.`

You can **add, remove** and **toggle** classes, e.g. for styling of an element.

```html
<main data-js="main">
  <button type="button" data-js="button">Add a class</button>
</main>
```

Add **page--primary** class to the above main section by using the `selectedElement.classList.add`
method:

```js
const main = document.querySelector('[data-js="main"]');
const button = document.querySelector('[data-js="button"]');
button.addEventListener("click", () => {
  main.classList.add("page--primary");
});
```

A click on the button adds the class **page--primary** to the main element:

```html
<main data-js="main" class="page--primary">
  <button type="button" data-js="button">Add a class</button>
</main>
```

You can also remove or toggle a class in the same way:

```js
main.classList.remove("page--primary");
```

```js
main.classList.toggle("page--primary");
```

---

#### Resources - basics

[Document](https://developer.mozilla.org/en-US/docs/Web/API/Document)  
[Using data attributes](https://developer.mozilla.org/en-US/docs/Learn/HTML/Howto/Use_data_attributes)  
[document.querySelector](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector)  
[data-\* attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/data-*)  
[.addEventListener()](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener)  
[Event reference](https://developer.mozilla.org/en-US/docs/Web/Events#event_listing)  
[classList](https://developer.mozilla.org/de/docs/Web/API/Element/classList)

---

---

</details>
<!-- ---------- ---------- ---------- ---------- ---------- ---------- -->
<!-- ---------- ////////// ---------- ---------- ////////// ---------- -->
<!-- ---------- ---------- ---------- ---------- ---------- ---------- -->

## JS Variables and numbers

<details>
<summary>Declaration | DataTypes | Operators | TypeCoersion | NumberSystems</summary>

## JS Variables and numbers

### variable declaration

Variables are a **reference** or **alias** for data stored in memory. You can access this data by using this variable.

- `const` declares a **constant**, the value **can't be changed**.  
  // default way to declare variables.
- `let` declares a **variable**, the value **can be changed**.  
  // only used, when reassingning
- `var` OUTDATED, not use anymore

```js
const aNewVariable = 1234;
```

The keyword `let` is only used when you need to reassign a value, for example when you want to
increase a counter.

```js
let counter = 0;
counter = counter + 1; // reassigning the value of counter
```

> 🧩 BestPractise: Expressive variable names are very important for the `readability of the code`. The Code becomes
> easier to understand and needs less comments. There are some key guidelines you should follow when
> naming a variable:
>
> - use camel case: `socialFeedEntry` instead of `socialfeedentry`
> - write out all words: `error` instead of `e`, `followerButton` instead of `flBtn`
> - be very specific, longer names are better than shorter: `updatedFollowerCounter` instead of
>   `counter`.

> 💡 The `=` sign in programming doesn't quite work like the mathematical equality that you (maybe)
> remember from school. It means: "the value of the item on the right of the equal sign is saved in
> the item on the left of it". What the item on the right actually represents is calculated first and
> saved afterwards.

---

### Primitive Data Types

JavaScript is a dynamically typed language, which means, that you don't have to specify what kind of
value you want to store, JavaScript detects this automatically.

There are 7 primitive data types:

| type        | represents                                                                                                                  | syntax                                                     |
| ----------- | --------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------- |
| `string`    | a sequence of characters: "abcd"                                                                                            | `const varName = "hello you.";` `const varName = "12345";` |
| `number`    | a number: 1234                                                                                                              | `const varName = 12345;` `const varName = 0.123;`          |
| `boolean`   | a binary statement, can be `true` or `false`                                                                                | `const varName = true;` or `const varName = false;`        |
| `null`      | represents "nothing", is typically set by developers                                                                        |
| `undefined` | represents the state of "not existing". Anything not specified or not found in JavaScript defaults to the value `undefined` |
| `BigInt`    | uncommon, used for integers larger than 9007199254740991                                                                    |
| `Symbol`    | uncommon, used for creating unique elements                                                                                 |

---

### Math & Operators

As a programmer you sometimes have to use mathematical operations to calculate certain widths or
positions of elements. Operators calculate values based on one or two expressions.

| operator | effect                                                                                       | syntax                     |
| -------- | -------------------------------------------------------------------------------------------- | -------------------------- |
| `+`      | adds two numbers together.                                                                   | `result = vari1 + vari2;`  |
| `-`      | subtracts two numbers                                                                        | `result = vari1 - vari2;`  |
| `*`      | multiplies two numbers                                                                       | `result = vari1 * vari2;`  |
| `/`      | divides two numbers                                                                          | `result = vari1 / vari2;`  |
| `**`     | potentiates two numbers: `2 ** 4 → 16`                                                       | `result = vari1 ** vari2;` |
| `%`      | The remainder or modulus. Gives you what remains after a whole number division: `8 % 3 → 2`. | `result = vari1 % vari2;`  |

> 💡 Operator Precedence  
> In maths, some operators have a higher precedence than others. This means that they are performed
> before operators with a lower precedence. For example, multiplication comes before addition.
>
> > 📙 You can read more about [**Operator precedence** in the mdn](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence).
>
> > 💡 If you are uncertain, use parentheses around calculations to denote precendence manually. Prettier
> > will remove any unnecessary parentheses from your expression automatically.

The **remainder** is a very useful operator, but might be difficult to understand at first. A real life
example would be time on a clock. After noon, you don't reach 13am but you start over at 1pm. 3
hours after midnight you don't have 15pm (or 27h in the 24h format), but 3am. It is whatever hour we
have mod 12:

```js
5 % 12; // → 5
12 % 12; // → 0
13 % 12; // → 1
15 % 12; // → 3
27 % 12; // → 3
```

You can also use this operator to determine if a number is even or odd:

```js
6 % 2; // → 0
```

This is `0` for all **even** numbers, because after dividing an even number by `2` nothing remains.

```js
5 % 2; // → 1
```

This is `1` for all **odd** numbers, because after this division you have always `1` left over.

---

### Assignment Operators

You already know the default assignment operator `=`. This operator just assigns the value on the
right to the element on the left. There are more assignment operators for very common actions like
increasing a variable by a fixed value.

| operator | effect                                                                                                               |
| -------- | -------------------------------------------------------------------------------------------------------------------- |
| `+=`     | Increases the value of the variable on the left about the value on the right: `count += 6` → count is increased by 6 |
| `-=`     | Decreases the value of the variable on the left about the value on the right                                         |
| `*=`     | Multiplies the variable on the left with the value on the right                                                      |
| `/=`     | Divides the variable on the left with the value on the right                                                         |
| `++`     | Increments the value of a variable by one: `count++` → count is increased by one                                     |
| `--`     | Decrements the value of a variable by one: `count--` → count is decreased by one                                     |

### Type Coersion

When you use an operator with a variable with an **unfitting type**, JavaScript will **automatically**
**convert (coerse)** this variable into a fitting type. For example:

```js
4 / "2"; // → 4 / 2
```

There is no "/" operator for strings, so JavaScript converts the string into a number if possible.
This is also true for boolean operators which we will cover in a later session.

> ❗️ There is another `+` operator in JavaScript, that links two strings together: `"a" + "b"` →
> `"ab"`. When 'adding' a number and a string, the number is converted to a string: `"a" + 6` → `"a6"`.
> Make sure that both variables are numbers if you want to add them.
> 📙 Read more about [**Type coersion** in the mdn](https://developer.mozilla.org/en-US/docs/Glossary/Type_coercion).

---

### Number Systems

When working with computers, it is sometimes useful to work with a different number system than the
standard 10 digit system, since a computer only understands `binary` numbers composed of only 0
and 1. You don't have to learn these systems by heart, but it is good if you heard about them.

- `decimal system`: the standard numbers, has 10 symbols "0" to "9".
- `binary system`: only has 2 symbols "0" and "1". If you want to write a bigger number than 1, you
  add another digit: 2 → "10" in binary.
- `hexadecimal system`: has 16 symbols "0" to "9" and "a" to "f". If you want to write a number
  bigger than 15 you add another digit: 12 → "c" in hexadecimal.

---

#### Resources - variables and numbers

- [Operator Precedence in the mdn](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence)
- [Type coersion in the mdn](https://developer.mozilla.org/en-US/docs/Glossary/Type_coercion)

---

---

</details>
<!-- ---------- ---------- ---------- ---------- ---------- ---------- -->
<!-- ---------- ////////// ---------- ---------- ////////// ---------- -->
<!-- ---------- ---------- ---------- ---------- ---------- ---------- -->

## JS Conditions and Booleans

<details>
<summary>
Boolean | TruthlyFalsely | Comparison+Logical-Operator | If-Else | Ternary % | AdvancedBoolean
</summary>

## JS Conditions and Booleans

### Boolean values

A boolean value, named after George Boole, only has two states. It can either be **true** or
**false**. Booleans are often used in conditional statements which can execute different code
depending on their value.

### Truthy and Falsy Values

Sometimes you want to have a condition depending on another type of value. JavaScript can transform
any value into a boolean with _type coercion_. That means that some values act as if they were true
and others as if they were false: _Truthy_ values become true, _falsy_ values become false.

- _truthy_ values:

  - non zero numbers: `1`, `2`, `-3`, etc.
  - non empty strings: `"hello"`
  - `true`

- _falsy_ values:
  - `0` / `-0`
  - `null`
  - `false`
  - `undefined`
  - empty string: `""`

---

### Comparison Operators

Comparison operators produce boolean values by comparing two expressions:

| Operator  | Effect                                                                           |
| --------- | -------------------------------------------------------------------------------- |
| A `===` B | strict equal: is `true` if both values are equal (including their type).         |
| A `!==` B | strict not equal: is `true` if both values are not equal (including their type). |
| A `>` B   | strictly greater than: is `true` if A is greater than B.                         |
| A `<` B   | strictly less than: is `true` if A is less than B.                               |
| A `>=` B  | greater than or equal: is `true` if A is greater than or equal B.                |
| A `<=` B  | less than or equal: is `true` if A is less than or equal B.                      |

> 💡 You might notice that JavaScript uses three equal signs (`===`) to check for equality. This can
> seem very strange at first.
>
> - `=` (`const x = 0`) is the assignment operator and has nothing to do with comparison.
> - `==` and `!=` are non-strict equality operators. You should **avoid them 99% of the time**.  
>   Non-strict equality tries to use type coercion to convert both values to the same type:
>   `"3" == 3` is `true`, which is seldomly what you want.
> - `===` and `!==` are strict equality operators. **This is what you need almost always**.  
>   Strict equality checks if type _and_ value are the same: `"3" === 3` is `false`.

---

### Logical Operators

Logical operators combine up to two booleans into a new boolean.

| Operator                      | Effect                                                 |
| ----------------------------- | ------------------------------------------------------ |
| `!`A                          | `not`: flips a `true` value to `false` and vice versa. |
| A <code>&#124;&#124;</code> B | `or`: is `true` if either A `or` B is true.            |
| A `&&` B                      | `and`: is `true` if both A `and` B is true.            |

> 💡 You can combine logical operators with brackets to define which operator should be evaluated
> first, e.g:
>
> - `(A || B) && (C || D)`
> - `!(A || B)`
>   💡 Be careful when using `&&` or `||` with non-boolean values. They actually return one of the
>   original values. That can be useful, but can also quickly lead to confusion. This behaviour is
>   called
>   [short-circuit evaluation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_AND#short-circuit_evaluation)
>   and is a more advanced topic.
>
> - `"some string" || "some other string"` evaluates to `"some string"`
> - `0 || 100` evaluates to `100`
> - `null && "yet another string"` evaluates to `null`

---

### Control Flow: `if / else`

With an if statement we can control whether a part of our code is executed or not, based on a
condition.

```js
const isSunShining = true;
if (isSunShining) {
  // code that is executed only if condition "isSunShining" is true
}
```

The else block is executed only if the condition is `false`.

```js
const isSunShining = false;
if (isSunShining) {
  // code that is executed only if condition "isSunShining" is true
} else {
  // code that is executed only if condition "isSunShining" is false
}
```

The condition expression between the `()` brackets can be composed of logical or comparison
operators as well. You can distinguish between more cases by chaining `else if` statements:

```js
if (hour < 12) {
  console.log("Good Morning.");
} else if (hour < 18) {
  console.log("Good afternoon.");
} else if (hour === 24) {
  console.log("Good night.");
} else {
  console.log("Good evening.");
}
```

If the condition is not a boolean, it is converted into one by type coercion. This can be used to
check whether a value is not 0 or an empty string:

```js
const name = "Alex";
if (name) {
  console.log("Hi " + name + "!"); // only executed if name is not an empty string
}
```

---

### Ternary Operator: `? :`

With if / else statements whole blocks of code can be controlled. The ternary operator can be used
if you want to decide between two _expressions_, e.g. which value should be stored in a variable:

```js
const greetingText = time < 12 ? "Good morning." : "Good afternoon.";
```

The ternary operator has the following structure:

```js
condition ? expressionIfTrue : expressionIfFalse;
```

If the condition is true, the first expression is evaluated, otherwise the second expression. The
ternary operator can be used to decide which function should be called:

```js
isUserLoggedIn ? logoutUser() : loginUser();
```

It can also distinguish which value should be passed as an argument to a function:

```js
moveElement(xPos > 300 ? 300 : xPos); // the element can't be moved further than 300.
```

> ❗️ The operator can only distinguish between two _expressions_ like values, math / logical
> operations or function calls, not between _statements_ like variable declarations, if / else
> statements or multi-line code blocks.

---

### Advanced: The strangeness of boolean coercion and making use of non-strict equality

<details>
<summary>🫣 This is an advanced topic and not important for the challenges. Click to expand if you're curious.</summary>

Assume you want to check if a variable has a useful value for us to work with. `if(variable)` does
in fact not check if `variable` is defined but rather if it is truthy. Take a look at these
examples:

- `if(undefined)` → falsy, won't execute
- `if(null)` → falsy, won't execute
- `if("")` → falsy, won't execute, but might still be a useful variable  
  (e.g. when user clears an input field)
- `if(0)` → falsy, won't execute, but might still be a useful variable  
  (e.g. when user wants to set the volume to `0`)
- `if(" ")` → truthy, will execute
- `if(-1)` → truthy, will execute

It's useful to define a variable as not having a value when it's `undefined` or `null`. We can check
for that like this:

```js
if (variable != null) {
  console.log('This will be logged even if variable is 0 or ""');
}
```

This is one of the rare valid use cases for non-strict comparison (`!=` instead of `!==`).

JavaScript tries to coerce the compared values into the same type. And just like `"3" == 3` is
`true`, `undefined == null` is also `true`. This also works with `!=` instead of `==`.

> ⚠️ Remember that this is an exception for using non-strict equality. **Strict equality should
> otherwise always be preferred.**

</details>

---

#### Resources - conditions and boolean

[MDN Comparison Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#comparison_operators)
[MDN Logical Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#logical_operators)
[MDN about if else](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else)
[MDN Ternary Operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator)

---

---

</details>
<!-- ---------- ---------- ---------- ---------- ---------- ---------- -->
<!-- ---------- ////////// ---------- ---------- ////////// ---------- -->
<!-- ---------- ---------- ---------- ---------- ---------- ---------- -->

## JS Function

<details>
<summary>FuncDeclaration | Parameters | FunctionCall | Scopes | ReturnStatements | ArrowFunction</summary>

## JS Function

Functions are a fundamental concept in JavaScript. They contain a set of statements - in other
words: They contain JavaScript code. Functions have to be defined. When a function is defined it can
be called an arbitrary number of times.

---

### Function Declarations

You can define a function using a **function declaration** which consists of:

- the function keyword
- the function name
- the function body (JavaScript statements / JavaScript code)

```js
function greet() {
  console.log("Hi Friends!");
  console.log("Nice to be here.");
}
```

> ❗️ Defining a function does not cause the JavaScript code in the function body to be executed.
> You have to call the function for the code to be executed.

### Parameters

Functions can accept parameters. Parameters can be used like predefined variables inside the
function body. When declaring a function we are free to choose a name for the parameters, but
descriptive, short names should be chosen.

```js
function printLetter(name) {
  console.log("Hi " + name + ", hope you are fine. Love, Johnny");
}
function printSum(first, second, third) {
  const sum = first + second + third;
  console.log("The sum of your numbers is: " + sum);
}
```

---

### Function Calls

When functions are defined you can call them by writing their name, followed by parentheses
("round brackets"). If the functions consume parameters you can pass them as arguments in the
brackets.

```js
greet();
/*
This will cause the following to be logged into the console:
Hi Friends!
Nice to be here.
*/
printLetter("Max");
printLetter("Jordan");
/*
This will cause the following to be logged into the console:
Hi Max, hope you are fine. Love, Johnny
Hi Jordan, hope you are fine. Love, Johnny
*/
printSum(1, 2, 3);
printSum(3, 4, 5);
/*
This will cause the following to be logged into the console:
The sum of your numbers is: 6
The sum of your numbers is: 12
*/
```

---

### Scope

The scope defines where variables are visible and where they can be referenced. In JavaScript there
are different kinds of scope, for example:

- global scope
- function scope

### Function scope

Variables defined **inside a function** are not accessible from outside. But all variables **outside
of the function** can be accessed from inside the function body:

```js
const globalVariable = "some Text";
function myFunction() {
  const localVariable = true;
  console.log(globalVariable);
  console.log(localVariable);
}
myFunction();
// logs:
// some Text
// true
console.log(localVariable); // Error! Variable not available outside of function
```

### Global scope

A variable is in the **global scope** when it is declared outside of any function, in a JavaScript
file. Global variables are visible and can be accessed from anywhere in that JavaScript file after
declaration.

---

### Return Statements

Functions are an incredible versatile and central tool in most programming languages. We already
learned how to pass values into a function with input parameters. But a function can also return a
value back to the place where it was called. This is done via a `return statement`.

```js
function add3Numbers(first, second, third) {
  const sum = first + second + third;
  return sum;
}
```

The `return statement` begins with the keyword `return` followed by an expression. This this case,
the expression is the variable sum. Its value is returned by the function and can be stored when the
function is called:

```js
const firstSum = add3Numbers(1, 2, 3);
// the return value is stored in "firstSum", namely 6

const secondSum = add3Numbers(4, 123, 33);
// the return value is now stored in "secondSum", namely 160
```

> 💡 An expression is anything that produces a value: a variable, a hardcoded value like `true` or
> `6`, a math operation like `2 + 3` or even another function call!
> [This article](https://www.joshwcomeau.com/javascript/statements-vs-expressions/) explains this in
> greater depth.

By this, we can outsource computations and / or decision processes and continue using the returned
value in the program.

A function can return only one expression value, but can have multiple return statements, in
combination with if else statements for example:

```js
function checkInputLength(inputString) {
  if (inputString.length > 3) {
    return true;
  } else {
    return false;
  }
}
```

### Early Return Statements

As soon as a return statement is reached in a function call, the function execution is ended. The
following `console.log()` is therefore never reached:

```js
function testFunction() {
  return "a returned string";

  console.log("I am never logged in the console.");
}
```

This behavior can be used to our advantage as early return statements. Sometimes we want to execute
certain parts of our code only if a condition applies. We can check this with an if else statement.
When multiple conditions are in place, the code becomes harder to read and to understand:

```js
function setBackgroundColor(color) {
  if (typeof color === "String") {
    if (color.startsWith("#")) {
      if (color.length >= 7) {
        document.body.style.backgroundColor = color;
      }
    }
  }
}
```

An alternative approach is to terminate the function with early return statements:

```js
function setBackgroundColor(color) {
	// first condition
	if(typeOf color !== 'String') {
		return;
	}

	// second condition
	if(!color.startsWith('#')) {
		return;
	}

	// third condition
	if(color.length < 7) {
		return;
	}

	// only if all 3 conditions are passed the final line of code is executed.
	body.style.backgroundColor = color;
}

```

This way of writing the code is more readable

💡 Hint: A return statement can be left empty, the returned value is then `undefined`.

### Arrow Function Expressions

Next to the classic function declaration, JavaScript has a second way to write functions as
`arrow function expressions`:

```js
const addNumbers = (first, second) => {
  return first + second;
};
```

The function is saved like a variable with the keyword `const`. The parameters are written normally
in round brackets followed by an fat arrow `=>`. Then the function body is written in curly
brackets.

### Implicit Return Statements

The advantage of arrow functions are possible shorter notations when certain criteria apply:

1. Omit the round brackets around the parameters: This is possible, if there is only one input:
   ```js
   const addOne = (number) => {
     return number + 1;
   };
   ```
2. Implicit return statements: If the function consists only of a return statement, the curly
   brackets and the return keyword can be omitted:
   ```js
   const addNumbers = (first, second) => {
     return first + second;
   };
   ```
   can be rewritten as:
   ```js
   const addNumbers = (first, second) => first + second;
   ```

> 💡 This shorthand notation comes in handy as soon as we work with callback functions in a few
> days. So try to remember this feature.

> 💡 Maybe you remember the syntax of the `addEventListener` method. We encountered these arrow
> functions there already!
>
> ```js
> button.addEventListener('click',() => {
> 	...
> })
> ```

---

#### Resources

[MDN docs: Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions)
[MDN docs: Scope](https://developer.mozilla.org/en-US/docs/Glossary/Scope)

---

---

</details>
<!-- ---------- ---------- ---------- ---------- ---------- ---------- -->
<!-- ---------- ////////// ---------- ---------- ////////// ---------- -->
<!-- ---------- ---------- ---------- ---------- ---------- ---------- -->

## Strings

<details><summary>TemplateLiterals | StringProperties | InputFields</summary>

## Strings

There are three ways to create strings using _string literals_:

1. `'string'`: single quotes
2. `"string"`: double quotes
3. `` `string` ``: back ticks or **template literals**.

> 💡 In general there is no preference for using either single or double quotes, except for stylistic
> reasons. Tools like prettier convert all strings to use the same style quotes. We have configured
> prettier to use double quotes by default. One reason to prefer one style of quotes over another on
> a case-by-case basis is when a quotation mark is part of the string:
>
> - `"It's such a nice day!"`
> - `'"Nice work", they said.'` or `'[data-js="foo"]'`
>
> Prettier detects these cases automatically.

Strings can be chained together by using the `+` operator (yes, the same as the maths operator).
This is called **string concatination**:

```js
const name = "Alex";
const stringConcatination = "Hello " + name + ", good to see you!";
```

### Template Literals

The third method to write strings has the useful property that you can insert variables into the
string by wrapping placeholders with a dollar sign and curly brackets `${}` . This is also called
**string interpolation**.

This way you don't have to concat multiple strings if you want to use a variable in your string:

```js
const stringConcatination = "Hello " + name + ", good to see you!";

const withTemplateString = `Hello ${name}, good to see you!`;
```

Any **expression** can be placed into these placeholders:

```js
const greeting = `Hello ${
  name !== null ? name : "mysterious person"
}, good to see you!`;
```

With template literals you can also write **multi-line strings**:

```js
`Hello,
this is in a new line.
Good bye!`;
```

### String Properties and Methods

Strings in JavaScript have some build-in **properties** and functionalities called **methods**. You
can call them with the dot notation followed by the name of the property / method.

```js
"A normal string".length; // evaluates to 15
"A normal string".toUpperCase(); // evaluates to "A NORMAL STRING"
```

> 💡 Methods are functions, thus they need to be invoked by placing `()` brackets after the name of
> the method.

| Property / Method                   | Effect                                                                   |
| ----------------------------------- | ------------------------------------------------------------------------ |
| `.length`                           | returns the number of characters in a string.                            |
| `.toUpperCase()`                    | returns a all uppercase version of the string.                           |
| `.toLowerCase()`                    | returns a all lowercase version of the string.                           |
| `.trim()`                           | returns a string with all whitespace removed from the beginning and end. |
| `.replaceAll(oldString, newString)` | replaces all occurrences of `oldString` with the `newString`.            |
| `.startsWith(subString)`            | returns `true` if the string starts with subString.                      |
| `.endsWith(subString)`              | returns `true` if the string ends with subString.                        |
| `.includes(subString)`              | returns `true` if the string contains the subString.                     |

> 💡 Go to the
> [MDN Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#instance_properties)
> for even more string methods.

---

### Input Fields

Every input field in HTML holds a **value** in form of a string. You can access the value by using
`.value` on the input Element:

```html
<form>
  <input data-js="textInput" type="text" value="test 123" />
  <input data-js="numberInput" type="number" value="42" />
</form>
```

```js
const textInput = document.querySelector('[data-js="textInput"]');
const numberInput = document.querySelector('[data-js="numberInput"]');

textInput.value; // evaluates to 'test 123'
numberInput.value; // evaluates to '42' (still a string!)
```

You can also change the value of the input by assigning a new value to this input property:

```js
textInput.value = "changed value!";
```

This change is immediately visible on the website.

For example, you can enforce all uppercase letters in a form by combining this functionality with an
`input` event listener on the input element:

```js
// transform on every change the input value to uppercase letters
textInput.addEventListener("input", () => {
  const oldValue = textInput.value;
  const newValue = oldValue.toUpperCase();
  textInput.value = newValue;
});
```

---

#### Resources

## [MDN Docs: String Methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#instance_properties)

---

---

</details>
<!-- ---------- ---------- ---------- ---------- ---------- ---------- -->
<!-- ---------- ////////// ---------- ---------- ////////// ---------- -->
<!-- ---------- ---------- ---------- ---------- ---------- ---------- -->

## Arrays [ ] + Objects { }

<details><summary>CommonArray Attributes+Methods | Objects | NestedObjects+Arrays | </summary>

## Arrays [ ] + Objects { }

### Array [ ]

Arrays are a structured data type which can store multiple values in one variable.

You can declare an array using `[]` square brackets (array literals):

```js
const shoppingList = ["apple", "tomato"];
```

Each item in the array has an **index**, which **starts at 0**. You can access individual items using the
bracket notation and the item's index:

```js
shoppingList[0]; // "apple"
shoppingList[1]; // "tomato"
```

Arrays can hold any type of value, even another array. This is called a **nested array**. The values of
nested arrays can be accessed by choosing the index of the nested array first and then stating the
index of the element inside the nested array.

```js
const nestedArray = ["a", 1, ["a", "new", "sentence"], false];
nestedArray[2][1]; // "new"
```

> 🧩 BestPractise: Keep it simple. Better one type of value per Array, except you need it. e.g. Array inside Array

You can **overwrite** individual **values** in an array:

```js
const shoppingList = ["apple", "tomato"];
shoppingList[0] = "banana";
shoppingList; // ["banana","tomato"];
```

### Common Array Attributes and **Methods**

| Attribute / Method       | Effect                                           |
| ------------------------ | ------------------------------------------------ |
| `array.length`           | returns the number of elements in the array      |
| `array.push(element)`    | adds `element` to the end of the array           |
| `array.pop()`            | removes the last element of an array             |
| `array.unshift(element)` | adds `element` as the first element of the array |
| `array.shift()`          | removes the first element of the array           |

> 💡 There are much more array methods and attributes which we will discover in later sessions. Go
> to the
> [MDN Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#instance_methods)
> for more information.

> 💡 Für ein **Array** kann man die Variable `const` verwenden, obwohl `const` normalerweise eine Wert-veränderung ausschließt. Der Variablen ist ein Array zugewiesen, _dessen Inhalt_ wir verändern und kein spezifischer Wert, den wir verändern

---

### Objects { }

Objects are a structured data type, which couple their values not to an index, but to a unique key.

You can declare an object using `{}` curly brackets (object literals):

```js
const person = {
  name: "Max Paddington", // KEY -> name   // VALUE -> "Max Peddington"
  age: 21, // KEY -> age   // VALUE -> 21
  isStudent: false, // KEY -> isStudent   // VALUE -> false
};
```

You can access the properties using the dot notation:

```js
person.name; //"Max Paddington"
```

You can also access the properties using the bracket notation:

```js
person["age"]; // 21
```

Objects can be nested:

```js
const person = {
  name: "Max Paddington",
  age: 21,
  isStudent: false,
  address: {
    street: "Berliner Str.",
    houseNumber: 42,
    city: "Leipzig",
    zipCode: "12345",
  },
};
```

Nested values can be **accessed by** chaining the **dot notation** and/or the bracket notation together.

```js
person.address.street; // "Berliner Str."
person.address["city"]; // "Leipzig"
```

You can **change values** of object properties by reassigning them using the dot or bracket notation:

```js
person.name = "Max Paddington";
person["age"] = 33;
```

You can **add new** properties in _the same way_:

```js
person.score = 15;
```

You can **delete properties** using the delete keyword:

```js
delete person.score;
```

### Nested Objects / Arrays

Arrays can contain objects and vice versa:

```js
const peopleArray = [
  {
    name: "John",
    age: 22,
  },
  {
    name: "Alex",
    age: 33,
  },
];
```

```js
const user = {
  userId: "1234",
  mail: "test@mail.com",
  shoppingCart: ["tomato", "banana", "chocolate"],
};
```

You can access elements via **chained** dot / bracket notation:

```js
peopleArray[1].name; // "Alex"
user.shoppingCart[0]; // "tomato"
```

---

> 💡 **KEY** kann auch als ein **string** vorgefunden werden. Wir müssen durch **bracket notation** darauf zugreifen, da **dot notation** nicht mit _Leerstellen_ umgehen kann
>
> ```js
> const person = {
>   name: "Marc",
>   age: 18,
>   "another key": "lorem", // KEY als String?
>   anotherKey: "value",
> };
>
> person["another key"] = "Peter"; // über KEY mit bracket-notation aufgerufen!
> person.name = "Oskar"; // hier dot-notation
> ```

---

#### Resources

[MDN Docs: Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
[MDN Docs: Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)

</details>

<!-- ---------- ---------- ---------- ---------- ---------- ---------- -->
<!-- ---------- ////////// ---------- ---------- ////////// ---------- -->
<!-- ---------- ---------- ---------- ---------- ---------- ---------- -->

## JS Forms

<details><summary>ListeningToSubmit | Events | AccessInteractive | UsingInput | ReadCheckbox | htmlFormValidation | inputEvent | resettingForms</summary>

## JS Forms

### Understanding the Default Behavior of Form Submit

If you click the submit button of a form, it triggers the following default behavior (without
writing _any_ JavaScript):

- The form sends a GET request with names and their values as prop inside an URL like
  `/?firstName=value1&lastName=value2&...`.
- The page is reloaded and thus the data is lost for us.

None of that is useful, if we want to do something with the submitted data in our frontend code. You
can prevent this behavior with a method called `.preventDefault()`.

> 💡 You can inspect this behaviour inside your dev browser tool -> Network

---

### Listening to the `submit` event and preventing the Default Behavior

In order to prevent this behavior of the `submit` event, you need to

- receive the event object as an argument of the event listener arrow function
- call `event.preventDefault()`

```js
const form = document.querySelector('[data-js="form"]');

form.addEventListener("submit", (event) => {
  event.preventDefault();
});
```

By calling `event.preventDefault()` the browser will not perform a GET request that would cause the
page to reload on submit.

> 💡 Durch das submitten unserer Form wird ein submit **event** ausgelößt

---

### The `event` Object and `event.target`

The `event` object is created whenever an event is triggered. You can accept it as the first
parameter in the callback function and thus access it inside the function body (e.g. via
`event.preventDefault()`).

For now, the most important method of the `event` object is `.preventDefault()`.

`event.target` is a reference to the element to which the event originated from - in this case - the
form.

```js
form.addEventListener("submit", (event) => {
  event.preventDefault();

  console.log(event.target);
});
// Output:
// <form data-js="form">
//		<fieldset>...</fieldset>
//		...
//		<button type="submit">Submit</button>
//	</form>
```

---

### Accessing Interactive Fields: `event.target.elements` and the `name` Attribute

While `event.target` represents the entire form, `event.target.elements` is a collection of all form
elements (form fields, field sets and buttons).

You get access to a specific form field via its `name` attribute and dot notation:

```js
form.addEventListener("submit", (event) => {
  event.preventDefault();

  const formElements = event.target.elements;

  console.log(formElements.firstName);
  console.log(formElements.firstName.value);
});
```

> 💡 Note that:
>
> - `event.target.elements` is stored in the variable `formElements` for better readability,
> - `firstName` is the string value of the corresponding `name` attribute, as in
>   `<input name="firstName"/>`, and
> - `firstName.value` returns the user input for the field with `name="firstName"`.

---

### Using Input Values

You can access all input values of the form by using `FormData()`. This constructor uses
`event.target` and can be transformed into a usable object afterwards:

```js
form.addEventListener("submit", (event) => {
  event.preventDefault();

  const formData = new FormData(event.target);
  const data = Object.fromEntries(formData);

  console.log(data);
});
```

This is very useful to easily access the input data of an entire form.

> 💡 Despite the fact that using `FormData` is much less verbose, `event.target.elements` is very
> useful if you want to access single form field. (Spoiler alert: In case you want to focus a
> specific field after resetting the form, for example.)

### Exception: Reading Values from Checkboxes

Checkboxes have two states: checked ("true") and not checked ("false"). In contrast to other input
types, the `value` attribute does not reflect this change, but is only used as an identifier for the
checkbox.

You can access the checkbox's state via the `.checked` property instead.

Imagine the following checkbox

```html
<input type="checkbox" name="colorBlue" value="blue" />
```

and its corresponding JavaScript:

```js
console.log(formElements.colorBlue.checked); // output: true or false
console.log(formElements.colorBlue.value); // output (always): blue
```

> 💡 `Zahlenwerte` aus Formularen werden als `"Strings"` ausgegeben und müssen vor weiterbenutzen als `Zahl` in eine solche umgewandelt (ge-parsed) werden.  
> `parseInt(stringValue)`  
> [parseInt // radix Info @ w3schools](https://www.w3schools.com/jsref/jsref_parseint.asp#:~:text=The%20parseInt%20method%20parses%20a,omitted%2C%20JavaScript%20assumes%20radix%2010)

---

### HTML Form Validation

Before submitting a form, it is important to ensure all required form fields are filled out, in the
correct format. This is called **client-side form validation**.

HTML provides several form field attributes to enable validation features build into the browser.

| Attribute                 | Description                                                                                                                                        |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| `required`                | if present, a form field needs to be filled in before the form can be submitted                                                                    |
| `minlength` / `maxlength` | minimum and maximum length of textual data (strings)                                                                                               |
| `min` / `max`             | minimum and maximum values of numerical input types                                                                                                |
| `type`                    | each input type has its own prefigured validation (like `email`)                                                                                   |
| `pattern`                 | [a regular expression pattern](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) the entered data needs to follow |

The following input field is valid if its value exists and it is a string between 3 and 30
characters:

```html
<input
  id="input-name"
  type="text"
  name="name"
  minlength="3"
  maxlength="30"
  required
/>
```

> ❗️ If the `required` attribute is omitted, the field is valid if it is empty or has a content
> between 3 and 30 characters, but invalid if 1 or 2 characters are entered.

`type="email"` will check if the input is a valid email address.

```html
<input id="input-email" type="email" name="email" />
```

---

### The `input` Event

Occasionally, you may want to do something if the value of a single field changes even before the
form is submitted.

The `input` event is fired every time when the value of a form field has been changed. For example,
a `<textarea />` will fire this event with every keystroke.

```js
const messageField = document.querySelector('[data-js="message"]');

messageField.addEventListener("input", (event) => {
  console.log(event.target.value);
});
```

> ❗️ Don't confuse the `input` event with the `change` event, which is only fired after a field's
> content has been committed by the user by pressing enter or moving the focus to the next field.

---

### Focus Input Fields

You can focus an input field with the `.focus()` method. This can be used to improve the user
experience after submitting a form.

```js
const messageField = document.querySelector('[data-js="message"]');

form.addEventListener("submit", (event) => {
  event.preventDefault();
  // [...] handle form data
  messageField.focus();
});
```

Instead of querying the input element using `querySelector`, it can also be obtained via the
`event.target.elements` collection:

```js
form.addEventListener("submit", (event) => {
  event.preventDefault();
  // [...] handle form data
  event.target.elements.message.focus();
});
```

This will focus a form field with the attribute `name="message"`.

---

### Resetting Forms

You can reset all form fields to their default value with the `.reset()` method.

```js
form.addEventListener("submit", (event) => {
  event.preventDefault();
  // [...] handle form data
  event.target.reset();
});
```

This often comes in handy in combination with `.focus()`. Think of a chat: After the message was
send, the input field is cleared and re-focussed, so users can write the next message.

---

#### Resources

- [MDN web docs: Client-side form validation](https://developer.mozilla.org/en-US/docs/Learn/Forms/Form_validation)
- [MDN web docs: input event](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/input_event)
- [Event interface](https://developer.mozilla.org/en-US/docs/Web/API/Event#properties)

</details>

<!-- ---------- ---------- ---------- ---------- ---------- ---------- -->
<!-- ---------- ////////// ---------- ---------- ////////// ---------- -->
<!-- ---------- ---------- ---------- ---------- ---------- ---------- -->

## JS createElement

<details><summary>TheDOM | createElement | elementProperties+Methods | innerHTML | resettingElementContent</summary>

## JS createElement

### The DOM

The **Document Object Model** is a representation of the HTML document. Each HTML Tag is modelled as
a **node** in a tree structure, which shows how HTML elements are nested. A computer program such as
your JavaScript file can access and manipulate the HTML website by changing the DOM via the
`document` object. ![the DOM](assets/DOM.png)

### `document.createElement`

You can generate an HTML element with JavaScript by using the `document.createElement` method. It
expects the type of element **as an argument**.

```js
const article = document.createElement("article");
const button = document.createElement("button");
```

After generating an element, you need to place the element into the DOM. For this, you can use the
`.append` method. It places the element as the **last child** into the respective element.

```js
document.body.append(article); // placing the created article at the end of the body
article.append(button); // placing the created button into the article
```

The result looks like this:

```html
<body>
  ...
  <article>
    <button></button>
  </article>
</body>
```

---

### Element Properties and Methods

As well as with queried HTML elements (via `querySelector`), we can add classes, event listeners and
more to the created HTML elements.

```js
article.classList.add("card");

button.addEventListener("click", () => {
  console.log("It works!");
});
```

The text of an element can be changed by reassigning the `.textContent` property:

```js
button.textContent = "Click me!";
```

### Common Element Properties and Methods

| Property          | Effect                                                             |
| ----------------- | ------------------------------------------------------------------ |
| `classList`       | add, toggle or remove classes from element                         |
| `textContent`     | get or set text inside element                                     |
| `style`           | define inline style, e.g. `element.style.backgroundColor = "red" ` |
| `hidden`          | boolean whether element is hidden or not                           |
| `focus()`         | focusses the element on the website                                |
| `hasAttribute()`  | returns true if the element has the given attribute                |
| `querySelector()` | returns the first child that matches the given CSS selector        |

> 💡 You can assign HTML attributes by using the element properties. Go to the
> [MDN Docs](https://developer.mozilla.org/en-US/docs/Web/API/Element#properties) for a
> comprehensive list of element properties.

---

### `.innerHTML`

> ❗️ innerHTML can be unsafe when user input is passed into the template literal. Use it with
> caution. Read
> [this article](https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML#replacing_the_contents_of_an_element)
> for more information about it.

The `innerHTML` property can be used to create the entire html layout of an element by passing the
html code as a string. By using **template literals** the content of the html can be dynamically
created.

```js
const cityName = "Lissabon";

article.innerHTML = `
	<h2> ${cityName} </h2>
	<p class="card__content">
		${cityName} is a very beautiful city in Portugal. 
		Go there and enjoy the stay!
	</p>
	<button type='button' class="card__booking-button"> 
		Book Trip 
	</button>
`;
```

This HTML code is rendered then **inside** the article element:

```html
<body>
  ...
  <article>
    <h2>Lissabon</h2>
    <p class="card__content">
      Lissabon is a very beautiful city in Portugal. Go there and enjoy the
      stay!
    </p>
    <button type="button" class="card__booking-button">Book Trip</button>
  </article>
</body>
```

### Resetting Element Content

`.innerHTML` can also be used to **reset** the content of an element, e.g. a container:

HTML before:

```html
<ul data-js="cardContainer">
  <li class="card">...</li>
  <li class="card">...</li>
  <li class="card">...</li>
</ul>
```

By setting the innerHTML to an empty string, the content is deleted:

```js
const cardContainer = document.querySelector('[data-js="cardContainer"]');
cardContainer.innerHTML = "";
```

The result:

```html
<ul data-js="cardContainer"></ul>
```

---

#### Resources

[MDN Docs about element Properties](https://developer.mozilla.org/en-US/docs/Web/API/Element#properties)  
[MDN Docs about securtiy risks with innerHTML](https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML#replacing_the_contents_of_an_element)

</details>
