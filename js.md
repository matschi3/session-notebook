# JavaScript

## JavaScript - Basics

### connect a JavaScript file

The `<script>`-Tag has two attributes:  
`src="./index.js"` sets the URL to Javascript file _index.js_  
`defer` tells browser to **delay the loading of script** until _all HTML elemens_ are loaded

```
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

```
console.log("Hello World!"); // logs into console
console.clear(); // clears console
console.error("Error!"); // logs as error into console
```

---

---

### selecting HTML Elements: `querySelector()`

before adding interactivity, we need to select the necessary HTML-Elements:

```
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
> ```
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

```
<button type="button" data-js="button">Log into console</button>
```

```
const button = document.querySelector('[data-js="button"]');
button.addEventListener("click", () => {});
```

- First you **specify** the kind of event, e.g. _click_ , _mouseover_ or [more event-types](https://developer.mozilla.org/en-US/docs/Web/Events#event_listing)
- Then you **define** what _code to execute_ when the event is _triggered_
- Code to execute between `{}` in this e.g. `console.log()`

```
const button = document.querySelector('[data-js="button"]');
button.addEventListener("click", () => {
  console.log("Yeah");
});
```

---

### add/remove/toggle classes: `.classList.`
