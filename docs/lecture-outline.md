# Lecture Outline — Programmieren mit Funktionen

## Status und Zweck

Planungsgrundlage für eine neue Iteration der Unterrichtseinheit, noch kein
Kursmaterial. Alle bisher genannten Themen bleiben enthalten. Beispiele und
Unterrichtsformat dürfen sich ändern. Die bestehende README wird in dieser
Planungsphase nicht angepasst.

## Zielgruppe und Ausgangslage

11. Klasse, etwa 16–17 Jahre. Die Schüler:innen haben eine Einheit mit
[Algorithmen mit Snap!](https://computingeducation.de/algorithmen-mit-snap/)
und eine Einheit zur Übersetzung von Snap!- in Python-Programme bearbeitet.

Das bedeutet Vorerfahrung, nicht automatisch gesichertes Verständnis aller
Konzepte. Insbesondere sind selbst definierte Reporter, eigene lokale Variablen pro Aufruf und
Rekursion nicht als beherrscht vorauszusetzen. Welche Wahlprojekte die Klasse
bearbeitet hat, ist noch zu klären.

## Leitidee

Die Schüler:innen sollen Programme nicht nur schreiben, sondern ihre Ausführung
mit expliziten Regeln erklären und vorhersagen können. Eine **notionale
Maschine** ist das dafür angebotene, bewusst vereinfachte Ausführungsmodell;
das **mentale Modell** ist die individuelle Vorstellung der Schüler:innen davon.
Beides muss nicht übereinstimmen. Diagnosen machen diese Unterschiede sichtbar.

Die [Didaktik](lecture-didactics.md) beschreibt die Modelle, ihre Grenzen und
die Forschungsgrundlage. Diese Outline legt die konzeptuelle Aufbaufolge der
Lerneinheiten fest. Die [Agenda](lecture-agenda.md) und die
[Modellmatrix](paradigmen-matrix-template.md) enthalten noch die bisherige
Modulstruktur und sind in einem späteren Schritt damit abzugleichen.

Das bekannte Box-Modell der Variablen bleibt erhalten: Werte werden in
Variablen gespeichert und von dort gelesen. Geltungsbereich und Grenze bei
gemeinsam verwendeten veränderbaren Objekten stehen in der
[didaktischen Festlegung](lecture-didactics.md#festlegung-werte-werden-in-variablen-gespeichert).

## Aufbau und Vorkenntnisse

Die Lerneinheiten verbinden wenige Leitkonzepte mit ihren Auswertungs- oder
Ausführungsregeln. Teilausdrücke, Klammerung und Ersetzen sind beispielsweise
Bestandteile des Auswertens von Ausdrücken, keine zusätzlichen gleichrangigen
Einheiten. Funktionen werden über die ersten beiden Einheiten aufgebaut,
nicht als separate Lerneinheit behandelt.

Eine eigene Einheit «Python-Grundlagen» entfällt. Bekannte Verzweigungen,
Schleifen, Zeichenkettenverkettung, Zeichenschleifen und die bisher verwendeten
arithmetischen und Vergleichsoperationen bleiben Vorkenntnisse. Lücken werden
bei Bedarf gezielt aufgegriffen. Die Semantik dieser Anweisungen wird später
im Zusammenhang mit der zweiten Maschine präzisiert.

Die bisherigen IDs PY1–PY4 werden deshalb nicht mehr als Ziele einer eigenen
Lerneinheit geführt. Verweise darauf in Agenda und Modellmatrix beziehen sich
bis zu deren Überarbeitung auf diesen Vorwissensbestand.

Die EX-, FU- und RE-IDs bleiben erhalten und werden den Einheiten zugeordnet,
in denen die betreffenden Modelle aufgebaut werden. Ein richtiges Ergebnis
allein weist ein Lernziel nicht nach; die jeweilige Erklärung gehört dazu.
Design-Rezept und Programmiersprachen werden später ausgearbeitet.

## Ausdrücke

### Konzepte und Aufbaufolge

| Reihenfolge | Konzept | Aufbau des mentalen Modells |
| --- | --- | --- |
| 1 | Ausdrücke | Unausgewertete Ausdrücke von ausgewerteten Ausdrücken unterscheiden. «Ausgewerteter Ausdruck» und «Wert» sind Synonyme. |
| 2 | Auswerten von Ausdrücken | Zunächst ohne Speicher arbeiten. Die Ausdrucksstruktur bestimmt die unmittelbaren Teilausdrücke; diese werden von links nach rechts ausgewertet. Erst wenn sie Werte sind, die Operation ausführen und den Ausdruck durch seinen Wert ersetzen. Den umgebenden Ausdruck erhalten. |
| 3 | Speicher | Das bekannte Box-Modell aktivieren: Benannte Variablen enthalten Werte. Zunächst ist der Speicher vorgegeben; wie er durch Anweisungen verändert wird, folgt später. |
| 4 | Auswerten im Kontext eines Speichers | Beim Auswerten einer Variable ihren gespeicherten Wert lesen und an ihrer Stelle im dargestellten Ausdruck einsetzen. |
| 5 | Funktionsdefinition | Name, Parameter und einen eingeschränkten Rumpf aus genau `return ausdruck` beschreiben. Nur den vereinbarten reinen Teilbereich verwenden. |
| 6 | Funktionsdefinitionen im Speicher | Unter einem Namen kann eine Funktionsdefinition verfügbar sein. Datenwerte in Variablenboxen und gespeicherte Definitionen in der Darstellung unterscheiden. Parameter sind dabei noch keine lokalen Variablen eines Aufrufs. |
| 7 | Funktionsaufrufe | Definition finden, Argumente von links nach rechts zu Werten auswerten und den Aufruf durch den geklammerten Rückgabeausdruck mit eingesetzten Argumentwerten ersetzen. Diesen Ausdruck anschliessend weiter auswerten. |

**Ergebnis:** Die erste Maschinenversion, die Ausdrucks- und Einsetzmaschine,
ist aufgebaut. Definitionen und Variablenwerte stehen zunächst bereit.
Die allgemeine Ausführung von `def`, Zuweisungen und Funktionsrümpfen ist
noch nicht Gegenstand dieser Version.

Die Auswertung ersetzt Teilausdrücke an Ort und Stelle im dargestellten
Programm, ohne eine separate Arbeitskopie einzuführen. Vorgegebene Speicher
erscheinen als Block mit optionalen Unterblöcken «Variablen» und «Funktionen»;
Definitionen werden vollständig aufgelistet. Das
[Speicherprotokoll](lecture-didactics.md#speicherzustand-und-speicherprotokoll)
für zeitliche Veränderungen bleibt davon unterschieden.

Der reine Teilbereich verwendet Parameter, Konstanten und passende reine
Funktionsaufrufe, aber keine Ausgabe, Zustandsänderungen oder Abhängigkeiten
von veränderlichen globalen Werten. Ein einziger `return` garantiert diese
Eigenschaft noch nicht. Kurzschlussoperatoren wie `and` und `or`, bedingte
Ausdrücke und verkettete Vergleiche benötigen eigene Regeln und bleiben
zunächst ausserhalb der beschriebenen Auswertung.

### Lernziele und Nachweise

| ID | Die Schüler:innen können … | Beobachtbarer Nachweis |
| --- | --- | --- |
| EX1 | Ausdrücke erkennen und erklären, dass ihre Auswertung einen Wert liefern kann. | Beispiele mit festen Werten, Variablen und Operationen als Ausdrücke einordnen und ihren möglichen Ergebniswert erklären. |
| EX2 | Unausgewertete Ausdrücke von ausgewerteten Ausdrücken unterscheiden und «ausgewerteter Ausdruck» und «Wert» als Synonyme verwenden. | In einem Auswertungsprotokoll unausgewertete Ausdrücke und Werte kennzeichnen und die Begriffe erklären. |
| EX3 | Ausdrücke schrittweise nach den Regeln des vereinbarten Modells auswerten. | Den nächsten Schritt und den unveränderten umgebenden Ausdruck angeben; auch einen Fehler begründen. |
| FU1 | Definition und Aufruf unterscheiden sowie Namen, Parameter, Rumpf und Argumente zuordnen. | Eine bereitgestellte Definition und zwei Aufrufe beschriften; erklären, dass das Bereitstellen der Definition ihren Rückgabeausdruck noch nicht auswertet. |
| FU2 | Definitionen und Aufrufe in mathematischer und Python-Notation lesen und schreiben. | Eine reine Ausdrucksfunktion zwischen beiden Notationen übertragen und denselben Aufruf durch geklammertes Einsetzen auswerten. |
| FU6 | Fehlerhafte Aufrufe erkennen und ihre Ursache erklären. | Unbekannten Funktionsnamen, falsche Anzahl positioneller Argumente und unzulässige Wertoperationen unterscheiden. |

Die Nachweise verbinden diese Ziele: einen Variablenwert aus einem vorgegebenen
Speicher lesen, eine Definition unter ihrem Namen finden und einen
verschachtelten Aufruf auswerten. Dabei müssen zuerst die Argumentwerte
entstehen, bevor der Rückgabeausdruck eingesetzt wird.

## Anweisungen

### Konzepte und Aufbaufolge

| Reihenfolge | Konzept | Aufbau des mentalen Modells |
| --- | --- | --- |
| 8 | Anweisungen | Ausdrücke auswerten und Anweisungen ausführen unterscheiden. Eine Anweisungsfolge und die aktuelle Ausführungsstelle darstellen. |
| 9 | Semantik bekannter Anweisungen | Zuweisungen, Verzweigungen, Schleifen und Definitionsanweisungen nach expliziten Regeln ausführen. Blöcke als enthaltene Anweisungsfolgen erklären. |
| 10 | Lokaler Speicher | Den bisherigen Speicher als globalen Speicher einordnen. Für jeden Funktionsaufruf eigene lokale Variablen vorsehen. |
| 11 | Funktionsaufrufe mit allgemeinerem Rumpf | Rumpf am Aufrufort einblenden, Argumentwerte in eigenen Parametervariablen speichern, Rumpfanweisungen ausführen und den Aufruf durch den Rückgabewert ersetzen. |

Bei einer Zuweisung wird erst der rechte Ausdruck ausgewertet, danach sein
Wert gespeichert. Beim Ausführen von `def` wird die Definition unter ihrem
Namen verfügbar, ohne den Rumpf auszuführen. Damit wird nun erklärt, wie die
in der ersten Einheit vorgegebenen Speicherinhalte entstehen können.

Erhaltener Ausdruckskontext, Ausgabe und Ausgabeprotokoll sowie
`return` und implizites `None` sind Bestandteile dieser Aufrufsemantik,
keine zusätzlichen Lerneinheiten. Der Aufrufort zeigt die Rückgabestelle;
«wartender Ausdruck» wird nicht als gesondertes Konzept verlangt.
Bei Schleifen wird erneut benötigter Code wiederhergestellt, nicht der
Speicher oder die Ausgabe. Die Fortsetzung nach regulärem Abschluss einer
Anweisung wird von Rückgabe und Fehler unterschieden.

**Ergebnis:** Die zweite Maschinenversion, die Anweisungs- und Aufrufmaschine,
ist aufgebaut. «Allgemeinerer Rumpf» meint mehrere Anweisungen und die
vereinbarten Kontrollstrukturen, nicht beliebige bisher ausgeschlossene
Python-Sprachmerkmale.

### Lernziele und Nachweise

| ID | Die Schüler:innen können … | Beobachtbarer Nachweis |
| --- | --- | --- |
| AN1 | Ausdrucksauswertung von Anweisungsausführung unterscheiden. | Bei einer Zuweisung die Auswertung der rechten Seite, das Speichern des Wertes und das Fortsetzen an der nächsten Anweisung getrennt erklären. |
| AN2 | Bekannte Zuweisungen, Verzweigungen, Schleifen und Definitionsanweisungen im Maschinenmodell ausführen. | Speicherzustand und Ausführungsstelle verfolgen; bei Wiederholung den benötigten Code wiederherstellen und aktuelle Speicherwerte erhalten; bei `def` keinen Rumpf ausführen. |
| FU3 | Erklären, warum das einfache mathematische Einsetzmodell nicht jeden Python-Funktionsrumpf beschreibt. | Einen mehrzeiligen Rumpf mit Verzweigung oder Ausgabe mit dem Ausdrucksmodell vergleichen. |
| FU4 | Bei gewöhnlichen positionellen Aufrufen zuerst die Argumente von links nach rechts auswerten, die Werte in den Parametervariablen speichern und dann den Rumpf ausführen. | Einen verschachtelten Aufruf in korrekter Reihenfolge verfolgen; nicht zuerst den äusseren Rumpf betreten. |
| FU5 | Funktionsaufrufe einschliesslich lokaler Variablenwerte, Rückgabestelle am Aufrufort und Rückgabewert auswerten. | Zwei Aufrufe mit gleichnamigen Parametern getrennt protokollieren und ihren Rückgabewert jeweils im erhaltenen Ausdruckskontext einsetzen. |
| FU7 | Ausgabe durch `print` und Rückgabe durch `return` unterscheiden. | Ausgabeprotokoll und Rückgabewert getrennt vorhersagen; implizites `None` erklären. |
| FU8 | Erklären, dass nach Auswertung eines `return`-Ausdrucks der aktuelle Aufruf verlassen wird. | Eine unerreichbare Folgeanweisung markieren; bei rekursivem Rückgabeausdruck zunächst den inneren Aufruf verfolgen. |

Die Argumentauswertung aus der ersten Einheit bleibt gültig. FU4 erweitert
sie um das Speichern der Argumentwerte und das Ausführen des Rumpfs.
Fehlerhafte Aufrufe aus FU6 werden auch mit der zweiten Version erklärt.
Rekursive Beispiele zu FU8 werden erst in der folgenden Einheit verwendet.

## Rekursion

### Konzepte und Aufbaufolge

| Reihenfolge | Konzept | Aufbau des mentalen Modells |
| --- | --- | --- |
| 12 | Rekursion | Dieselbe Funktion aus ihrem Rumpf heraus aufrufen. Die bekannte Regel blendet weitere Rümpfe mit eigenen lokalen Speichern am jeweiligen Aufrufort ein, keine neue Art der Ausführung. |

Basisfall, Verkleinerung und Wunschdenken werden innerhalb dieses Konzepts
behandelt. Die Schüler:innen unterscheiden den Entwurf einer Lösung für ein
kleineres Problem von der konkreten Ausführung mehrerer Aufrufe.
Die Einblendungen zeigen die noch nicht abgeschlossenen Aufrufe.
Ein optionales Aufrufstapelbild stellt dieselben Aufrufe zusätzlich dar.

**Ergebnis:** Die zweite Maschinenversion erklärt auch Rekursion. Eine dritte
Aufrufregel ist nicht nötig. Vorwissen zu Verzweigungen und die
Anweisungssemantik der vorherigen Einheit werden vorausgesetzt.

### Lernziele und Nachweise

| ID | Die Schüler:innen können … | Beobachtbarer Nachweis |
| --- | --- | --- |
| RE1 | Rekursion als Selbstaufruf mit denselben Aufrufregeln verstehen und Wunschdenken als Entwurfsstrategie nutzen. | Einen kleineren Teilauftrag unter einer klaren Annahme zur Lösung des Gesamtauftrags verwenden. |
| RE2 | Einen Rekursionsanfang finden und erklären, warum rekursive Aufrufketten für die betrachteten Eingaben enden müssen. | Direkt lösbare Eingaben und ihre Ergebnisse benennen. |
| RE3 | Fehlenden Rekursionsanfang und nicht erreichte Abbruchfälle erkennen. | Ein Gegenbeispiel verfolgen und Nichtterminierung im Modell vom `RecursionError` der Laufzeit unterscheiden. |
| RE4 | Eine Aufgabe auf näher am Rekursionsanfang liegende Teilaufgaben zurückführen. | Für den angegebenen Eingabebereich eine abnehmende Grösse und die Verkleinerung erklären. |
| RE5 | Eine passende rekursive Python-Funktion entwerfen, implementieren und prüfen. | Basisfall, rekursiven Fall und Kombination begründen; ausstehende Arbeit beim Rückweg erklären. |

## Design-Rezept

**Zurückgestellt:** Konzepte und Einordnung dieser Lerneinheit werden später
bearbeitet. Die folgenden Lernziele bleiben als bisheriger Arbeitsstand
erhalten. Die vorangehende Rekursionseinheit setzt die eigenständige
Ausarbeitung des vollständigen Rezepts nicht voraus.

### Bisherige Lernziele und Nachweise

| ID | Die Schüler:innen können … | Beobachtbarer Nachweis |
| --- | --- | --- |
| DR1 | `pass` als Anweisung ohne Wirkung zum Platzhalten eines Blocks verwenden. | Einen syntaktisch gültigen Funktionsrumpf erstellen und erklären, dass spätere Anweisungen trotzdem ausgeführt werden. |
| DR2 | Das sechsstufige Design-Rezept mit und ohne Rekursion anwenden. | Namen, Parameter, Zweck, Beispiele, Rumpf und Prüfung als nachvollziehbare Zwischenstände dokumentieren. |
| DR3 | Nach jedem Rezeptschritt einen ausführbaren Zwischenstand erhalten. | Bis Schritt 3 läuft die Datei ohne Fehler; ab Schritt 4 dürfen bewusst noch nicht erfüllte Tests `AssertionError` auslösen. Die fertige Lösung besteht die vereinbarten Tests. |

## Programmiersprachen

**Zurückgestellt:** Konzepte und Aufbaufolge werden später bearbeitet.
Lindenmayer-Systeme gehören zu dieser Lerneinheit. Die folgenden Lernziele
bleiben als bisheriger Arbeitsstand erhalten.

### Bisherige Lernziele und Nachweise

| ID | Die Schüler:innen können … | Beobachtbarer Nachweis |
| --- | --- | --- |
| SP1 | Spezifikation und Implementierung einer Sprache unterscheiden. | Syntax und Bedeutung einer kleinen Sprache beschreiben und einer Interpreterstelle zuordnen. |
| SP2 | Die Python-Implementierung der vereinbarten Lindenmayer-Zeichensprache nachvollziehen und um Befehle erweitern. | Einen zusätzlichen Befehl spezifizieren, den vorhandenen Interpreter anpassen und einen unterscheidenden Test erklären. |
| LS1 | Ersetzungsregeln eines L-Systems von einem Axiom aus über mehrere Generationen von Hand anwenden. | Alte und neue Generation getrennt notieren; erst danach das Ergebnis als Zeichenprogramm interpretieren. |

## Präzisierungen gegenüber den bisherigen Formulierungen

- `=` und `+=` sind hier Zuweisungsanweisungen, keine gewöhnlichen
  wertliefernden Operatoren. `//` rundet den Quotienten nach unten, nicht
  allgemein in Richtung null.
- «Ausgewerteter Ausdruck» und «Wert» sind im Unterrichtsmodell Synonyme.
  Das ist nicht die Behauptung,
  jedes beliebige Python-Objekt sei ein vollständig reduzierter Textausdruck.
- Mehrzeilige oder effektbehaftete Python-Funktionen liegen ausserhalb der
  einfachen Übersetzung in mathematische Ausdrucksnotation. Das heisst nicht,
  dass ihr Verhalten grundsätzlich nicht mathematisch beschreibbar wäre.
- Bei einem `return` wird zuerst sein Ausdruck ausgewertet. Ein rekursiver
  Aufruf darin kann weitere Aufrufe und Rückgaben auslösen. Das Verlassen gilt
  jeweils für **einen Aufruf**, nicht pauschal für die gesamte Funktion.
- Nichtterminierende Definitionen können sehr wohl Auswertungsschritte
  ausführen; sie liefern im Modell nur kein abschliessendes Ergebnis.
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
begründeter Vorschlag, noch keine abschliessende Entscheidung. Auch die Auswahl
des ersten Rekursionsproblems wird nach einer Prüfung der nötigen
Voraussetzungen festgelegt.