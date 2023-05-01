# CSS Basics

![CSS Ruleset](./img/css_ruleset.png)

| Bereich     | Beschreibung                                             |
| ----------- | -------------------------------------------------------- |
| Selector    | Wählt das zu stylende Element                            |
| Declaration | Definiert das Styling durch `Eigenschafts`+`Werte`-Paare |
| Property    | Name der zu stylenden `Eigenschaft`                      |
| Value       | Der `Wert` einer zugehörigen `Eigenschaft`               |
| Keyword     | Wie `Value` // Keywords haben vordefinierte Funktionen   |

Es können **mehrere Elemente** mit **einem Ruleset** gestyled werden, sowie **mehrere Deklarationen** in einem **Ruleset** vorhanden sein:

```
h1,
h2,
h3 {
    color: green;
    font-size: 12px;
}
```

---

## Linking Stylesheets

Simple implementation of seperated `styles.css`-file in `<head>` of the HTML document, so that styles get loaded into the browser before the Content does.

```
<head>
  ...
  <link rel="stylesheet" href="./file/styles.css" />
</head>
```

> ❗️ Der `.` in/vor `"./file/styles.css"` ist wichtig, damit die Datei über den Dateipfad und nicht über die URL aufgerufen wird.  
> Kann sonst bei Domainwechsel für Probleme sorgen.

---

## Box Model

> ❗️ Hier fehlt noch ein Teil, der bald kommt und an diese Stelle gehört ❗️

---

## Inline and Block/Box elements

- **inline elements** nehmen den Platz ein, _den sie selbst benötigen_.  
   // platziert **in** text lines
- **block/box elements** nehmen den _gesamten horizontalen Platz_ des `<parent element>` ein.  
   // platziert in **neuer Zeile**
  > 💡 Dieses Standartverhalten kann durch die `display` Eigenschaft verändert werden.  
  > `display: flex | grid`

---

## Selectors

- **universal** -Selektor  
  // wählt alles (kann durch **Combinators** gezielt eingesetzt werden):

```
* {
    box-sizing: border-box;
}
```

> 💡 The property `box-sizing` changes the way how the `width` and `height` of an element is calculated.
> The default value is `content-box`. The values of `width` and `height` set the size of the "content
> box". With the value `border-box`, the size of the "border box" is set instead.  
> Now, the `width` property defines the size of the border box, padding and border width are subtracted to calculate the available space for the content.

- **element**/type -Selektor  
  // wählt HTML Elemente anhand ihres Typen:

```
h1 {
}
```

---

- **.class** -Selektor  
  // wählt Elemente einer bestimmten Klasse:

```
.box {
}
```

---

- **#ID** -Selektor  
  // wählt _ein Element_ mit eindeutiger ID:

```
#unique {
}
```

---

- **attribute** -Selektor  
  // wählt Elemente anhand ihres Attributes:

Alle Elemente generell mit `type` -Attribut:

```
[type] {
}
```

Alle Elemente mit `type` -Attribut und dazugehörigem Wert `"button"`:

```
[type="button"] {
}
```

Alle `a` -Elemente mit `href` -Attribut **_beginnend_** mit Wert `"https"`:

```
a[href^="https"] {
}
```

> 🧩 BestPractise:  
> .class-Selektor hauptsächlich benutzen  
> #ID-Selektor **nicht** für styling

---

## Combinators
