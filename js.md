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
