layout: Post
title: Alle Markdown-Formate

# Grundlagen

Es ist sehr einfach , einige Worte **fett** **fett** und andere Wörter *kursiv* *kursiv* mit Markdown zu machen. *Sie **können sie** kombinieren* . Und ***dreifach*** oder ***dreifach*** . Sie können sogar [auf Google verlinken!](http://google.com) und auch [mit dem Titel verknüpfen](http://google.com "Titel")
Textzeilenumbruch und ~~ durchgestrichen ~~

Sie können eine `#` bis zu `######` sechs für verschiedene Überschriftengrößen verwenden. <a href="http://google.com" target="_blank">Testlink</a>

Wenn Sie jemanden zitieren möchten, verwenden Sie das Zeichen> vor der Zeile:

> Kaffee. Die beste Bio-Suspension, die jemals entwickelt wurde ... Ich habe die Borg damit geschlagen.
> - Kapitän Janeway
>     - elem

# Dies ist ein `<h1>` -Tag

# Dies ist auch ein `<h1>`

## Dies ist ein `<h2>` -Tag

## Dies ist auch ein `<h2>`

###### Dies ist ein `<h6>` -Tag

## Listen

Manchmal möchten Sie nummerierte Listen:

1. Eins
2. Zwei

- rot
- Grün

- rot
- Grün

- Striche funktionieren genauso gut
- Und wenn Sie Unterpunkte haben, setzen Sie zwei Leerzeichen vor den Bindestrich oder Stern:
    - So was
    - Und das
        - Auch diese
        - Und das

# Horizontale Regeln

---

---

---

---

---

# Bilder

![Externes Bild](https://octodex.github.com/images/yaktocat.png)

![Internal image](/img/screwdriver.png "Optionaler Titel")

# Codes

Es gibt viele verschiedene Möglichkeiten, Code mit GitHubs Markdown zu formatieren. Wenn Sie Inline-Codeblöcke haben, wickeln Sie diese in Backticks ein: `var example = true` . Wenn Sie einen längeren Codeblock haben, können Sie mit vier Leerzeichen einrücken:

```
if (isAwesome){
  return true
}
```

GitHub unterstützt auch das sogenannte Code-Fencing, das mehrere Zeilen ohne Einrückung zulässt:

```
if (isAwesome){
  return true
}
```

Wenn Sie die Syntaxhervorhebung verwenden möchten, geben Sie die folgende Sprache an:

```javascript
if (isAwesome){
  return true
}
```

# Tabelle

Erster Header | Zweiter Header
--- | ---
Inhalt aus Zelle 1 | Inhalt aus Zelle 2
Inhalt in der ersten Spalte | Inhalt in der zweiten Spalte

# Extras

GitHub unterstützt viele Extras in Markdown, mit denen Sie auf Personen verweisen und Links zu ihnen erstellen können. Wenn Sie jemals einen Kommentar an jemanden richten möchten, können Sie seinem Namen ein @ -Symbol voranstellen: Hey @kneath - lieben Sie Ihren Pullover!

Aber ich muss zugeben, Aufgabenlisten sind mein Favorit:

- [x] Dies ist ein vollständiger Gegenstand
- [] Dies ist ein unvollständiger Artikel

Wenn Sie eine Aufgabenliste in den ersten Kommentar eines Problems aufnehmen, wird in Ihrer Liste der Probleme ein hilfreicher Fortschrittsbalken angezeigt. Es funktioniert auch in Pull Requests!

Und natürlich Emoji! : funkelt :: Kamel :: Boom:

# Unterstrichene Variable (WebFundamentals)

Projektpfad: /web/_project.yaml
