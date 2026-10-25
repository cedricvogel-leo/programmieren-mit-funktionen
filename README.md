<!--
author:   Cedric Vogel
version:  1.0.0
language: de

comment:  Eine interaktive Lerneinheit zu Funktionen in Python. Test

import: https://raw.githubusercontent.com/cedricvogel-leo/glpython-liascript/main/README.md
-->

# Programmieren mit Funktionen

[Im LiaScript-Reader öffnen](https://liascript.github.io/course/?https://raw.githubusercontent.com/cedricvogel-leo/programmieren-mit-funktionen/main/README.md)

In dieser Lerneinheit zerlegen Sie ein Programm in überschaubare Funktionen.
Sie untersuchen Funktionsaufrufe, übergeben Argumente und verwenden Rückgabewerte.

**Voraussetzungen:** Sie kennen Variablen, Rechenoperationen, `print` und einfache
`for`-Schleifen in Python. Erfahrung mit eigenen Funktionen benötigen Sie noch nicht.

**Zeitvorschlag:** 90 Minuten, zuzüglich einer optionalen Turtle-Aufgabe.

## So arbeiten Sie mit der Einheit

Öffnen Sie die Einheit über den Link zum LiaScript-Reader. Auf GitHub können Sie den
Text lesen; die interaktiven Python-Beispiele funktionieren im Reader.

1. Lesen Sie den Code und notieren Sie Ihre Vorhersage seiner Ausgabe.
2. Starten Sie den Code über die Ausführen-Schaltfläche.
3. Nutzen Sie die schrittweise Visualisierung, um Ihre Vorhersage zu prüfen.
4. Ändern Sie den Code und erklären Sie die Auswirkungen.

Python läuft über [GLPython](https://github.com/cedricvogel-leo/glpython-liascript)
im Browser. Eine lokale Python-Installation ist dafür nicht nötig; zum Laden des
Readers, des Makros und der Laufzeit benötigen Sie eine Internetverbindung.
Jeder Codeblock hat eine eigene Laufzeit. Deshalb enthalten die Beispiele alle
Definitionen, die sie benötigen.

## Lernziele

Am Ende können Sie:

1. eine Funktion definieren und mehrfach aufrufen;
2. Parameter und Argumente unterscheiden;
3. `return` von `print` unterscheiden und Rückgabewerte weiterverwenden;
4. lokale Variablen beim Ablauf eines Programms verfolgen;
5. wiederholten Code durch eine Funktion ersetzen und mit Beispielen prüfen.

## 1. Wiederholungen erkennen

Zwei Begrüssungen unterscheiden sich nur durch den Namen:

```python
print("Hallo, Ada!")
print("Willkommen im Python-Kurs.")

print("Hallo, Linus!")
print("Willkommen im Python-Kurs.")
```
@GLPython.eval

**Untersuchen Sie:** Notieren Sie, welche Zeilen Sie ändern müssten, wenn die
Begrüssung künftig aus drei Zeilen bestehen soll. Beschreiben Sie, was passiert,
wenn Sie eine Stelle vergessen.

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

**Aufgabe:** Ergänzen Sie eine dritte Zeile in der Funktion und rufen Sie sie dreimal auf.
Prüfen Sie anschliessend, ob jeder Aufruf die neue Zeile ausgibt.

## 3. Parameter und Argumente

Mit einem Parameter kann derselbe Ablauf unterschiedliche Eingaben verarbeiten.

```python
def begruesse(name):
    print("Hallo, " + name + "!")


begruesse("Ada")
begruesse("Linus")
```
@GLPython.eval

`name` ist ein **Parameter** der Definition. `"Ada"` ist ein **Argument** des
Aufrufs. Dieser Wert wird in der Parametervariable `name` gespeichert.

**Aufgabe:** Ergänzen Sie einen zweiten Parameter `kurs`. Jeder Aufruf soll eine
Person in einem bestimmten Kurs begrüssen. Passen Sie auch beide Aufrufe an.

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

**Experiment:** Ersetzen Sie `return breite * hoehe` durch `print(breite * hoehe)`.
Untersuchen Sie die Ausgabe und die Fehlermeldung. Ohne explizites `return` liefert
eine Python-Funktion `None`; damit lässt sich die Addition in diesem Beispiel
nicht auswerten.
Stellen Sie danach die funktionierende Version wieder her.

## 5. Lokale Variablen verfolgen

Notieren Sie zunächst Ihre Vorhersage der beiden Ausgaben. Gehen Sie dann in
der Visualisierung schrittweise durch die Funktionsaufrufe.

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

**Erklären Sie:** Warum bleibt die Variable `zahl` ausserhalb der Funktion gleich
`5`? Welche Werte hat der lokale Parameter `zahl` bei den beiden Aufrufen?

Der Parameter und `ergebnis` gehören zum jeweiligen Funktionsaufruf.
Der Parametername muss nicht mit dem Namen des übergebenen Wertes übereinstimmen.

## 6. Selbst anwenden

Schreiben Sie die Funktion `gesamtpreis(einzelpreis, anzahl)`. Sie soll den
Gesamtpreis zurückgeben, nicht selbst ausgeben.

Ersetzen Sie `pass` durch Ihre Lösung. Die Vorlage ist absichtlich noch nicht
vollständig; die Prüfungen schlagen fehl, bis Sie sie ergänzen.

```python
def gesamtpreis(einzelpreis, anzahl):
    pass


assert gesamtpreis(3, 4) == 12
assert gesamtpreis(5, 0) == 0
assert gesamtpreis(2.5, 2) == 5.0
print("Alle Prüfungen bestanden.")
```
@GLPython.eval

**Transfer:** Speichern Sie zwei Rückgabewerte für verschiedene Artikel in
Variablen und geben Sie ihre Summe aus. Ergänzen Sie einen eigenen Testfall.

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

**Aufgabe:** Zeichnen Sie drei unterschiedlich grosse Quadrate. Erklären Sie den
Unterschied zwischen dieser Funktion, die zeichnet, und einer Funktion, die
eine Fläche als Zahl zurückgibt.

## Rückblick

- Wann wird der Körper einer Funktion ausgeführt?
- Was unterscheidet einen Parameter von einem Argument?
- Wann benötigen Sie `return`, wann `print`?
- Wie helfen Ihnen kleine Testfälle beim Ändern eines Programms?

**Abschluss:** Zeigen Sie eine selbst geschriebene Funktion mit zwei Aufrufen und
mindestens einer Prüfung. Begründen Sie, welchen Teil des Programms sie vereinfacht.

## Hinweise für Lehrkräfte und Beitragende

Diese Datei ist zugleich der Einstieg und die ausführbare LiaScript-Quelle.
Der Ordner `docs/` folgt der Dateistruktur des
[Referenzprojekts](https://github.com/andre-dietrich/Datenbankensysteme-Vorlesung/tree/main/docs);
die Dokumente enthalten die Planung der neuen Kursiteration.

- [Rahmen und Lernziele](docs/lecture-outline.md)
- [Ablauf und Zeitplanung](docs/lecture-agenda.md)
- [Didaktik, Makros und Bearbeitung](docs/lecture-didactics.md)
- [Vergleichsmatrix für die Reflexion](docs/paradigmen-matrix-template.md)
- [Sprachkonventionen](docs/sprachkonventionen.md)

Zum Bearbeiten können Sie diese Datei im
[LiaScript LiveEditor](https://liascript.github.io/LiveEditor/) laden.
Prüfen Sie Änderungen im Reader oder LiveEditor: normale Markdown-Vorschauen führen
die Makros nicht aus. Der Reader-Link oben verwendet den Stand auf GitHub;
lokale Änderungen sind dort erst nach dem Push auf `main` sichtbar.
