# JavaScript

## JavaScript - Basics

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

## JavaScript - variables and numbers

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

## JavaScript -

###
