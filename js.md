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

## Resources

### Connect a JavaScript file

[The Script element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script)

### Hello World

[Console](https://developer.mozilla.org/en-US/docs/Web/API/Console)

### Selecting HTML Elements

[Document](https://developer.mozilla.org/en-US/docs/Web/API/Document)

[Using data attributes](https://developer.mozilla.org/en-US/docs/Learn/HTML/Howto/Use_data_attributes)

[document.querySelector](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector)

[data-\* attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/data-*)

### Add Interaction

[.addEventListener()](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener)

[Event reference](https://developer.mozilla.org/en-US/docs/Web/Events#event_listing)

### Add/remove & toggle classes

[classList](https://developer.mozilla.org/de/docs/Web/API/Element/classList)

---

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

## ❗️ checked bis hier

## Assignment Operators

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

## Type Coersion

When you use an operator with a variable with an unfitting type, JavaScript will automatically
convert (coerse) this variable into a fitting type. For example:

```js
4 / "2"; // → 4 / 2
```

There is no "/" operator for strings, so JavaScript converts the string into a number if possible.
This is also true for boolean operators which we will cover in a later session.

> ❗️ There is another `+` operator in JavaScript, that links two strings together: `"a" + "b"` →
> `"ab"`. When 'adding' a number and a string, the number is converted to a string: `"a" + 6` → `"a6"`.
> Make sure that both variables are numbers if you want to add them.
> 📙 Read more about [**Type coersion** in the mdn](https://developer.mozilla.org/en-US/docs/Glossary/Type_coercion).

## Number Systems

When working with computers, it is sometimes useful to work with a different number system than the
standard 10 digit system, since a computer only understands `binary` numbers composed of only 0
and 1. You don't have to learn these systems by heart, but it is good if you heard about them.

- `decimal system`: the standard numbers, has 10 symbols "0" to "9".
- `binary system`: only has 2 symbols "0" and "1". If you want to write a bigger number than 1, you
  add another digit: 2 → "10" in binary.
- `hexadecimal system`: has 16 symbols "0" to "9" and "a" to "f". If you want to write a number
  bigger than 15 you add another digit: 12 → "c" in hexadecimal.

---

## Resources

- [Operator Precedence in the mdn](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence)
- [Type coersion in the mdn](https://developer.mozilla.org/en-US/docs/Glossary/Type_coercion)
