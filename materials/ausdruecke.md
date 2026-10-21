<!--
author:   Cedric Vogel
version:  0.2.0
language: de

comment:  Ausdrücke schrittweise auswerten: vorhersagen, erklären und mit Python prüfen.

import: https://raw.githubusercontent.com/cedricvogel-leo/glpython-liascript/main/README.md
-->

# Ausdrücke — was rechnet Python als Nächstes?

[Im LiaScript-Reader öffnen](https://liascript.github.io/course/?https://raw.githubusercontent.com/cedricvogel-leo/programmieren-mit-funktionen/main/materials/ausdruecke.md)

Sie haben bereits mit Snap! und Python programmiert. Jetzt untersuchen wir
genauer, **wie ein Ausdruck ausgewertet wird**.

Nach dieser Lektion können Sie:

- Ausdrücke von Zuweisungsanweisungen unterscheiden;
- einen Wert von einer noch offenen Rechnung unterscheiden;
- den nächsten Auswertungsschritt begründen;
- erklären, was bei einem Schritt unverändert bleibt;
- erkennen, wenn eine Auswertung zu einem Fehler statt zu einem Wert führt.

Arbeiten Sie zuerst ohne Ausführen-Schaltfläche. Tragen Sie Ihre Vorhersagen
in die Quizfelder ein und notieren Sie Ihre Begründungen auf Papier oder in
Ihren Notizen. Vergleichen Sie anschliessend Ihre Erklärungen miteinander.
Erst danach prüfen Sie Ihre Quizantworten oder führen Python aus.

Die Quizfelder geben Rückmeldung zu Ihren Antworten. Hinweise helfen bei
Bedarf weiter. Eine richtige Auswahl ersetzt nicht die Begründung.
Die Aufgaben-Checkboxen haken Sie selbst ab; sie bewerten Ihre Erklärung nicht.

Die Python-Felder sind im LiaScript-Reader ausführbar. Auf GitHub sind sie
nur Text. Zum Laden der Laufzeit benötigen Sie eine Internetverbindung;
eine eigene Python-Installation ist nicht nötig.

## 1. Erst vorhersagen

Welchen Wert haben diese Ausdrücke? Tragen Sie für die ersten beiden
Ausdrücke jeweils nur die Ergebniszahl ein.

**`2 + 3 * 4`**

[[14]]
[[?]] Welche Operation hat Vorrang: Addition oder Multiplikation?
***
Zuerst `3 * 4 → 12`, dann `2 + 12 → 14`.
***

**`(2 + 3) * 4`**

[[20]]
[[?]] Welche Teilrechnung wird durch die Klammern zusammengefasst?
***
Zuerst `2 + 3 → 5`, dann `5 * 4 → 20`.
***

**`"2" + "3"` — wählen Sie den Ergebniswert mit der passenden Wertart.**

- [( )] Die Zahl `5`.
- [( )] Die Zahl `23`.
- [(X)] Die Zeichenkette `"23"`.
- [( )] Es entsteht ein Fehler.
[[?]] Die Anführungszeichen kennzeichnen Zeichenketten.
***
`+` verknüpft hier zwei Zeichenketten. Das Ergebnis ist `"23"`, nicht die
Zahl `23`. Die reine Ausgabe durch `print` zeigt diesen Unterschied nicht.
***

- [ ] Ich habe zu jeder Vorhersage eine Begründung notiert.

**Vergleichen Sie:** Falls Sie verschiedene Ergebnisse erhalten haben,
markieren Sie den Schritt, an dem sich Ihre Erklärungen unterscheiden.

Prüfen Sie erst jetzt:

```python
print(2 + 3 * 4)
print((2 + 3) * 4)
print("2" + "3")
```
@GLPython.eval

<details>
<summary>Vergleich und Erklärung</summary>

Die Ausgaben lauten `14`, `20` und `23`.

- Im ersten Ausdruck wird das Produkt berechnet, bevor die Summe berechnet wird.
- Im zweiten Ausdruck legen die Klammern die Summe als erste Rechnung fest.
- Im dritten Ausdruck verbindet `+` zwei Zeichenketten. Der Wert ist `"23"`,
  nicht die Zahl `23`. Bei `print` werden die Anführungszeichen nicht angezeigt.

Ein richtiges Ergebnis ist ein Anfang. Entscheidend ist, dass Ihre Erklärung
auch bei einem anderen Ausdruck funktioniert.

</details>

## 2. Ausdruck, Wert oder Anweisung?

Ein **Ausdruck** ist ein Stück Programmtext, dessen Auswertung einen Wert
liefern kann. Zum Beispiel liefert die Auswertung von `2 + 3` den Wert `5`.

Manche Ausdrücke schreiben schon unmittelbar einen Wert hin: `5`, `"Hallo"`
oder `True`. Andere enthalten noch auszuführende Operationen oder Variablen,
deren gespeicherter Wert gelesen werden muss.

Ein Wert ist das bestimmte Ergebnis. Im Folgenden schreiben wir Werte mit
Python-Notation hin, zum Beispiel `5` oder `"Hallo"`.

Eine **Anweisung** legt einen Programmschritt fest. Die Zuweisung
`preis = 2 + 3` ist eine Anweisung: Erst wird rechts der Ausdruck ausgewertet,
dann wird das Ergebnis in der Variable `preis` gespeichert.

### Ordnen Sie zu und begründen Sie

Für diese Aufgabe ist in der Variable `preis` bereits die Zahl `5` gespeichert.

Wählen Sie in jeder Zeile genau eine Kategorie:

- **Wert direkt:** Ein Ausdruck schreibt unmittelbar einen Wert hin.
- **Noch auswerten:** Ein Ausdruck enthält eine Operation oder liest eine Variable.
- **Zuweisung:** Eine Anweisung speichert einen Wert.

[[Wert direkt] [Noch auswerten] [Zuweisung]]
[(X) ( ) ( )] `5`
[( ) (X) ( )] `2 + 3`
[( ) (X) ( )] `preis`
[( ) (X) ( )] `preis == 5`
[( ) ( ) (X)] `preis = 5`
[(X) ( ) ( )] `"Hallo"`
[[?]] Eine Zuweisung mit `=` ist kein Vergleich mit `==`.
***

| Programmtext | Einordnung |
| --- | --- |
| `5` | Ausdruck, der unmittelbar den Zahlenwert `5` hinschreibt. |
| `2 + 3` | Ausdruck mit noch auszuführender Addition. Ergebnis: `5`. |
| `preis` | Ausdruck, der den gespeicherten Wert einer Variable liest. Hier ergibt er `5`. |
| `preis == 5` | Vergleichsausdruck. Hier ergibt er den Wahrheitswert `True`. |
| `preis = 5` | Zuweisungsanweisung, kein Vergleichsausdruck. |
| `"Hallo"` | Ausdruck, der unmittelbar einen Zeichenkettenwert hinschreibt. |

Der Text `preis` ist nicht selbst die Zahl `5`. Er bezeichnet eine Variable,
in der hier `5` gespeichert ist. In der Rechnung lesen wir diesen Wert.

***

**Begründen Sie:** Warum gehört `preis` nicht in dieselbe Kategorie wie `5`,
obwohl beide hier denselben Wert ergeben?

- [ ] Ich habe den Unterschied zwischen Variablenname und gespeichertem Wert erklärt.

## 3. Unsere Auswertungsmaschine

Wir verwenden ein vereinfachtes Modell dafür, wie Python unsere Ausdrücke
auswertet. Ein solches menschenlesbares Modell heisst **notionale Maschine**.
Es ist keine zusätzliche Software. Sie können seine Schritte selbst ausführen.

Unsere Maschine betrachtet zunächst nur Zahlen, Zeichenketten, Variablen
mit gespeicherten Werten und einfache Rechen- und Vergleichsoperationen.

Sie zeigt zwei Dinge:

1. **Variablen als Boxen:** Welcher Wert ist gerade in welcher Variable gespeichert?
2. **Restlicher Ausdruck:** Was muss noch ausgewertet werden?

### Regeln für unsere Beispiele

- Steht eine Variable an der Reihe, lesen Sie ihren gespeicherten Wert.
- Beachten Sie Klammern und die Rangfolge der Operationen: etwa Multiplikation
  vor Addition. Bei `+` und `-` gleicher Rangstufe wird von links gruppiert.
- Führen Sie eine Operation erst aus, wenn die benötigten Operanden als Werte
  vorliegen.
- Ersetzen Sie nur den ausgewerteten Teil durch sein Ergebnis. Der umgebende
  Ausdruck bleibt unverändert.
- Ist eine Variable noch nicht definiert oder eine Operation für diese Werte nicht erlaubt,
  endet die Auswertung mit einem Fehler.

**Unsere Schreibweise:** `→` bedeutet «wird im nächsten Schritt ausgewertet zu».
Dieser Pfeil ist eine Erklärung auf Papier, kein Python-Operator.

```text
3 * (2 + 4)
→ 3 * 6
→ 18
```

Beim ersten Schritt wird nur `2 + 4` durch `6` ersetzt. Die Multiplikation
mit `3` wartet noch. Die Klammern um die einzelne Zahl können wir weglassen.

`→`, `=` und `==` bedeuten also Verschiedenes:

| Zeichen | Bedeutung |
| --- | --- |
| `→` | Ein Auswertungsschritt in unserer Erklärung. |
| `=` | Eine Zuweisung in Python. |
| `==` | Ein Vergleich in Python, dessen Ergebnis `True` oder `False` ist. |

Das Modell erklärt die Ausdrücke dieser Lektion, nicht schon alle Möglichkeiten
von Python. Eigene Funktionen und ihre Aufrufe untersuchen wir später.

## 4. Was bleibt bei einem Schritt stehen?

Gegeben ist:

```text
10 - 2 * (1 + 2)
```

**Ihre Aufgabe:**

1. Markieren Sie die Teilrechnung, die Sie als Nächstes auswerten.
2. Schreiben Sie genau einen Pfeilschritt auf.
3. Markieren Sie, welcher Teil unverändert geblieben ist.
4. Ergänzen Sie die restlichen Schritte.

**Welcher Ausdruck steht nach genau einem Auswertungsschritt da?**

- [( )] `8 * (1 + 2)`
- [(X)] `10 - 2 * 3`
- [( )] `10 - 6`
- [( )] `4`
[[?]] Ersetzen Sie nur die nächste Teilrechnung. Das Endergebnis ist noch kein einzelner Schritt.
***
Nur `1 + 2` wird zu `3`. Der Kontext `10 - 2 * …` bleibt erhalten.
`10 - 6` benötigt bereits zwei Rechenschritte, `4` drei.
***

Eine Person schlägt diesen Anfang vor:

```text
10 - 2 * (1 + 2)
→ 8 * (1 + 2)
```

**Erklären Sie:** Warum ist das kein erlaubter Schritt? Geben Sie nicht nur das
richtige Endergebnis an.

- [ ] Ich habe die falsche Spur mit einer Regel widerlegt und meine vollständige Spur notiert.

Prüfen Sie danach das Ergebnis:

```python
print(10 - 2 * (1 + 2))
```
@GLPython.eval

<details>
<summary>Lösung und Regelprüfung</summary>

```text
10 - 2 * (1 + 2)
→ 10 - 2 * 3
→ 10 - 6
→ 4
```

Zuerst wird die geklammerte Summe berechnet. `10 - 2 * …` bleibt dabei stehen.
Danach wird das Produkt berechnet, zuletzt die Differenz.

Der vorgeschlagene Schritt berechnet `10 - 2` zu früh: Die `2` ist ein
Operand der Multiplikation, deren Ergebnis erst anschliessend von `10`
abgezogen wird.

</details>

### Jetzt verändern

Setzen Sie in `10 - 2 * 3` Klammern so, dass der Wert `24` entsteht.
Notieren Sie zuerst die Auswertungsspur, ändern Sie dann das Python-Feld und
prüfen Sie das Ergebnis.

<details>
<summary>Eine Lösung</summary>

```text
(10 - 2) * 3
→ 8 * 3
→ 24
```

Nicht die Zahlen oder Operationen wurden geändert, sondern ihre Gruppierung.

</details>

## 5. Werte speichern, nicht Gleichungen

Lesen Sie dieses Programm, ohne es auszuführen:

```python
a = 3
b = a + 1
a = 8
print(b)
print(a + b)
```
@GLPython.eval

**Vorhersage:** Welche zwei Ausgaben entstehen?

Füllen Sie zunächst die Tabelle der gespeicherten Werte für die drei Zuweisungen aus:

| Nach der Anweisung | Wert von `a` | Wert von `b` |
| --- | --- | --- |
| `a = 3` | | noch nicht definiert |
| `b = a + 1` | | |
| `a = 8` | | |

**Welche Werte sind nach den drei Zuweisungen gespeichert?**

- [(X)] In `a` ist `8` gespeichert, in `b` ist `4` gespeichert.
- [( )] In `a` ist `8` gespeichert, in `b` ist `9` gespeichert.
- [( )] In `a` ist `3` gespeichert, in `b` ist `4` gespeichert.
[[?]] In `b` wird ein berechneter Wert gespeichert, keine dauerhaft nachzurechnende Formel.
***
Bei `b = a + 1` ist in `a` noch `3` gespeichert. Deshalb wird `4` in `b`
gespeichert. Die spätere Zuweisung an `a` ändert diesen Wert in `b` nicht.
***

Tragen Sie jeweils nur die Ausgabezahl ein:

**Erste Ausgabe: `print(b)`**

[[4]]

**Zweite Ausgabe: `print(a + b)`**

[[12]]
[[?]] Lesen Sie die zuletzt gespeicherten Werte aus beiden Variablen.

Schreiben Sie dann die Auswertung des letzten Ausdrucks `a + b` schrittweise auf.
Führen Sie erst danach das Programm aus.

<details>
<summary>Lösung und typische Fehlvorstellung</summary>

| Nach der Anweisung | Wert von `a` | Wert von `b` |
| --- | --- | --- |
| `a = 3` | `3` | noch nicht definiert |
| `b = a + 1` | `3` | `4` |
| `a = 8` | `8` | `4` |

Für die zweite Zuweisung wird `a + 1 → 3 + 1 → 4` ausgewertet.
In `b` wird dieser Wert gespeichert, keine dauerhaft nachzurechnende Formel.

Am Ende gilt:

```text
a + b
→ 8 + b
→ 8 + 4
→ 12
```

Die Ausgaben sind `4` und `12`. Die spätere Zuweisung an `a` ändert `b` nicht.

</details>

### Transfer

Was ändert sich, wenn Sie **nach** `a = 8` eine weitere Anweisung
`b = a + 1` einfügen? Erklären Sie die Änderung zuerst mit dem Modell.
Prüfen Sie anschliessend Ihre Vorhersage.

<details>
<summary>Vergleich</summary>

Die neu hinzugefügte Anweisung wertet `a + 1` mit dem jetzt gültigen Wert
von `a` aus: `8 + 1 → 9`. Danach ist in `b` der Wert `9` gespeichert.
Die Ausgaben ändern sich zu `9` und `17`.

</details>

## 6. Werte können auch Zeichenketten und Wahrheitswerte sein

Notieren Sie zu jedem Ausdruck eine Spur. Tragen Sie anschliessend den
Ergebniswert ein beziehungsweise wählen Sie ihn aus.
In dieser Aufgabe ist in der Variable `name` der Wert `"Ada"` gespeichert.

**`"Hallo, " + name`**

- [( )] Die Zeichenkette `"Hallo, name"`.
- [(X)] Die Zeichenkette `"Hallo, Ada"`.
- [( )] Es entsteht ein Fehler.

**`3 + 2 == 5`**

- [(X)] `True`
- [( )] `False`
- [( )] `5`
[[?]] Nach der Addition ist noch ein Vergleich auszuwerten.

**`7 // 2` — tragen Sie nur die Ergebniszahl ein.**

[[3]]

**`-3 // 2` — tragen Sie nur die Ergebniszahl ein.**

[[-2]]
[[?]] `//` rundet nach unten, nicht allgemein in Richtung null.
***
Der Quotient ist `-1.5`. Die nächste ganze Zahl darunter ist `-2`.
***

```python
name = "Ada"
print("Hallo, " + name)
print(3 + 2 == 5)
print(7 // 2)
print(-3 // 2)
```
@GLPython.eval

<details>
<summary>Lösung</summary>

```text
"Hallo, " + name → "Hallo, " + "Ada" → "Hallo, Ada"
3 + 2 == 5 → 5 == 5 → True
7 // 2 → 3
-3 // 2 → -2
```

`//` rundet den Quotienten nach unten. Bei `-1.5` ist das `-2`, nicht `-1`.
Ein Vergleich liefert einen Wahrheitswert, hier `True`.

Wir haben `-3` bereits als geschriebenen negativen Zahlenwert behandelt;
unser Modell zeigt nicht jeden internen Python-Auswertungsschritt einzeln.

</details>

## 7. Nicht jede Auswertung liefert einen Wert

Vergleichen Sie:

```text
"3" + "2"
3 + 2
"3" + 2
```

Welche Auswertungen sind möglich? Wo entsteht ein Fehler? Begründen Sie anhand der
Werte, mit denen die Operation arbeiten soll.

**Wählen Sie alle Ausdrücke aus, deren Auswertung einen Wert liefert.**

- [[X]] `"3" + "2"`
- [[X]] `3 + 2`
- [[ ]] `"3" + 2`
[[?]] Prüfen Sie, welche Wertarten als Operanden von `+` zusammenpassen.
***
Die ersten beiden Ausdrücke ergeben `"32"` beziehungsweise `5`.
Der dritte Ausdruck verbindet eine Zeichenkette mit einer Zahl; dies führt
hier zu `TypeError`.
***

Dieses Python-Beispiel enthält **absichtlich einen Fehler**. Notieren Sie
auch, welche Ausgaben Sie davor erwarten und ob die letzte Zeile erreicht wird.

**Welche Ausgabe beziehungsweise welcher Fehlerverlauf ist zu erwarten?**

- [( )] Ausgaben `32`, `5`, `32` und `Ende`; kein Fehler.
- [( )] Sofort ein `TypeError`, ohne vorherige Ausgabe.
- [(X)] Ausgaben `32` und `5`, danach `TypeError`; keine Ausgabe `Ende`.
- [( )] Ausgaben `32` und `5`, danach `NameError`; keine Ausgabe `Ende`.
***
Die ersten beiden Zeilen werden ausgeführt. Der Fehler entsteht erst bei
der dritten Addition. Danach wird die letzte Anweisung nicht mehr erreicht.
***

```python
print("3" + "2")
print(3 + 2)
print("3" + 2)
print("Ende")
```
@GLPython.eval

<details>
<summary>Lösung und Bedeutung der Fehlermeldung</summary>

Zuerst erscheinen `32` und `5`.
Danach trifft `+` auf eine Zeichenkette und eine Zahl. Python verbindet diese
beiden Werte nicht automatisch. Es entsteht ein `TypeError`.
Die Ausgabe `Ende` wird nicht mehr erreicht.

Der Text der Fehlermeldung kann je nach Laufzeit abweichen. Wichtig sind die
Fehlerart und die Erklärung: Diese Operanden passen hier nicht zusammen.

**Gezielte Änderung:** Wenn eine Verkettung gemeint ist, ändern Sie die Zahl zu
`"2"`. Wenn eine Addition gemeint ist, ändern Sie die Zeichenkette zu `3`.
Prüfen Sie beide Varianten getrennt. Eine Reparatur braucht also eine Entscheidung
darüber, was berechnet werden soll.

</details>

### Unbekannter Name

Jedes Codefeld dieser Lektion hat eine eigene Laufzeit. In diesem Feld
wurde die Variable `unbekannter_preis` noch nicht definiert.

**Was geschieht beim Versuch, `unbekannter_preis + 1` auszuwerten?**

- [( )] Der Wert ist `1`, weil eine unbekannte Variable automatisch `0` enthält.
- [(X)] Es entsteht ein `NameError`, bevor die Addition ausgeführt werden kann.
- [( )] Es entsteht ein `TypeError`, weil Zeichenketten und Zahlen gemischt werden.
***
Die Variable wurde noch nicht definiert. Es kann kein gespeicherter Wert
gelesen werden. Dieser Fehler ist vom Zusammenrechnen unpassender Wertarten
zu unterscheiden.
***

```python
print(unbekannter_preis + 1)
```
@GLPython.eval

<details>
<summary>Erklären statt raten</summary>

Beim Versuch, den Wert von `unbekannter_preis` zu lesen, entsteht ein `NameError`.
Diese Variable wurde hier noch nicht definiert. Python nimmt nicht automatisch `0`
an. Deshalb kann auch die Addition nicht ausgeführt werden.

Die vollständige Auswertungsspur endet am Fehler; es gibt keinen Ergebniswert
für den gesamten Ausdruck.

</details>

## 8. Abschluss — können Sie das Modell selbst anwenden?

Bearbeiten Sie diese Aufgaben **ohne Python-Ausführung**. Verwenden Sie bei
Ihren Erklärungen die Regeln unserer Maschine.

1. Ordnen Sie `4`, `n + 2`, `n == 4` und `n = 4` ein:
   Ausdruck oder Zuweisungsanweisung? Welcher Ausdruck schreibt direkt einen
   Wert hin?
2. In `n` ist `4` gespeichert. Werten Sie `2 * (n + 3) - 1` schrittweise aus.
   Markieren Sie bei einem Schritt den unveränderten Kontext.
3. Nach `n = 4; m = n * 2; n = 1`: Welchen Wert hat `m`? Warum?
4. Welche unterschiedliche Regel erklärt die Fehler in `"4" + 1` und
   `fehlender_name + 1`, wenn diese Variable noch nicht definiert wurde?
5. Erfinden Sie einen Ausdruck, bei dem Klammern das Ergebnis verändern.
   Notieren Sie beide Spuren und erklären Sie den Unterschied.

### Prüfen Sie ausgewählte Ergebnisse

Halten Sie Ihre vollständigen Spuren und Begründungen fest, bevor Sie die
Quizantworten prüfen.

**Aufgabe 1: Welche Texte sind Ausdrücke? Wählen Sie alle passenden aus.**

- [[X]] `4`
- [[X]] `n + 2`
- [[X]] `n == 4`
- [[ ]] `n = 4`
***
Die ersten drei Texte sind Ausdrücke. Nur `4` schreibt unmittelbar einen
Wert hin. `n = 4` ist eine Zuweisungsanweisung.
***

**Aufgabe 2: Welchen Wert ergibt `2 * (n + 3) - 1` für `n = 4`?
Tragen Sie nur die Ergebniszahl ein.**

[[13]]

**Aufgabe 3: Welcher Wert ist am Ende in `m` gespeichert?
Tragen Sie nur die Ergebniszahl ein.**

[[8]]
[[?]] Wird bei der späteren Zuweisung an `n` auch eine neue Zuweisung an `m` ausgeführt?

**Aufgabe 4: Welche Erklärung unterscheidet die beiden Fehler?**

- [( )] In beiden Fällen fehlt nur eine Klammer.
- [( )] Beide Ausdrücke lesen eine nicht definierte Variable.
- [(X)] Im ersten Fall passen die Wertarten nicht zusammen; im zweiten kann kein gespeicherter Variablenwert gelesen werden.
***
`"4" + 1` führt zu `TypeError`; die Verwendung der nicht definierten
Variable `fehlender_name` führt zu `NameError`.
***

### Eigene Arbeit prüfen

Diese Checkliste ist eine Selbsteinschätzung, keine automatische Bewertung.

- [ ] Ich habe in Aufgabe 2 den nächsten Schritt und den unveränderten Kontext markiert.
- [ ] Ich habe in Aufgabe 3 erklärt, warum die spätere Zuweisung den Wert in `m` nicht ändert.
- [ ] Ich habe für Aufgabe 5 zwei eigene Auswertungsspuren und eine Erklärung notiert.

Vergleichen Sie Ihre Begründungen miteinander. Prüfen Sie die selbst erfundenen Ausdrücke erst,
wenn die Spuren festgehalten sind.

<details>
<summary>Selbstkontrolle für Aufgaben 1–4</summary>

1. `4`, `n + 2` und `n == 4` sind Ausdrücke. `4` schreibt unmittelbar
   einen Wert hin. `n = 4` ist eine Zuweisungsanweisung.
2. Eine mögliche Spur ist:

   ```text
   2 * (n + 3) - 1
   → 2 * (4 + 3) - 1
   → 2 * 7 - 1
   → 14 - 1
   → 13
   ```

   Beim Ersetzen von `n` bleibt `2 * (… + 3) - 1` unverändert.
3. In `m` ist `8` gespeichert. Das spätere Speichern von `1` in `n` wertet die
   frühere rechte Seite nicht erneut aus.
4. `"4" + 1` scheitert an nicht passenden Wertarten (`TypeError`).
   `fehlender_name + 1` scheitert bereits beim Versuch, den Wert einer noch
   nicht definierten Variable zu lesen (`NameError`).

</details>

### Mein Modell in einem Satz

Vervollständigen Sie:

> Beim Auswerten eines Ausdrucks bestimme ich zuerst …
>
> Nach einem Schritt bleibt …
>
> Wenn ein Name oder eine Operation nicht passt, …

Notieren Sie zum Schluss eine Erklärung, die Sie heute geändert haben, und den
Grund dafür. Eine begründete Korrektur zeigt mehr als ein geratenes Ergebnis.

## Hinweise für Lehrkräfte

Diese Beispiellektion setzt den Ausdrucksteil von M1 um, nicht bereits das
gesamte Modul A1 mit mathematischen Funktionsaufrufen.
Sie bezieht sich auf EX1–EX3 sowie ausgewählte Voraussetzungen aus PY2 und PY4.
Sie ersetzt keine vollständige Grundlagen-Diagnose.

| Lernziel | Lerngelegenheiten | Individueller Nachweis |
| --- | --- | --- |
| EX1: Ausdrücke erkennen | Abschnitt 2; Kontrast zwischen Ausdruck und Zuweisung. | Abschlussaufgabe 1 mit Begründung. |
| EX2: Wert und offene Rechnung unterscheiden | Abschnitte 2–3; gespeicherte Variablenwerte und Restrechnung. | In Abschlussaufgabe 2 Zwischenausdrücke und Ergebnis unterscheiden. |
| EX3: Schritte und Fehler begründen | Abschnitte 4–7; absichtlich fehlerhafte Spur und Programme. | Abschlussaufgaben 2–4 und eine eigene Kontrastspur in Aufgabe 5. |

Die Lektion verwendet native LiaScript-Text-, Auswahl- und Matrixquizze sowie
Aufgaben-Checkboxen gemäss der
[LiaScript-Dokumentation](https://github.com/LiaScript/docs/blob/master/README.md#quizzes).
Die Quizze prüfen festgelegte Antworten, nicht die Qualität einer Begründung
oder einer selbst erfundenen Auswertungsspur. Freie Erklärungen werden weiterhin
auf Papier oder in eigenen Notizen festgehalten. Aufgaben-Checkboxen dienen
der Selbsteinschätzung und sind keine bewerteten Quizantworten.

Die Quizze erlauben erneute Versuche, Hinweise und das Anzeigen der Lösung.
Native Lösungsblöcke werden nach erfolgreicher Prüfung oder Auflösen sichtbar;
zusätzliche aufklappbare Erklärungen bleiben frei zugänglich.
Es handelt sich um formative Selbstkontrolle, nicht um eine gesperrte Prüfung.
Der öffentliche Reader-Link funktioniert erst, wenn
diese Datei auf `main` veröffentlicht wurde. Für lokale Änderungen die Quelle
im [LiaScript LiveEditor](https://liascript.github.io/LiveEditor/) öffnen.

`print` wird hier nur als bekanntes Mittel zum Sichtbarmachen verwendet.
Dass `print` selbst ein Funktionsaufruf ist und `None` zurückgibt, gehört in die
spätere Funktionslektion. Kein Ergebniswert entsteht allein dadurch, dass etwas
angezeigt wird. Für `"23"` und `23` muss die Wertart ausdrücklich mitbenannt
werden, weil die reine Ausgabe diesen Unterschied nicht zeigt.

Die Pfeilspuren sind didaktische Darstellungen, keine Behauptung über einzelne
Interpreterereignisse. GLPython prüft Resultate und Fehler; die manuelle Spur
bleibt nötig, wenn das Werkzeug Teilausdrücke nicht entsprechend sichtbar macht.

Planungsgrundlagen:
[Outline](../docs/lecture-outline.md),
[Didaktik](../docs/lecture-didactics.md),
[Agenda](../docs/lecture-agenda.md).
Die Entscheidung für explizite Modellregeln und aktive Erklärungen folgt der
dort eingeordneten Forschungsgrundlage; diese konkrete Lektion ist ein noch
zu erprobender Unterrichtsentwurf.
