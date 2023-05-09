# Markdown

Der Markdown(.md)-Syntax ermöglicht das schreiben von formatiertem Text, welcher in einer simplen Textdatei gespeichert wird. Es werden bestimmte Textzeichen benutzt, um den Text auf bestimmte Weise darzustellen.

| Markdown Syntax                        | Beschreibung                                                 |
| -------------------------------------- | ------------------------------------------------------------ |
| `# Überschrift1`                       | Level 1 Überschrift                                          |
| `# Überschrift6`                       | Level 6 Überschrift                                          |
| `[ ] checkbox`                         | [ ] checkbox                                                 |
| `[x] checkedbox`                       | [x] checkedbox                                               |
| `**fetterText**`                       | **fetterText**                                               |
| `_kursiverText_`                       | _kursiverText_                                               |
| `---`                                  | Trennstrich                                                  |
| `> eingerückter Textblock`             | eingerückterTextblock                                        |
| `- uListItem`                          | unordered ListItem                                           |
| `1. oListItem`                         | ordered ListItem                                             |
| `[link text](https://www.example.com)` | [externerLink](https://www.example.com)                      |
| `[link text](../project/README.md)`    | relativerLink (überordnes Verzeichnis)                       |
| `[link text](./project/README.md)`     | relativerLink (Verzeichnis)                                  |
| `![Bildbeschreibung](img-url)`         | Bild                                                         |
| `` `inline Codeblock` ``               | `inline Codeblock`                                           |
| ` ``` Codeblock ``` `                  | `Codeblock`                                                  |
| ` ```html Codeblock ``` `              | `Codeblock` für html oder andere                             |
| ` ```css Codeblock ``` `               | `Codeblock` für CSS oder andere                              |
| `[ _ ][ _ ]`                           | Zeilenumbruch mit 2 Leerstellen am Ende der Zeile            |
| `[^1], [^2], ...`                      | Fußnoten // auch Namen möglich, werden in Zahlen umgewandelt |

<details><summary>mehr...</summary> Es kann auch ein `< details >` -Bereich erstellt und mit einer `< summary >`versehen werden.  </details>

---

## Tabellen

Es müssen mindestens **drei `---`** pro Spalte vorhanden sein, welche durch **`|`** getrennt werden.  
**Doppelpunkte (:)** werden benutzt um Spalten anzuordnen.

```
| Spalte 1       | Spalte 2      | Spalte 3  |
| -------------- |:-------------:| ---------:|
| Spalte 1       | normal        | € 200     |
| Spalte 2       | zentriert     | € 400     |
| Spalte 3 ist   | right-aligned | € 600     |
```

> | Spalte 1     |   Spalte 2    | Spalte 3 |
> | ------------ | :-----------: | -------: |
> | Spalte 1     |    normal     |    € 200 |
> | Spalte 2     |   zentriert   |    € 400 |
> | Spalte 3 ist | right-aligned |    € 600 |

Die äußeren Markierungen (|) sind **optional**, es geht auch ohne.

```
Markdown | weniger | schön
--- | --- | ---
*rendert* | `trotzdem` | **schön**
1 | 2 | 3
```

> | Markdown  | weniger    | schön     |
> | --------- | ---------- | --------- |
> | _rendert_ | `trotzdem` | **schön** |
> | 1         | 2          | 3         |

---

#### Quellen und weiterführende Links

- [Handout](https://github.com/neuefische/muc-web-23-3/blob/main/sessions/github-and-markdown/github-and-markdown.md)
- [Challanges](https://github.com/neuefische/muc-web-23-3/blob/main/sessions/github-and-markdown/challenges-github-and-markdown.md)

---

- [Markdown Cheatsheet (by adam-p)](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

---

> 💡 Hinweis

> ❗️ Achtung
