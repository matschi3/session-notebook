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

## log/print to console

In JavaScript we can print text to the console of the web browser. We can use this for debugging or error logging for example.

```
console.log("Hello World!"); // logs into console
console.clear(); // clears console
console.error("Error!"); // logs as error into console
```

---

## selecting HTML Elements `querySelector()`

before adding ineractivity, we need to select the
