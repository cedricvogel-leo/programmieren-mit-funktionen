# Lecture Outline — Programmieren mit Funktionen

## Status und Zweck

Planungsgrundlage für eine neue Iteration der Unterrichtseinheit, noch kein
Kursmaterial. Alle bisher genannten Themen bleiben enthalten. Beispiele und
Unterrichtsformat dürfen sich ändern. Die bestehende README wird in dieser
Planungsphase nicht angepasst.

## Zielgruppe und Ausgangslage

11. Klasse, etwa 16–17 Jahre. Die Lernenden haben eine Einheit mit
[Algorithmen mit Snap!](https://computingeducation.de/algorithmen-mit-snap/)
und eine Einheit zur Übersetzung von Snap!- in Python-Programme bearbeitet.

Das bedeutet Vorerfahrung, nicht automatisch gesichertes Verständnis aller
Konzepte. Insbesondere sind selbst definierte Reporter, lokale Bindungen und
Rekursion nicht als beherrscht vorauszusetzen. Welche Wahlprojekte die Klasse
bearbeitet hat, ist noch zu klären.

## Leitidee

Die Lernenden sollen Programme nicht nur schreiben, sondern ihre Ausführung
mit expliziten Regeln erklären und vorhersagen können. Eine **notionale
Maschine** ist das dafür angebotene, bewusst vereinfachte Ausführungsmodell;
das **mentale Modell** ist die individuelle Vorstellung der Lernenden davon.
Beides muss nicht übereinstimmen. Diagnosen machen diese Unterschiede sichtbar.

Die [Didaktik](lecture-didactics.md) beschreibt die Modelle, ihre Grenzen und
die Forschungsgrundlage. Die [Agenda](lecture-agenda.md) übersetzt sie in eine
vorläufige Lernfolge. Die [Modellmatrix](paradigmen-matrix-template.md) hält
Diagnose und Beobachtungen zusammen.

## Inhaltlicher Rahmen

| Bereich | Rolle in der neuen Iteration |
| --- | --- |
| Python-Grundlagen | Vorwissen diagnostizieren und gezielt sichern, nicht die gesamte Vorgängereinheit wiederholen. |
| Ausdrücke | Werte, Auswertungsschritte und Auswertungskontext explizit machen. |
| Funktionen | Von mathematisch anschlussfähigen Ausdrücken zu Python-Aufrufen mit lokalen Bindungen und Rückkehr gelangen. |
| Design-Rezept | Entwurf, Beispiele, Implementierung und Prüfung als wiederkehrendes Vorgehen nutzen. |
| Rekursion | Dasselbe Aufrufmodell wiederverwenden; Ausführung und Entwurf durch Wunschdenken unterscheiden. |
| Programmiersprachen | Eine kleine Sprache spezifizieren, nachvollziehen und ihren Interpreter erweitern. |
| Lindenmayer-Systeme | Wortersetzung und anschließende Interpretation als verschiedene Prozesse verstehen. |

## Lernziele und beobachtbare Nachweise

Die IDs sind die Referenz für Agenda und Diagnosen. Die Tabellen decken die
gelieferten Lernziele ab; sprachliche Präzisierungen sind unten ausgewiesen.
Ein Lernziel ist nicht allein durch erfolgreiches Ausführen eines Programms
nachgewiesen.

### Python-Grundlagen

| ID | Die Lernenden können … | Beobachtbarer Nachweis |
| --- | --- | --- |
| PY1 | Verzweigungen und Schleifen in Python anwenden. | Einen Zweig und mehrere Schleifendurchläufe vorhersagen, begründen und einen Ablauf verändern. |
| PY2 | `+`, `-`, `*`, `/`, `%`, `//`, `==`, `!=`, `>`, `<`, `>=`, `<=` sowie Zuweisungen mit `=` und `+=` korrekt einsetzen. | Werte und Bindungsänderungen getrennt protokollieren; beispielsweise `-3 // 2 == -2` erklären. |
| PY3 | Mit einer `for`-Schleife die Zeichen einer Zeichenkette der Reihe nach verarbeiten. | Für eine kurze Zeichenkette die einzelnen Iterationswerte angeben und den leeren Fall behandeln. |
| PY4 | Zeichenketten mit `+` verknüpfen. | Die Reihenfolge einer Verkettung und den Unterschied zu numerischer Addition erklären. |

### Ausdrücke

| ID | Die Lernenden können … | Beobachtbarer Nachweis |
| --- | --- | --- |
| EX1 | Ausdrücke erkennen und erklären, dass ihre Auswertung einen Wert liefern kann. | Ausdrücke von Anweisungen wie Zuweisung oder `return` unterscheiden. |
| EX2 | Einen noch auszuwertenden Ausdruck von einem bereits bestimmten Wert unterscheiden. | Bei einer Reduktionsfolge Wert und verbleibende Rechnung kennzeichnen. |
| EX3 | Ausdrücke schrittweise nach den Regeln des vereinbarten Modells auswerten. | Den nächsten Schritt und den unveränderten umgebenden Ausdruck angeben; auch einen Fehler begründen. |

### Funktionen

| ID | Die Lernenden können … | Beobachtbarer Nachweis |
| --- | --- | --- |
| FU1 | Definition und Aufruf unterscheiden sowie Namen, Parameter, Rumpf und Argumente zuordnen. | Eine Definition und zwei Aufrufe beschriften; erklären, wann der Rumpf ausgeführt wird. |
| FU2 | Definitionen und Aufrufe in mathematischer und Python-Notation lesen und schreiben. | Eine reine Ausdrucksfunktion zwischen beiden Notationen übertragen und denselben Aufruf auswerten. |
| FU3 | Erklären, warum das einfache mathematische Einsetzmodell nicht jeden Python-Funktionsrumpf beschreibt. | Einen mehrzeiligen Rumpf mit Verzweigung oder Ausgabe mit dem Ausdrucksmodell vergleichen. |
| FU4 | Bei gewöhnlichen positionellen Aufrufen zuerst die Argumente von links nach rechts auswerten und dann den Rumpf mit gebundenen Parameterwerten ausführen. | Einen verschachtelten Aufruf in korrekter Reihenfolge verfolgen; nicht zuerst den äußeren Rumpf betreten. |
| FU5 | Funktionsaufrufe einschließlich lokaler Bindungen, Rückkehrstelle und Rückgabewert auswerten. | Zwei Aufrufe mit gleichnamigen Parametern getrennt protokollieren und die unterbrochene Rechnung fortsetzen. |
| FU6 | Fehlerhafte Aufrufe erkennen und ihre Ursache erklären. | Unbekannten Namen, falsche Anzahl positioneller Argumente und unzulässige Wertoperationen unterscheiden. |
| FU7 | Ausgabe durch `print` und Rückgabe durch `return` unterscheiden. | Ausgabeprotokoll und Rückgabewert getrennt vorhersagen; implizites `None` erklären. |
| FU8 | Erklären, dass nach Auswertung eines `return`-Ausdrucks der aktuelle Aufruf verlassen wird. | Eine unerreichbare Folgeanweisung markieren; bei rekursivem Rückgabeausdruck zunächst den inneren Aufruf verfolgen. |

### Rekursion

| ID | Die Lernenden können … | Beobachtbarer Nachweis |
| --- | --- | --- |
| RE1 | Rekursion als Selbstaufruf mit denselben Aufrufregeln verstehen und Wunschdenken als Entwurfsstrategie nutzen. | Einen kleineren Teilauftrag unter einer klaren Annahme zur Lösung des Gesamtauftrags verwenden. |
| RE2 | Einen Rekursionsanfang finden und erklären, warum rekursive Aufrufketten für die betrachteten Eingaben enden müssen. | Direkt lösbare Eingaben und ihre Ergebnisse benennen. |
| RE3 | Fehlenden Rekursionsanfang und offensichtlich nicht erreichte Abbruchfälle erkennen. | Ein Gegenbeispiel verfolgen und Nichtterminierung im Modell vom `RecursionError` der Laufzeit unterscheiden. |
| RE4 | Eine Aufgabe auf näher am Rekursionsanfang liegende Teilaufgaben zurückführen. | Für den angegebenen Eingabebereich eine abnehmende Größe und die Verkleinerung erklären. |
| RE5 | Eine passende rekursive Python-Funktion entwerfen, implementieren und prüfen. | Basisfall, rekursiven Fall und Kombination begründen; ausstehende Arbeit beim Rückweg erklären. |

### Design-Rezept

| ID | Die Lernenden können … | Beobachtbarer Nachweis |
| --- | --- | --- |
| DR1 | `pass` als Anweisung ohne Wirkung zum Platzhalten eines Blocks verwenden. | Einen syntaktisch gültigen Funktionsrumpf erstellen und erklären, dass spätere Anweisungen trotzdem ausgeführt werden. |
| DR2 | Das sechsstufige Design-Rezept mit und ohne Rekursion anwenden. | Namen, Parameter, Zweck, Beispiele, Rumpf und Prüfung als nachvollziehbare Zwischenstände dokumentieren. |
| DR3 | Nach jedem Rezeptschritt einen ausführbaren Zwischenstand erhalten. | Bis Schritt 3 läuft die Datei ohne Fehler; ab Schritt 4 dürfen bewusst noch nicht erfüllte Tests `AssertionError` auslösen. Die fertige Lösung besteht die vereinbarten Tests. |

### Programmiersprachen und Lindenmayer-Systeme

| ID | Die Lernenden können … | Beobachtbarer Nachweis |
| --- | --- | --- |
| SP1 | Spezifikation und Implementierung einer Sprache unterscheiden. | Syntax und Bedeutung einer kleinen Sprache beschreiben und einer Interpreterstelle zuordnen. |
| SP2 | Die Python-Implementierung der vereinbarten Lindenmayer-Zeichensprache nachvollziehen und um Befehle erweitern. | Einen zusätzlichen Befehl spezifizieren, den vorhandenen Interpreter anpassen und einen unterscheidenden Test erklären. |
| LS1 | Ersetzungsregeln eines L-Systems von einem Axiom aus über mehrere Generationen von Hand anwenden. | Alte und neue Generation getrennt notieren; erst danach das Ergebnis als Zeichenprogramm interpretieren. |

## Präzisierungen gegenüber den bisherigen Formulierungen

- `=` und `+=` sind hier Zuweisungsanweisungen, keine gewöhnlichen
  wertliefernden Operatoren. `//` rundet den Quotienten nach unten, nicht
  allgemein in Richtung null.
- „Wert“ ist der Begriff für das bestimmte Ergebnis, nicht die Behauptung,
  jedes beliebige Python-Objekt sei ein vollständig reduzierter Textausdruck.
- Mehrzeilige oder effektbehaftete Python-Funktionen liegen außerhalb der
  einfachen Übersetzung in mathematische Ausdrucksnotation. Das heißt nicht,
  dass ihr Verhalten grundsätzlich nicht mathematisch beschreibbar wäre.
- Bei einem `return` wird zuerst sein Ausdruck ausgewertet. Ein rekursiver
  Aufruf darin kann weitere Aufrufe und Rückgaben auslösen. Das Verlassen gilt
  jeweils für **einen Aufruf**, nicht pauschal für die gesamte Funktion.
- Nichtterminierende Definitionen können sehr wohl Auswertungsschritte
  ausführen; sie liefern im Modell nur kein abschließendes Ergebnis.
- `assert` ist eine Anweisung, keine Funktion. Die konkrete Gestaltung der
  Zwischenstände und der absichtlichen Testfehler steht in der
  [Didaktik](lecture-didactics.md#design-rezept-und-ausführbare-zwischenstände).

## Grenzen und offene Entscheidungen

Kein zusätzlicher Pflichtstoff sind Klassen, Closures, veränderbare
Container mit Aliasing, Funktionen höherer Ordnung oder das eigene Schreiben
eines L-System-Ersetzungsmotors. Für die Interpreter-Erweiterung werden
benötigte Schnittstellen und Operationen bereitgestellt.

Die Unterrichtsdauer, verbindliche Prüfungsform und tatsächlich bearbeiteten
Snap!-Wahlprojekte sind offen. Das Format kurzer Lernzyklen ist ein
begründeter Vorschlag, noch keine abschließende Entscheidung. Auch die Auswahl
des ersten Rekursionsproblems wird nach einer Prüfung der nötigen
Voraussetzungen festgelegt.