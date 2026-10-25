<!--
author:   Cedric Vogel
version:  1.0.0
language: de

comment:  Ausdrücke, Auswertung und vorgegebene Speicher: vorhersagen, erklären und mit Python prüfen.

import: https://raw.githubusercontent.com/cedricvogel-leo/glpython-liascript/main/README.md
-->

# Ausdrücke — Schritt für Schritt zum Wert

[Im LiaScript-Reader öffnen](https://liascript.github.io/course/?https://raw.githubusercontent.com/cedricvogel-leo/programmieren-mit-funktionen/main/materials/ausdruecke.md)

Wie wird ein Ausdruck schrittweise zu einem Wert? Und welche Rolle spielen
die gespeicherten Werte der Variablen?

Nach diesem Einstieg können Sie:

- Ausdrücke anhand ihrer Merkmale beschreiben und einordnen;
- den nächsten Auswertungsschritt mit einer Regel begründen;
- den unveränderten Teil eines Ausdrucks benennen;
- einen Wert aus einem vorgegebenen Speicher lesen und im Ausdruck einsetzen;
- erklären, warum eine Auswertung mit einem Fehler enden kann.

## 1. Ausdrücke

Wir betrachten Werte und Ausdrücke, in denen **Operatoren**
Teilausdrücke miteinander verbinden.

Die Werte in unseren Beispielen sind Zahlen, Zeichenketten und
Wahrheitswerte. Operatoren sind zum Beispiel `+`, `-`, `>` und `==`.

<!-- data-type="none" data-sortable="false" -->
| A | B |
| --- | --- |
| `2 + 3` | `5` |
| `"Hal" + "lo"` | `"Hallo"` |
| `3 < 5` | `True` |

Beschreiben Sie den Unterschied zwischen den Ausdrücken in Spalte A und
den Ausdrücken in Spalte B.

[[___ ___ ___]]

<details>
<summary>Musterlösung</summary>

In Spalte A stehen **unausgewertete Ausdrücke**. Es sind noch Operationen
auszuführen.

In Spalte B stehen **ausgewertete Ausdrücke**. Es sind keine Operationen
mehr auszuführen. Wir nennen diese Ausdrücke auch **Werte**.
«Ausgewerteter Ausdruck» und «Wert» bedeuten dasselbe.

In `2 + 3` sind die Teilausdrücke `2` und `3` bereits Werte. Der gesamte
Ausdruck ist aber noch unausgewertet, weil die Addition noch auszuführen ist.

</details>

## 2. Auswerten von Ausdrücken

Beim Auswerten werden Teilausdrücke **an Ort und Stelle durch ihre Werte
ersetzt**. Der umgebende Ausdruck bleibt erhalten.

> **Klammern und Operatorrangfolge**
>
> Klammern legen fest, welche Teilausdrücke zusammengehören. Ohne
> zusätzliche Klammern gilt für die hier verwendeten Operatoren:
>
> - `*`, `/`, `//` und `%` haben Vorrang vor `+` und `-`.
> - `+` und `-` haben Vorrang vor Vergleichen wie `<`, `>` und `==`.
> - Gleichrangige arithmetische Operatoren werden von links nach rechts
>   gruppiert: `8 - 3 - 1` bedeutet `(8 - 3) - 1`.
>
> Klammern bestimmen die Gruppierung, nicht pauschal den nächsten Schritt.

> **Anleitung zum Auswerten**
>
> 1. Ist der Ausdruck bereits ein Wert, sind Sie fertig.
> 2. Bestimmen Sie anhand der Klammern und der Operatorrangfolge die
>    **äussere Operation**: die Operation, die zuletzt ausgeführt wird.
> 3. Werten Sie deren linken Teilausdruck mit dieser Anleitung aus.
> 4. Werten Sie danach deren rechten Teilausdruck mit dieser Anleitung aus.
> 5. Führen Sie die äussere Operation mit den beiden Werten aus.
>
> Ersetzen Sie ausgewertete Teilausdrücke jeweils an Ort und Stelle durch
> ihren Wert. Der umgebende Ausdruck bleibt erhalten. Ist eine Operation
> für die Werte nicht erlaubt, endet die Auswertung mit einem Fehler.

Ein Wert muss nicht erneut ausgewertet werden.
Ein **Auswertungsprotokoll** hält den Ausgangsausdruck und jeden Schritt
bis zu einem Wert oder Fehler fest.
Der Pfeil `→` beschreibt einen Auswertungsschritt. Er ist **kein
Python-Operator**. Sie können ihn in Ihren Eingabefeldern auch als `->`
schreiben. Klammern um einen einzelnen Wert lassen wir weg.

In `2 + 3 * 4` ist die Addition die äussere Operation. Ihre unmittelbaren
Teilausdrücke sind `2` und `3 * 4`. `2` ist bereits ein Wert. Deshalb:

```text
2 + 3 * 4
→ 2 + 12
→ 14
```

«Von links nach rechts» heisst also **nicht**, immer zuerst den am
weitesten links geschriebenen Operator auszuführen.

**Mit der Visualisierung vergleichen:** Drücken Sie ▷❘, um die
Auswertungsschritte zu verfolgen.

```python
2 + 3 * 4
```
@GLPython.visual

### Zwei unausgewertete Teilausdrücke

Lesen Sie den Ausdruck zunächst, ohne Python auszuführen:

```python
(2 + 3) * (4 + 5)
```

**Welcher Ausdruck steht nach genau einem Schritt da?**

- [( )] `(2 + 3) * 9`
- [(X)] `5 * (4 + 5)`
- [( )] `5 * 9`
- [( )] `45`
[[?]] Die Multiplikation wartet auf zwei Summen. Welche davon steht links?
***
Zuerst wird `2 + 3` zu `5`. `5 * 9` wäre bereits der Stand nach zwei
Schritten; `45` ist der endgültige Wert.
***

Schreiben Sie das Auswertungsprotokoll. Benennen Sie den Teil, der beim
ersten Schritt unverändert bleibt.

[[___ ___ ___ ___ ___]]

**Danach prüfen:** Führen Sie den Code aus. `print(...)` zeigt das Ergebnis an.

```python
print((2 + 3) * (4 + 5))
```
@GLPython.eval

<details>
<summary>Auswertungsprotokoll und unveränderter Kontext</summary>

```text
(2 + 3) * (4 + 5)
→ 5 * (4 + 5)
→ 5 * 9
→ 45
```

Im ersten Schritt bleibt die Multiplikation mit `(4 + 5)` erhalten.
Erst wenn beide Summen Werte sind, wird multipliziert.

</details>

Vergleichen Sie Ihr Protokoll mit der Lösung. Begründen Sie eine nötige
Korrektur oder bestätigen Sie die Reihenfolge mit einer Regel.

[[___ ___ ___]]

### Einen falschen Schritt erklären

Eine Person schlägt vor:

```text
10 - 2 * (1 + 2)
→ 8 * (1 + 2)
```

**Ihre Erklärung:** Warum ist der Schritt nicht erlaubt? Geben Sie den
tatsächlich nächsten Teilausdruck, den korrekten nächsten Gesamtausdruck
und den dabei unveränderten Teil an.

[[___ ___ ___ ___]]

<details>
<summary>Regelprüfung</summary>

Die `2` gehört zur Multiplikation. Deren Ergebnis muss vorliegen, bevor
es von `10` abgezogen werden kann. Als Nächstes wird `1 + 2` ausgewertet:

```text
10 - 2 * (1 + 2)
→ 10 - 2 * 3
```

Der Kontext `10 - 2 * …` bleibt erhalten.

</details>

### Mit Klammern verändern

Setzen Sie in `10 - 2 * 3` Klammern so, dass der Wert `24` entsteht.
Zahlen und Operationen dürfen Sie nicht ändern.

Schreiben Sie das Auswertungsprotokoll des veränderten Ausdrucks.
Erklären Sie die neue Gruppierung.

[[___ ___ ___ ___]]

**Erst danach prüfen:** Ändern Sie nur den Ausdruck innerhalb von
`print(...)` im folgenden Feld.

```python
print(10 - 2 * 3)
```
@GLPython.eval

<details>
<summary>Eine passende Lösung</summary>

```text
(10 - 2) * 3
→ 8 * 3
→ 24
```

Die Klammern machen `10 - 2` zu einem Teilausdruck der Multiplikation.
Ohne diese Klammern ergibt der ursprüngliche Ausdruck `4`.

</details>

**Nach der Prüfung:** Halten Sie eine nötige Änderung fest oder begründen
Sie, warum Ihr Entwurf bereits passt.

[[___ ___ ___]]

### Wenn eine Operation nicht passt

`"3" + "2"` ergibt die Zeichenkette `"32"`. `3 + 2` ergibt die Zahl `5`.
Aber was geschieht hier?

```python
"3" + 2
```

**Ihre Vorhersage:**

- [( )] Der Wert ist die Zahl `5`.
- [( )] Der Wert ist die Zeichenkette `"32"`.
- [(X)] Die Auswertung endet mit einem Fehler.
***
Die Operation `+` kann hier keine Zeichenkette mit einer Zahl verbinden.
Die Auswertung endet mit `TypeError`, nicht mit einem Wert.
***

**Ihre Begründung:** Beide Teilausdrücke sind bereits Werte. Warum reicht
das trotzdem nicht, um die Addition auszuführen?

[[___ ___ ___]]

**Jetzt prüfen — dieser Block enthält absichtlich einen Fehler:**

```python
print("3" + 2)
```
@GLPython.eval

**Nach der Prüfung:** Erklären Sie, was die Fehlerart `TypeError` hier
bedeutet. Ändern Sie bei Bedarf Ihre erste Erklärung, nicht die Aufgabe.

[[___ ___ ___]]

## 3. Speicher

Variablen sind **benannte Boxen**, in denen Werte gespeichert sind.

> **Speicher**
>
> > **Variablen**
> >
> > ```text
> > anzahl    3
> > preis     5
> > name      "Ada"
> > ```

`preis` ist der Name einer Variable, nicht selbst die Zahl `5`.
Die Box enthält hier den Wert `5`. Sie enthält nicht die noch
unausgewertete Formel, aus der dieser Wert vielleicht einmal entstanden ist.
Wie Werte gespeichert oder verändert werden, untersuchen wir später.

**Den Speicher lesen**

**Welcher Wert ist in `name` gespeichert?**

- [( )] Die Zeichenkette `"name"`.
- [(X)] Die Zeichenkette `"Ada"`.
- [( )] Die Variable enthält noch keinen Wert.
***
Neben dem Variablennamen `name` steht der gespeicherte
Zeichenkettenwert `"Ada"`.
***

**Ihre Erklärung:** Worin unterscheiden sich `preis`, `5` und `"preis"`?
Verwenden Sie die Begriffe «Variable», «Zahlenwert» und «Zeichenkettenwert».

[[___ ___ ___]]

<details>
<summary>Mit der Erklärung vergleichen</summary>

`preis` bezeichnet eine Variable. `5` ist ein Zahlenwert.
`"preis"` ist ein Zeichenkettenwert, der die Buchstaben des Wortes enthält.
Die Anführungszeichen machen einen Unterschied.

</details>

**Ihre Ergänzung:** Halten Sie eine Korrektur fest oder erklären Sie den
Unterschied noch einmal an `name` und `"name"`.

[[___ ___ ___]]

## 4. Auswerten im Kontext eines Speichers

Beim Auswerten einer Variable wird ihr gespeicherter Wert gelesen und
an ihrer Stelle im Ausdruck eingesetzt. **Das Lesen verändert den Speicher
nicht.**

> **Speicher**
>
> > **Variablen**
> >
> > ```text
> > n    4
> > ```

```text
2 * (n + 3) - 1
→ 2 * (4 + 3) - 1
→ 2 * 7 - 1
→ 14 - 1
→ 13
```

Zuerst lesen wir `n`. Der Kontext `2 * (… + 3) - 1` bleibt dabei erhalten.
Während der gesamten Auswertung bleibt in `n` der Wert `4` gespeichert.

### Zwei Variablen lesen

> **Speicher**
>
> > **Variablen**
> >
> > ```text
> > a    8
> > b    4
> > ```

Lesen Sie den Ausdruck:

```python
a + b * 2
```

**Welcher Ausdruck folgt nach genau einem Schritt?**

- [(X)] `8 + b * 2`
- [( )] `a + 4 * 2`
- [( )] `a + 8`
- [( )] `16`
[[?]] Die äussere Addition braucht die Werte von `a` und `b * 2`. Lesen Sie zuerst den linken Teilausdruck.
***
Zuerst wird `a` gelesen. Erst danach wird `b * 2` ausgewertet.
Die Regel lautet nicht «zuerst alle Variablen ersetzen» und auch nicht
«Multiplikation vor jedem Lesen».
***

Schreiben Sie das Auswertungsprotokoll. Benennen Sie den beim ersten
Schritt unveränderten Teil und die danach in `a` und `b` gespeicherten Werte.

[[___ ___ ___ ___ ___ ___]]

**Danach prüfen:** Führen Sie den Code aus. Die ersten beiden Zeilen
stellen den vorgegebenen Speicher bereit; `print(...)` zeigt das Ergebnis.

```python
a = 8
b = 4
print(a + b * 2)
```
@GLPython.eval

<details>
<summary>Auswertungsprotokoll</summary>

```text
a + b * 2
→ 8 + b * 2
→ 8 + 4 * 2
→ 8 + 8
→ 16
```

Beim ersten Schritt bleibt `… + b * 2` erhalten.
Im Speicher stehen weiterhin `a`: `8` und `b`: `4`.
In `a` wird nicht das Ergebnis `16` gespeichert.

</details>

**Ihre Regelprüfung:** Welche Ihrer Schritte stimmen überein? Falls Sie
etwas korrigieren, nennen Sie die dazugehörige Regel.

[[___ ___ ___]]

### Gleicher Ausdruck, anderer Speicher

Betrachten Sie zwei **getrennt vorgegebene** Speicher. Wir führen keine
Anweisungen aus, um von einem zum anderen zu gelangen.

> **Speicher A**
>
> > **Variablen**
> >
> > ```text
> > name    "Ada"
> > ```

> **Speicher B**
>
> > **Variablen**
> >
> > ```text
> > name    "Mia"
> > ```

Für beide Speicher lautet der Ausdruck:

```python
"Hallo, " + name
```

Schreiben Sie für A und B jeweils das Auswertungsprotokoll.
Verwenden Sie Anführungszeichen für Zeichenkettenwerte. Erklären Sie
die unterschiedlichen Ergebnisse.

[[___ ___ ___ ___ ___]]

**Jetzt prüfen:** Der Block ist für Speicher A vorbereitet. Führen Sie ihn
aus. Setzen Sie danach in der ersten Zeile `"Mia"` statt `"Ada"` ein, um
unabhängig davon Speicher B zu prüfen. Weitere Änderungen sind nicht nötig.

```python
name = "Ada"
print("Hallo, " + name)
```
@GLPython.eval

<details>
<summary>Beide Auswertungsprotokolle vergleichen</summary>

```text
Speicher A:
"Hallo, " + name → "Hallo, " + "Ada" → "Hallo, Ada"

Speicher B:
"Hallo, " + name → "Hallo, " + "Mia" → "Hallo, Mia"
```

Das Lesen liefert je nach vorgegebenem Speicher einen anderen Wert.
Der jeweilige Speicher bleibt während der Ausdrucksauswertung unverändert.
Die Anzeige durch `print` zeigt Zeichenketten ohne die Anführungszeichen.

</details>

**Nach der Prüfung:** Begründen Sie eine Korrektur oder erklären Sie,
warum das Lesen den jeweiligen Speicher nicht verändert.

[[___ ___ ___]]

### Wenn ein Name fehlt

> **Speicher**
>
> > **Variablen**
> >
> > ```text
> > preis    5
> > ```

Eine Variable `fehlender_name` ist nicht vorhanden.

```python
fehlender_name + 1
```

**Ihre Vorhersage:**

- [( )] Der Ausdruck ergibt `1`, weil fehlende Namen den Wert `0` liefern.
- [(X)] Die Auswertung endet beim Lesen mit `NameError`.
- [( )] Es entsteht derselbe `TypeError` wie bei `"3" + 2`.
***
Für `fehlender_name` kann kein gespeicherter Wert gelesen werden.
Die Addition kann deshalb noch gar nicht ausgeführt werden.
***

**Ihre Erklärung:** Vergleichen Sie `fehlender_name + 1` mit `"3" + 2`.
Beim zweiten Ausdruck sind beide Teilausdrücke bereits Werte. Warum
scheitern die Auswertungen an unterschiedlichen Schritten?

[[___ ___ ___]]

**Jetzt prüfen — auch dieser Fehler ist beabsichtigt:**

```python
preis = 5
print(fehlender_name + 1)
```
@GLPython.eval

**Nach der Prüfung:** Beschreiben Sie, an welchem Schritt die jeweilige
Auswertung endet. Korrigieren Sie Ihre erste Erklärung bei Bedarf hier.

[[___ ___ ___]]

### Abschluss

Bearbeiten Sie den folgenden Transfer zunächst **ohne Python-Ausführung**.
Nutzen Sie nur den vorgegebenen Speicher und unsere Regeln:

> **Speicher**
>
> > **Variablen**
> >
> > ```text
> > x    2
> > y    5
> > ```

```python
(x + 3) * (y - 1)
```

Schreiben Sie das Auswertungsprotokoll. Benennen Sie den zuerst
ausgewerteten Teilausdruck und für einen Schritt den unveränderten Kontext.
Erklären Sie, was währenddessen mit dem Speicher geschieht.

[[___ ___ ___ ___ ___ ___ ___]]

**Welchen Ergebniswert haben Sie erhalten?**

[[20]]
[[?]] Werten Sie erst den linken Teilausdruck der Multiplikation vollständig aus, dann den rechten.
***
Beide Teilausdrücke werden zu Werten: `5` und `4`. Die Multiplikation
ergibt danach `20`. Das vollständige Protokoll steht in der Selbstkontrolle.
***

**Erst jetzt mit Python vergleichen:**

```python
x = 2
y = 5
print((x + 3) * (y - 1))
```
@GLPython.eval

<details>
<summary>Selbstkontrolle</summary>

```text
(x + 3) * (y - 1)
→ (2 + 3) * (y - 1)
→ 5 * (y - 1)
→ 5 * (5 - 1)
→ 5 * 4
→ 20
```

Zuerst wird `x` gelesen. Beim ersten Schritt bleibt
`(… + 3) * (y - 1)` erhalten. Nach der linken Summe ist der rechte
Teilausdruck an der Reihe. Im Speicher bleiben `x`: `2` und `y`: `5`.

</details>

**Nach dem Vergleich:** Ergänzen Sie:

> «Ausgewerteter Ausdruck» und «Wert» …
>
> Den nächsten Schritt finde ich, indem …
>
> Beim Lesen einer Variable …
>
> Eine Erklärung, die ich bestätigt oder geändert habe, lautet …, weil …

[[___ ___ ___ ___ ___ ___]]

### Hinweise für Lehrkräfte

Dieser Einstieg behandelt ausschliesslich die ersten vier Konzepte der
aktuellen [Outline](../docs/lecture-outline.md#ausdrücke), nicht bereits
die vollständige Ausdrucks- und Einsetzmaschine mit Funktionsaufrufen.
Er setzt bekannte arithmetische Operationen und erste Python-Erfahrung
voraus, aber keine neu eingeführte Anweisungssemantik.

<!-- data-type="none" data-sortable="false" -->
| Lernziel | Lerngelegenheiten | Individueller Nachweis |
| --- | --- | --- |
| EX1: Ausdrücke erkennen | Abschnitt 1; Beispiele mit Werten und Operationen, später mit Variablen. | Beschreibung der Spalten A und B; Bedeutung von `preis`, `5` und `"preis"`. |
| EX2: Unausgewertete Ausdrücke und Werte unterscheiden | Abschnitt 1; Begriffe nach dem offenen A/B-Vergleich einführen. | Beschreibung des Unterschieds zwischen A und B und Abschlussreflexion. |
| EX3: Schritte und Fehler begründen | Abschnitte 2 und 4; unmittelbare Teilausdrücke, Kontext, Lesen und Fehler. | Auswertungsprotokoll zur Transferaufgabe, unveränderter Speicher und Unterscheidung der Fehlerursachen. |

Die Lektion verwendet native Quizze und
[freie Texteingaben](https://github.com/LiaScript/docs/blob/master/README.md#text-inputs).
Alle schriftlichen Aufträge haben einen Eingabeort im Kurs. Eine richtige
Quizantwort weist weder ein vollständiges Auswertungsprotokoll noch eine passende Begründung
nach. Offene Texte werden nicht automatisch bewertet oder an die Lehrkraft
übermittelt. Vergleich und Rückmeldung müssen passend organisiert werden.

Vorhersagen und spätere Korrekturen haben getrennte Felder. Lösungen sind
formative Hilfen und keine technisch gesperrten Prüfungsinhalte. Zum
Benennen von Kontext und markiertem Teilausdruck genügen Texteingaben;
eine grafische Markierfunktion wird nicht vorausgesetzt.

Die Zuweisungen in Prüfblöcken initialisieren nur den jeweils vorgegebenen
Speicher. `print` macht Ergebnisse sichtbar. Beides wird nicht als neuer
Lernstoff erklärt oder geprüft. Bei Zeichenketten müssen die Wertarten
explizit benannt werden, weil die Ausgabe keine Anführungszeichen zeigt.
Jeder ausführbare Block hat eine eigene Laufzeit und enthält seine
benötigte Vorbereitung selbst.

Die Auswertungsprotokolle zeigen Ersetzungen an Ort und Stelle im
dargestellten Programm, keine Änderung der Quelldatei auf dem Datenträger
und keine separate Arbeitskopie. Sie bilden nicht jedes Interpreterereignis ab.
Die GLPython-Visualisierung zu
`2 + 3 * 4` dient dem Vergleich, nicht als Definition unserer Schritte.
Die Regeln gelten für den hier verwendeten strikten Teilbereich:
Kurzschlussoperatoren, bedingte Ausdrücke und verkettete Vergleiche sind
nicht enthalten.

Für lokale Änderungen die Quelle im
[LiaScript LiveEditor](https://liascript.github.io/LiveEditor/) öffnen.
Der öffentliche Reader-Link zeigt erst nach Veröffentlichung auf `main`
den neuen Stand.

Planungsgrundlagen:
[Outline](../docs/lecture-outline.md),
[Didaktik](../docs/lecture-didactics.md#aufgaben-vollständig-im-kurs-bearbeiten),
[Agenda](../docs/lecture-agenda.md).
Diese konkrete Lektion bleibt ein zu erprobender Unterrichtsentwurf.
