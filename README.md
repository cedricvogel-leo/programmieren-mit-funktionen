<!--
author:   Cedric Vogel
version:  0.1.0
language: de

comment:  Eine interaktive Lerneinheit zu Funktionen in Python.

import: https://raw.githubusercontent.com/cedricvogel-leo/glpython-liascript/main/README.md
-->

# Programmieren mit Funktionen

[Im LiaScript-Reader öffnen](https://liascript.github.io/course/?https://raw.githubusercontent.com/cedricvogel-leo/programmieren-mit-funktionen/main/README.md)

In dieser Lerneinheit zerlegst du ein Programm in überschaubare Funktionen.
Du untersuchst Funktionsaufrufe, übergibst Argumente und verwendest Rückgabewerte.

**Voraussetzungen:** Du kennst Variablen, Rechenoperationen, `print` und einfache
`for`-Schleifen in Python. Erfahrung mit eigenen Funktionen brauchst du noch nicht.

**Zeitvorschlag:** 90 Minuten, zuzüglich einer optionalen Turtle-Aufgabe.

## So arbeitest du mit der Einheit

Öffne die Einheit über den Link zum LiaScript-Reader. Auf GitHub kannst du den
Text lesen; die interaktiven Python-Beispiele funktionieren im Reader.

1. Lies den Code und sage seine Ausgabe voraus.
2. Starte den Code über die Ausführen-Schaltfläche.
3. Nutze die schrittweise Visualisierung, um deine Vorhersage zu prüfen.
4. Ändere den Code und erkläre die Auswirkungen.

Python läuft über [GLPython](https://github.com/cedricvogel-leo/glpython-liascript)
im Browser. Eine lokale Python-Installation ist dafür nicht nötig; zum Laden des
Readers, des Makros und der Laufzeit brauchst du eine Internetverbindung.
Jeder Codeblock hat eine eigene Laufzeit. Deshalb enthalten die Beispiele alle
Definitionen, die sie benötigen.

## Lernziele

Am Ende kannst du:

1. eine Funktion definieren und mehrfach aufrufen;
2. Parameter und Argumente unterscheiden;
3. `return` von `print` unterscheiden und Rückgabewerte weiterverwenden;
4. lokale Variablen beim Ablauf eines Programms verfolgen;
5. wiederholten Code durch eine Funktion ersetzen und mit Beispielen prüfen.

## 1. Wiederholungen erkennen

Zwei Begrüßungen unterscheiden sich nur durch den Namen:

```python
print("Hallo, Ada!")
print("Willkommen im Python-Kurs.")

print("Hallo, Linus!")
print("Willkommen im Python-Kurs.")
```
@GLPython.eval

**Überlege:** Welche Zeilen müsstest du ändern, wenn die Begrüßung künftig aus
drei Zeilen bestehen soll? Was passiert, wenn du eine Stelle vergisst?

Eine Funktion gibt einem wiederverwendbaren Ablauf einen Namen.

## 2. Eine Funktion definieren und aufrufen

```python
def begruesse():
    print("Hallo!")
    print("Willkommen im Python-Kurs.")


begruesse()
begruesse()
```
@GLPython.eval

`def` beginnt die Definition. Der eingerückte Funktionskörper wird erst
ausgeführt, wenn die Funktion aufgerufen wird. Die Klammern gehören zum Aufruf.

**Aufgabe:** Ergänze eine dritte Zeile in der Funktion und rufe sie dreimal auf.
Prüfe anschließend, ob jeder Aufruf die neue Zeile ausgibt.

## 3. Parameter und Argumente

Mit einem Parameter kann derselbe Ablauf unterschiedliche Eingaben verarbeiten.

```python
def begruesse(name):
    print("Hallo, " + name + "!")


begruesse("Ada")
begruesse("Linus")
```
@GLPython.eval

`name` ist ein **Parameter** der Definition. `"Ada"` ist ein **Argument**, das
beim Aufruf an diesen Parameter gebunden wird.

**Aufgabe:** Ergänze einen zweiten Parameter `kurs`. Jeder Aufruf soll eine
Person in einem bestimmten Kurs begrüßen. Passe auch beide Aufrufe an.

## 4. Ergebnisse zurückgeben

`print` zeigt etwas an. `return` liefert einen Wert an die aufrufende Stelle
zurück und beendet den aktuellen Funktionsaufruf.

```python
def rechteckflaeche(breite, hoehe):
    return breite * hoehe


flaeche = rechteckflaeche(4, 3)
print(flaeche)
print(rechteckflaeche(2, 5) + flaeche)

assert rechteckflaeche(4, 3) == 12
assert rechteckflaeche(0, 5) == 0
```
@GLPython.eval

Die Ausgabe lautet zuerst `12`, dann `22`. Die `assert`-Anweisungen prüfen
Ergebnisse: Ist eine Bedingung falsch, wird ein Fehler angezeigt.

**Experiment:** Ersetze `return breite * hoehe` durch `print(breite * hoehe)`.
Untersuche die Ausgabe und die Fehlermeldung. Ohne explizites `return` liefert
eine Python-Funktion `None`; damit lässt sich hier nicht weiterrechnen.
Stelle danach die funktionierende Version wieder her.

## 5. Lokale Variablen verfolgen

Sage zunächst die beiden Ausgaben voraus. Gehe dann in der Visualisierung
schrittweise durch die Funktionsaufrufe.

```python
def verdopple(zahl):
    ergebnis = zahl * 2
    return ergebnis


zahl = 5
erster_wert = verdopple(zahl)
zweiter_wert = verdopple(erster_wert)
print(zahl)
print(zweiter_wert)
```
@GLPython.visual

**Erkläre:** Warum bleibt die Variable `zahl` außerhalb der Funktion gleich
`5`? Welche Werte hat der lokale Parameter `zahl` bei den beiden Aufrufen?

Der Parameter und `ergebnis` gehören zum jeweiligen Funktionsaufruf.
Der Parametername muss nicht mit dem Namen des übergebenen Wertes übereinstimmen.

## 6. Selbst anwenden

Schreibe die Funktion `gesamtpreis(einzelpreis, anzahl)`. Sie soll den
Gesamtpreis zurückgeben, nicht selbst ausgeben.

Ersetze `pass` durch deine Lösung. Die Vorlage ist absichtlich noch nicht
vollständig; die Prüfungen schlagen fehl, bis du sie ergänzt.

```python
def gesamtpreis(einzelpreis, anzahl):
    pass


assert gesamtpreis(3, 4) == 12
assert gesamtpreis(5, 0) == 0
assert gesamtpreis(2.5, 2) == 5.0
print("Alle Prüfungen bestanden.")
```
@GLPython.eval

**Transfer:** Speichere zwei Rückgabewerte für verschiedene Artikel in
Variablen und gib ihre Summe aus. Ergänze einen eigenen Testfall.

## 7. Optional: Zeichnen mit Funktionen

Auch Zeichenbefehle lassen sich zu einem benannten Ablauf zusammenfassen.

```python
from gturtle import *


def quadrat(seite):
    for _ in range(4):
        forward(seite)
        right(90)


makeTurtle()
quadrat(60)
quadrat(100)
```
@GLPython.turtle

**Aufgabe:** Zeichne drei unterschiedlich große Quadrate. Erkläre den
Unterschied zwischen dieser Funktion, die zeichnet, und einer Funktion, die
eine Fläche als Zahl zurückgibt.

## Rückblick

- Wann wird der Körper einer Funktion ausgeführt?
- Was unterscheidet einen Parameter von einem Argument?
- Wann brauchst du `return`, wann `print`?
- Wie helfen dir kleine Testfälle beim Ändern eines Programms?

**Abschluss:** Zeige eine selbst geschriebene Funktion mit zwei Aufrufen und
mindestens einer Prüfung. Begründe, welchen Teil des Programms sie vereinfacht.

## Hinweise für Lehrkräfte und Beitragende

Diese Datei ist zugleich der Einstieg und die ausführbare LiaScript-Quelle.
Der Ordner `docs/` folgt der Dateistruktur des
[Referenzprojekts](https://github.com/andre-dietrich/Datenbankensysteme-Vorlesung/tree/main/docs);
die vier Dokumente bleiben vorerst als leere Platzhalter bestehen.

- [Rahmen und Lernziele](docs/lecture-outline.md)
- [Ablauf und Zeitplanung](docs/lecture-agenda.md)
- [Didaktik, Makros und Bearbeitung](docs/lecture-didactics.md)
- [Vergleichsmatrix für die Reflexion](docs/paradigmen-matrix-template.md)

Zum Bearbeiten kannst du diese Datei im
[LiaScript LiveEditor](https://liascript.github.io/LiveEditor/) laden.
Prüfe Änderungen im Reader oder LiveEditor: normale Markdown-Vorschauen führen
die Makros nicht aus. Der Reader-Link oben verwendet den Stand auf GitHub;
lokale Änderungen sind dort erst nach dem Push auf `main` sichtbar.
