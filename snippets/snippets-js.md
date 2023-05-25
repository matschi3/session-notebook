## connect javascript index.js

`html`

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

## select html elements `querySelector()`

`html`

```html
<body>
  <main class="main" id="main" data-js="main">...</main>
</body>
```

`js`

```js
const mainElement = document.querySelector('[data-js="main"]');
```

---

## add interaction `addEventListener()`

```js
const button = document.querySelector('[data-js="button"]');
button.addEventListener("click", () => {
  console.log("Yeah");
});
```

---

## if else

```js
if (hour < 12) {
  console.log("Good Morning.");
} else if (hour < 18) {
  console.log("Good afternoon.");
} else if (hour === 24) {
  console.log("Good night.");
} else {
  console.log("Good evening.");
  // is executed only if call other conditions are false
}
```

---

## ternary operator `? :`

```js
condition ? expressionIfTrue : expressionIfFalse;

isUserLoggedIn ? logoutUser() : loginUser();

const greetingText = time < 12 ? "Good morning." : "Good afternoon.";
```

---

## function `function myFunction() {}`

```js
function add3Numbers(first, second, third) {
  const sum = first + second + third;
  return sum; // and return statement (returns where function is called)
}
```

---
