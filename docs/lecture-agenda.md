# Lecture Agenda — Konzept- und Lernfolge

## Status

Dies ist eine vorläufige Abfolge von Lernmodulen, keine Präsentationsgliederung
und kein fertiger Stundenplan. Umfang und Prüfungsrahmen sind noch offen.
Modulgrenzen sind keine Festlegung auf einzelne Unterrichtsstunden.

Die Lernziel-IDs stammen aus der [Outline](lecture-outline.md).
M1–M6 bezeichnen die Modelle in der [Didaktik](lecture-didactics.md).
Beobachtungen werden in der [Modellmatrix](paradigmen-matrix-template.md)
gesammelt.

Vorgeschlagen sind kurze Lernzyklen mit Vorhersage, Handspur, Erklärung,
Werkzeugvergleich und eigener Anwendung. Lehrkraftimpulse und längere
Arbeitsphasen bleiben möglich; das endgültige Format ist nicht entschieden.

## Abhängigkeiten

- A0 diagnostiziert die Grundlagen und bestimmt nötige Unterstützung.
- A1 baut auf Ausdrucks- und Bindungsverständnis aus A0 auf.
- A2 setzt A1 voraus und entwickelt dessen Ausdrucksmodell weiter.
- A3 verwendet A2 für Entwurf und Prüfung wertliefernder Funktionen.
- A4 verbindet A2 und A3 für rekursive Aufrufe und rekursiven Entwurf.
- A5 braucht Funktionen, Verzweigungen und Zeichenschleifen aus A0–A3;
  Rekursion ist für einen einfachen Interpreter keine Voraussetzung.
- A6 setzt die Unterscheidung von Quellwort und Interpretation aus A5 voraus.
- A7 führt die Nachweise zusammen. Rekursive und sprachbezogene Aufgaben
  dürfen unterschiedliche Kontexte verwenden, müssen aber die gemeinsamen
  Lernziele abdecken.

Die aufgeführte Reihenfolge ist ein Vorschlag. A5 muss nicht künstlich von
Rekursion abhängig gemacht werden. Eine Umstellung darf jedoch die expliziten
Modellübergänge nicht überspringen.

## A0 — Vorwissen und vorhandene Modelle sichtbar machen

**Ziele:** PY1–PY4; Voraussetzungen für EX1–EX3.

**Voraussetzungen:** Bearbeitete Snap!- und Python-Übersetzungseinheiten,
ohne daraus individuelle Beherrschung abzuleiten.

**Modellarbeit:** Bekannte Bindungen, Ausgaben, Zweigwahl und Schleifendurchläufe
unterscheiden. Noch kein neuer vollständiger Funktionsmechanismus.

**Diagnose:** Für `a = 3; b = a + 1; a = 8` Endbindungen erklären; Zweig und
Durchläufe eines kurzen Programms vorhersagen; eine Zeichenschleife auch
für die leere Zeichenkette verfolgen; `-3 // 2` begründen.

**Aktivität:** Individuelle Vorhersage, Vergleich zweier Begründungen,
gezielte Übersetzungs- oder Änderungsaufgabe. Für alle in PY2 aufgeführten
Operationen wird ein kleiner diagnostischer Aufgabenpool benötigt; das einzelne
Divisionsbeispiel deckt dieses Ziel nicht vollständig ab.

**Evidenz und Anpassung:** Getrennte Zustands- und Ausgabeprotokolle.
Bei Lücken kurze passende Sicherung, nicht automatisch ein vollständiger
Grundlagenblock. Snap!-Reporter und eigene Blöcke nur als Anschluss nutzen,
wenn die tatsächliche Erfahrung erhoben wurde.

## A1 — Auswerten und Einsetzen erklären

**Ziele:** EX1–EX3, FU1, FU2, FU4; Einführung von FU6.

**Voraussetzungen:** Ausdrücke und Namensbindungen aus A0; nötige
Rechenoperationen sind gesichert.

**Modellarbeit:** M1 und der bewusst begrenzte reine Teilbereich M2.
Reduktionspfeil, mathematische Definition, Python-Definition und Aufruf trennen.

**Diagnose:** Den nächsten Schritt in `3 * (2 + 4)` angeben.
Für `f(x) = x² + 1` den verschachtelten Aufruf `f(1 + f(2))` auswerten.
Einen Aufruf mit unbekanntem Namen begründet als fehlerhaft einordnen.

**Aktivität:** Kurzer Modellimpuls, individuelle Reduktionsspur,
Begründungsvergleich und Übertragung einer reinen Funktion nach Python.
Erst anschließend Ausführung zur Prüfung.

**Evidenz und Anpassung:** Argumente werden vor dem äußeren Rumpf ausgewertet;
umgebende Rechnungen bleiben erhalten. Bei Verwechslungen zunächst einfache
Einzelaufrufe nutzen. Der reine Teilbereich muss ausdrücklich benannt werden,
damit die folgende Erweiterung nicht wie ein Widerspruch erscheint.

## A2 — Python-Aufrufe, lokale Bindungen und Rückkehr

**Ziele:** FU1, FU3–FU8, EX3; Anwendung von PY1 und PY2.

**Voraussetzungen:** A1; Verzweigungen und Zuweisungen aus A0.

**Modellarbeit:** M3 ergänzt M2 um getrennte Aufrufrahmen, Anweisungen,
Fortsetzungen und Ausgabe. Reine Beispiele müssen in beiden Ansichten
dasselbe Resultat haben.

**Diagnose:** Eine ausgebende Funktion ohne explizite Rückgabe in `f(3) + 1`
verfolgen; zwei Aufrufe mit demselben Parameternamen vergleichen;
eine Anweisung nach `return` beurteilen.

**Aktivität:** Minimale Kontrastpaare: `print`/`return`,
ein/ein weiterer Parameter, gültiger/fehlerhafter Aufruf. Einen Ablauf
von Hand protokollieren und anschließend mit der verfügbaren Visualisierung
vergleichen. Ein Mehrparameterbeispiel mit beobachtbaren Argumentwirkungen
prüft die Links-nach-rechts-Reihenfolge.

**Evidenz und Anpassung:** Ausgabe `3`, Rückgabewert `None` und anschließenden
`TypeError` getrennt erklären. Zusätzlich unbekannten Namen und falsche
Argumentanzahl unterscheiden. Bei Fehlern wird die betreffende Regel geklärt,
nicht nur das Programm repariert.

**Übergangskriterium:** Lernende können lokale Bindungen und die wartende
Rechnung darstellen und `return` erklären, ohne es als Ausgabe zu beschreiben.

## A3 — Das Design-Rezept an vollständigen Zwischenständen

**Ziele:** DR1–DR3, FU1–FU8; Anwendung von PY1.

**Voraussetzungen:** A2, besonders Rückgabewerte und `None`.

**Modellarbeit:** Keine neue Ausführungsmaschine. Vertrag, Beispiele,
Implementierung und Tests verwenden das Modell aus A2.

**Diagnose:** Erklären, warum ein Rumpf mit `pass` gültig ist und
`assert volumen(2, 3, 4) == 24` am Platzhalter scheitert. Danach zeigen,
welcher Schritt aus einer gültigen Definition eine erfüllte Lösung macht.

**Aktivität:** Das sechsstufige Rezept aus der
[Didaktik](lecture-didactics.md#design-rezept-und-ausführbare-zwischenstände)
an einem wertliefernden Beispiel bearbeiten. Anschließend eine Funktion mit
mehreren Fällen, etwa dem bisherigen Maximum zweier Zahlen, eigenständig
entwerfen. Die kommentierte Zweckbeschreibung verwendet die Parameternamen.

**Evidenz und Anpassung:** Alle sechs Zwischenstände lassen sich ausführen;
bewusste Testfehler entstehen erst mit Schritt 4 und sind `AssertionError`.
Tests unterscheiden Fälle und Randfälle. Bei Schwierigkeiten Signatur,
Zweck oder Testform teilweise vorgeben, nicht den ganzen Rumpf.

## A4 — Rekursiv entwerfen und rekursive Abläufe erklären

**Ziele:** RE1–RE5, DR2–DR3, FU4–FU8.

**Voraussetzungen:** A2 und A3. Für den vorgeschlagenen Zeichenketteneinstieg
müssen Leerprüfung und Zerlegung in erstes Zeichen und Rest bereitgestellt
und verstanden werden; sie sind bisher kein gesichertes Vorwissen.

**Modellarbeit:** M4 verwendet dieselben Aufrufregeln wie M3. Entwurfsannahme
für das kleinere Problem und konkrete Ausführung werden getrennt bearbeitet.

**Diagnose:** Einen Aufruf auf `"ab"` mit den Aufrufen auf `"b"` und `""`
verfolgen und die ausstehenden Additionen zeigen. Danach eine Definition
ohne Basisfall und eine mit unverändertem Argument beurteilen.

**Aktivität:** Einen strukturell kleiner werdenden String-Auftrag als
Einstieg erproben. Basisfall, Eingabebereich und abnehmende Länge formulieren;
danach Wunschdenken für den Rest und Implementierung nach Design-Rezept.
Erst einen kurzen Aufruf vollständig verfolgen, dann den Entwurf ohne
vollständiges gedankliches Aufrollen begründen.

**Evidenz und Anpassung:** Getrennte lokale Bindungen, Basisfall und Rückweg
werden erklärt; die Lösung besteht begründete Beispiele. Einen
`RecursionError` nicht automatisch als Beweis einer nichtterminierenden
Definition werten.

**Transfer:** Die bisherige Summation verbindet den Einstieg mit bekannten
Zahlenproblemen. Manhattan-Routen können anschließend zwei Teilprobleme
einführen, mit nichtnegativen ganzzahligen Koordinaten, Randfällen auf den
Achsen und einer abnehmenden Größe `x + y`. Kleine Eingaben halten
Ausführungsumfang und Laufzeit überschaubar. Dieser konkrete Kontext ist
ersetzbar; rekursiver Entwurf und Erklärung bleiben Pflicht.

## A5 — Eine Sprache spezifizieren und implementieren

**Ziele:** SP1, SP2; Anwendung von PY1, PY3, PY4 und FU1–FU8.

**Voraussetzungen:** A0–A3. Die benötigten Turtle- und Stapeloperationen
werden mit einer klaren Schnittstelle bereitgestellt.

**Modellarbeit:** M5 trennt Quellwort, Sprachspezifikation, Turtle-Zustand und
Python-Ausführung des Interpreters.

**Diagnose:** Einen kurzen Befehlsstring von Hand verfolgen und die dazugehörige
Stelle im bereitgestellten Interpreter identifizieren. Bei geschachtelten
Klammern vorhersagen, welche Pose als Nächstes wiederhergestellt wird.

**Aktivität:** Von der bisherigen kleinen Sprache mit `F`, `B`, `+`, `-`
zur Zeichensprache mit gespeicherten Posen übergehen. Einen neuen Befehl
zuerst spezifizieren, dann implementieren und anhand eines unterscheidenden
Beispiels prüfen. Die neue Bedeutung darf nicht nur aus zufälligem
beobachtetem Verhalten der Implementierung abgeleitet werden.

**Evidenz und Anpassung:** Quellposition, Pose und Zeichnung werden getrennt
verfolgt; eine Erweiterung stimmt mit ihrer Spezifikation überein.
Ein vorbereitetes Interpretergerüst vermeidet neue, ungesicherte
Datenstrukturthemen.

**Vor Ausarbeitung klären:** Konkrete Befehle und Parameter, Ausgangspose,
ignorierte Zeichen sowie gültige Klammerfolgen beziehungsweise Fehlerregeln.
Gespeicherte Turtle-Posen sind kein Ersatzmodell für Python-Aufrufrahmen.

## A6 — Generationen erzeugen, danach interpretieren

**Ziele:** LS1, SP1, SP2; Anwendung von PY3 und PY4.

**Voraussetzungen:** A5 sowie nachvollziehbare Zeichenkettenverkettung.

**Modellarbeit:** M6 ergänzt einen eigenen Ersetzungszustand. Das
Generationenwort wird erst nach Abschluss durch M5 interpretiert.

**Diagnose:** `A → AB`, `B → A` ausgehend von `A` über drei Übergänge
anwenden. Erwartet: `AB`, `ABA`, `ABAAB`. Jede Ersetzung auf das
alte Wort beziehen, nicht auf gerade erzeugte Zeichen.

**Aktivität:** Zunächst nur Wörter und Regeln; danach passende
Wachstums- und Zeichenbeispiele aus den bisherigen Lindenmayer-Materialien
gegenüberstellen. Vorhersagen des Wortes und der Zeichnung getrennt prüfen.
Die Befehlsimplementierung aus A5 im Gesamtbeispiel wiedererkennen.

**Evidenz und Anpassung:** Für jedes Symbol ist seine Herkunft in der alten
Generation nachvollziehbar. Ein komplexes Bild gilt nicht als Nachweis
korrekter Ersetzung. Bei Schwierigkeiten alte und neue Generation in
getrennten Zeilen oder Tabellen halten.

**Grenze:** Mehrere Generationen von Hand erzeugen und die bereitgestellte
Implementierung nachvollziehen; keinen eigenen Ersetzungsmotor verlangen.

## A7 — Transfer und Modelle reflektieren

**Ziele:** Nachweise für alle Bereiche der [Outline](lecture-outline.md)
zusammenführen; gezielt noch offene Ziele prüfen.

**Voraussetzungen:** Die zu prüfenden Module wurden bearbeitet.

**Aktivität:** Ein unbekanntes kleines Programm ohne Ausführung erklären;
eine wertliefernde Funktion nach Rezept entwerfen; eine rekursive Lösung
begründen; einen Sprachbefehl erweitern; eine neue Ersetzungsfolge verfolgen.
Diese Nachweise können über mehrere Aufgaben verteilt werden. Ein einziges
Großprojekt ist nicht erforderlich.

**Evidenz:** Individuelle Vorhersage, regelbasierte Erklärung, Umsetzung und
gezielter Test. Auch bei Partner- oder Projektarbeit individuelle Erklärungen
erheben. Die [Matrix](paradigmen-matrix-template.md) zeigt verbleibende Lücken.

**Rückkopplung:** Prüfen, ob die kurzen Lernzyklen zu selbstständigem Erklären
und Entwerfen führen oder zu viel Führung benötigen. Die Formatentscheidung
und die nächste Iteration aus diesen Beobachtungen ableiten.

## Umgang mit den bisherigen Materialien

| Material | Vorschlag für die neue Iteration | Begründung |
| --- | --- | --- |
| 1201: Ausdrucksauswertung und mathematische Funktionen | Beibehalten, Geltungsbereich ausweisen, mit einzelnen Vorhersagen verbinden. | Macht M1 und M2 explizit, ohne sie für ganz Python auszugeben. |
| 1203: Design-Rezept, Volumen und Maximum | Rezept beibehalten; Zwischenstände und Testformen präzisieren. | Verbindet Entwurf mit beobachtbarer Ausführbarkeit und Fallunterscheidung. |
| 1205: Domino, Summation, Manhattan-Routen | Domino als begrenzte Entwurfsanalogie; strukturellen Einstieg prüfen; Zahlen- und Routenbeispiele später einsetzen. | Trennt Wunschdenken, Aufrufmechanik und zusätzliche Problemkomplexität. |
| 1207: Spezifikation und kleine Sprache | Beibehalten, aber Zustandsprotokoll und neue Befehle explizit prüfen. | Verknüpft Sprachbeschreibung und Implementierung, statt nur eine Demo zu zeigen. |
| 1209: Lindenmayer-Wachstum | Beibehalten, Ersetzungs- und Zeichenphase deutlich trennen. | Verhindert Vermischung zweier verschiedener Modelle. |

Die Aussagen beziehen sich auf die erkennbaren Präsentationsinhalte.
Arbeitsblätter und nur als Bild sichtbare Codebeispiele müssen vor einer
wörtlichen oder technischen Übernahme gesondert geprüft werden.