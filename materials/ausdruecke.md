<!--
author:   Cedric Vogel
version:  0.1.0
language: de

comment:  Ausdrücke schrittweise auswerten: vorhersagen, erklären und mit Python prüfen.

import: https://raw.githubusercontent.com/cedricvogel-leo/glpython-liascript/main/README.md
-->

# Ausdrücke — was rechnet Python als Nächstes?

[Im LiaScript-Reader öffnen](https://liascript.github.io/course/?https://raw.githubusercontent.com/cedricvogel-leo/programmieren-mit-funktionen/main/materials/ausdruecke.md)

Du hast bereits mit Snap! und Python programmiert. Jetzt untersuchen wir
genauer, **wie ein Ausdruck ausgewertet wird**.

Nach dieser Lektion kannst du:

- Ausdrücke von Zuweisungsanweisungen unterscheiden;
- einen Wert von einer noch offenen Rechnung unterscheiden;
- den nächsten Auswertungsschritt begründen;
- erklären, was bei einem Schritt unverändert bleibt;
- erkennen, wenn eine Auswertung zu einem Fehler statt zu einem Wert führt.

Arbeite zuerst ohne Ausführen-Schaltfläche. Notiere deine Vorhersage und eine
Begründung auf Papier oder in deinen Notizen. Vergleicht anschließend eure
Erklärungen. Erst danach prüfst du mit Python oder klappst die Lösung auf.

Die Python-Felder sind im LiaScript-Reader ausführbar. Auf GitHub sind sie
nur Text. Zum Laden der Laufzeit brauchst du eine Internetverbindung;
eine eigene Python-Installation ist nicht nötig.

## 1. Erst vorhersagen

Welchen Wert haben diese drei Ausdrücke?

| Ausdruck | Meine Vorhersage | Meine Begründung |
| --- | --- | --- |
| `2 + 3 * 4` | | |
| `(2 + 3) * 4` | | |
| `"2" + "3"` | | |

**Vergleicht:** Falls ihr verschiedene Ergebnisse habt: An welchem Schritt
unterscheiden sich eure Erklärungen?

Prüft erst jetzt:

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

Ein richtiges Ergebnis ist ein Anfang. Entscheidend ist, dass deine Erklärung
auch bei einem anderen Ausdruck funktioniert.

</details>

## 2. Ausdruck, Wert oder Anweisung?

Ein **Ausdruck** ist ein Stück Programmtext, dessen Auswertung einen Wert
liefern kann. Zum Beispiel liefert die Auswertung von `2 + 3` den Wert `5`.

Manche Ausdrücke schreiben schon unmittelbar einen Wert hin: `5`, `"Hallo"`
oder `True`. Andere enthalten noch auszuführende Operationen oder Namen,
deren Wert nachgeschlagen werden muss.

Ein Wert ist das bestimmte Ergebnis. Im Folgenden schreiben wir Werte mit
Python-Notation hin, zum Beispiel `5` oder `"Hallo"`.

Eine **Anweisung** legt einen Programmschritt fest. Die Zuweisung
`preis = 2 + 3` ist eine Anweisung: Erst wird rechts der Ausdruck ausgewertet,
dann wird der Name `preis` an das Ergebnis gebunden.

### Ordne zu und begründe

Für diese Aufgabe ist der Name `preis` bereits an die Zahl `5` gebunden.

1. Welche Zeilen sind Ausdrücke?
2. Welche davon schreiben schon unmittelbar einen Wert hin?
3. Welche Zeile ist eine Zuweisungsanweisung?

```text
5
2 + 3
preis
preis == 5
preis = 5
"Hallo"
```

<details>
<summary>Lösung mit Begründung</summary>

| Programmtext | Einordnung |
| --- | --- |
| `5` | Ausdruck, der unmittelbar den Zahlenwert `5` hinschreibt. |
| `2 + 3` | Ausdruck mit noch auszuführender Addition. Ergebnis: `5`. |
| `preis` | Ausdruck mit einem nachzuschlagenden Namen. Hier ergibt er `5`. |
| `preis == 5` | Vergleichsausdruck. Hier ergibt er den Wahrheitswert `True`. |
| `preis = 5` | Zuweisungsanweisung, kein Vergleichsausdruck. |
| `"Hallo"` | Ausdruck, der unmittelbar einen Zeichenkettenwert hinschreibt. |

Der Text `preis` ist nicht selbst die Zahl `5`. Der Name verweist hier auf
diesen Wert. Um ihn in einer Rechnung zu verwenden, schlagen wir die Bindung nach.

</details>

## 3. Unsere Auswertungsmaschine

Wir verwenden ein vereinfachtes Modell dafür, wie Python unsere Ausdrücke
auswertet. Ein solches menschenlesbares Modell heißt **notionale Maschine**.
Es ist keine zusätzliche Software. Du kannst seine Schritte selbst ausführen.

Unsere Maschine betrachtet zunächst nur Zahlen, Zeichenketten, bekannte
Namen und einfache Rechen- und Vergleichsoperationen.

Sie zeigt zwei Dinge:

1. **Bindungen:** Welcher Name steht gerade für welchen Wert?
2. **Restlicher Ausdruck:** Was muss noch ausgewertet werden?

### Regeln für unsere Beispiele

- Steht ein Name an der Reihe, schlage seinen gebundenen Wert nach.
- Beachte Klammern und die Rangfolge der Operationen: etwa Multiplikation
  vor Addition. Bei `+` und `-` gleicher Rangstufe wird von links gruppiert.
- Führe eine Operation erst aus, wenn die benötigten Operanden als Werte
  vorliegen.
- Ersetze nur den ausgewerteten Teil durch sein Ergebnis. Der umgebende
  Ausdruck bleibt unverändert.
- Ist ein Name unbekannt oder eine Operation für diese Werte nicht erlaubt,
  endet die Auswertung mit einem Fehler.

**Unsere Schreibweise:** `→` bedeutet „wird im nächsten Schritt ausgewertet zu“.
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

**Deine Aufgabe:**

1. Markiere die Teilrechnung, die du als Nächstes auswertest.
2. Schreibe genau einen Pfeilschritt auf.
3. Markiere, welcher Teil unverändert geblieben ist.
4. Ergänze die restlichen Schritte.

Eine Person schlägt diesen Anfang vor:

```text
10 - 2 * (1 + 2)
→ 8 * (1 + 2)
```

**Erkläre:** Warum ist das kein erlaubter Schritt? Gib nicht nur das richtige
Endergebnis an.

Prüfe danach das Ergebnis:

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
Operand der Multiplikation, deren Ergebnis erst anschließend von `10`
abgezogen wird.

</details>

### Jetzt verändern

Setze in `10 - 2 * 3` Klammern so, dass der Wert `24` entsteht.
Notiere zuerst die Auswertungsspur, ändere dann das Python-Feld und prüfe.

<details>
<summary>Eine Lösung</summary>

```text
(10 - 2) * 3
→ 8 * 3
→ 24
```

Nicht die Zahlen oder Operationen wurden geändert, sondern ihre Gruppierung.

</details>

## 5. Namen nachschlagen, nicht Gleichungen speichern

Lies dieses Programm, ohne es auszuführen:

```python
a = 3
b = a + 1
a = 8
print(b)
print(a + b)
```
@GLPython.eval

**Vorhersage:** Welche zwei Ausgaben entstehen?

Fülle zunächst die Bindungstabelle für die drei Zuweisungen aus:

| Nach der Anweisung | Wert von `a` | Wert von `b` |
| --- | --- | --- |
| `a = 3` | | noch nicht gebunden |
| `b = a + 1` | | |
| `a = 8` | | |

Schreibe dann die Auswertung des letzten Ausdrucks `a + b` schrittweise auf.
Führe erst danach das Programm aus.

<details>
<summary>Lösung und typische Fehlvorstellung</summary>

| Nach der Anweisung | Wert von `a` | Wert von `b` |
| --- | --- | --- |
| `a = 3` | `3` | noch nicht gebunden |
| `b = a + 1` | `3` | `4` |
| `a = 8` | `8` | `4` |

Für die zweite Zuweisung wird `a + 1 → 3 + 1 → 4` ausgewertet.
An `b` wird dieser Wert gebunden, keine dauerhaft nachzurechnende Formel.

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

Was ändert sich, wenn du **nach** `a = 8` eine weitere Anweisung
`b = a + 1` einfügst? Erkläre die Änderung zuerst mit dem Modell, dann prüfe.

<details>
<summary>Vergleich</summary>

Die neu hinzugefügte Anweisung wertet `a + 1` mit dem jetzt gültigen Wert
von `a` aus: `8 + 1 → 9`. Danach ist `b` an `9` gebunden.
Die Ausgaben ändern sich zu `9` und `17`.

</details>

## 6. Werte können auch Zeichenketten und Wahrheitswerte sein

Ergänze zu jedem Ausdruck eine Spur und den Ergebniswert.
In dieser Aufgabe ist `name` an `"Ada"` gebunden.

| Ausdruck | Meine Spur | Ergebniswert |
| --- | --- | --- |
| `"Hallo, " + name` | | |
| `3 + 2 == 5` | | |
| `7 // 2` | | |
| `-3 // 2` | | |

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

Vergleiche:

```text
"3" + "2"
3 + 2
"3" + 2
```

Welche Auswertungen sind möglich? Wo entsteht ein Fehler? Begründe anhand der
Werte, mit denen die Operation arbeiten soll.

Dieses Python-Beispiel enthält **absichtlich einen Fehler**. Sage auch voraus,
welche Ausgaben davor noch entstehen und ob die letzte Zeile erreicht wird.

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

**Gezielte Änderung:** Wenn eine Verkettung gemeint ist, ändere die Zahl zu
`"2"`. Wenn eine Addition gemeint ist, ändere die Zeichenkette zu `3`.
Prüfe beide Varianten getrennt. Eine Reparatur braucht also eine Entscheidung
darüber, was berechnet werden soll.

</details>

### Unbekannter Name

Jedes Codefeld dieser Lektion hat eine eigene Laufzeit. In diesem Feld
wurde `unbekannter_preis` nicht gebunden.

```python
print(unbekannter_preis + 1)
```
@GLPython.eval

<details>
<summary>Erklären statt raten</summary>

Beim Nachschlagen von `unbekannter_preis` entsteht ein `NameError`.
Der Name hat hier keinen gebundenen Wert. Python nimmt nicht automatisch `0`
an. Deshalb kann auch die Addition nicht ausgeführt werden.

Die vollständige Auswertungsspur endet am Fehler; es gibt keinen Ergebniswert
für den gesamten Ausdruck.

</details>

## 8. Abschluss — kannst du das Modell selbst anwenden?

Bearbeite diese Aufgaben **ohne Python-Ausführung**. Verwende bei deinen
Erklärungen die Regeln unserer Maschine.

1. Ordne `4`, `n + 2`, `n == 4` und `n = 4` ein:
   Ausdruck oder Zuweisungsanweisung? Welcher Ausdruck schreibt direkt einen
   Wert hin?
2. `n` ist an `4` gebunden. Werte `2 * (n + 3) - 1` schrittweise aus.
   Markiere bei einem Schritt den unveränderten Kontext.
3. Nach `n = 4; m = n * 2; n = 1`: Welchen Wert hat `m`? Warum?
4. Welche unterschiedliche Regel erklärt die Fehler in `"4" + 1` und
   `fehlender_name + 1`, wenn der Name nicht gebunden ist?
5. Erfinde einen Ausdruck, bei dem Klammern das Ergebnis verändern.
   Notiere beide Spuren und erkläre den Unterschied.

Vergleicht eure Begründungen. Prüft die selbst erfundenen Ausdrücke erst,
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
3. `m` ist an `8` gebunden. Die spätere Bindung von `n` an `1` wertet die
   frühere rechte Seite nicht erneut aus.
4. `"4" + 1` scheitert an nicht passenden Wertarten (`TypeError`).
   `fehlender_name + 1` scheitert bereits am Nachschlagen des Namens (`NameError`).

</details>

### Mein Modell in einem Satz

Vervollständige:

> Beim Auswerten eines Ausdrucks bestimme ich zuerst …
>
> Nach einem Schritt bleibt …
>
> Wenn ein Name oder eine Operation nicht passt, …

Notiere zum Schluss eine Erklärung, die du heute geändert hast, und den
Grund dafür. Eine begründete Korrektur zeigt mehr als ein geratenes Ergebnis.

## Hinweise für Lehrkräfte

Diese Beispiellektion setzt den Ausdrucksteil von M1 um, nicht bereits das
gesamte Modul A1 mit mathematischen Funktionsaufrufen.
Sie bezieht sich auf EX1–EX3 sowie ausgewählte Voraussetzungen aus PY2 und PY4.
Sie ersetzt keine vollständige Grundlagen-Diagnose.

| Lernziel | Lerngelegenheiten | Individueller Nachweis |
| --- | --- | --- |
| EX1: Ausdrücke erkennen | Abschnitt 2; Kontrast zwischen Ausdruck und Zuweisung. | Abschlussaufgabe 1 mit Begründung. |
| EX2: Wert und offene Rechnung unterscheiden | Abschnitte 2–3; Bindungen und Restrechnung. | In Abschlussaufgabe 2 Zwischenausdrücke und Ergebnis unterscheiden. |
| EX3: Schritte und Fehler begründen | Abschnitte 4–7; absichtlich fehlerhafte Spur und Programme. | Abschlussaufgaben 2–4 und eine eigene Kontrastspur in Aufgabe 5. |

Vorhersagen werden außerhalb der Codefelder festgehalten und nicht automatisch
gespeichert oder bewertet. Aufklappbare Lösungen sind Hilfen zur Selbstkontrolle,
keine gesperrte Prüfung. Der öffentliche Reader-Link funktioniert erst, wenn
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
