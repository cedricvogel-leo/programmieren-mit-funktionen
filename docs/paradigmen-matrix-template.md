# Modellmatrix — Notionale Maschinen und Lernnachweise

## Zweck und Verwendung

Der Dateiname bleibt passend zur übernommenen Repository-Struktur erhalten.
Inhaltlich ist dies **keine Paradigmen-Rangliste**, sondern ein Planungs- und
Beobachtungsbogen für die Entwicklung von mentalen Modellen.

Die [Didaktik](lecture-didactics.md) definiert die Modelle und ihre Regeln,
die [Outline](lecture-outline.md) die Lernziele und die
[Agenda](lecture-agenda.md) die Lerngelegenheiten.
Hier werden sie knapp verbunden, ohne die vollständigen Beschreibungen zu
duplizieren. Leere Beobachtungsfelder werden erst beim Einsatz ausgefüllt.

## Planungsübersicht

| Modell und Modul | Ziele | Sichtbarer Zustand und zentrale Regel | Brücke zum bisherigen Modell | Diagnose / erwartete Evidenz | Fehlvorstellung und Grenze |
| --- | --- | --- | --- | --- | --- |
| M1 / A0–A1: Ausdrücke | PY1–PY4, EX1–EX3 | Ausdruck, Bindungen, nächster Schritt; Teilrechnung auswerten und Kontext erhalten. | Bekannte Snap!- und Python-Abläufe diagnostisch aufgreifen. | `3 * (2 + 4) → 3 * 6 → 18`; nach `a = 3; b = a + 1; a = 8` bleibt `b` gleich `4`. | Zuweisung als dauerhafte Gleichung; noch keine Erklärung mehrzeiliger Aufrufe. |
| M2 / A1: Reines Einsetzen | FU1, FU2, FU4, FU6 | Definition, Argumentwerte, Restrechnung; Argumente auswerten, dann Werte einsetzen. | M1 auf reine mathematisch anschlussfähige Funktionen ausdehnen. | Für `f(x) = x² + 1` bei `f(1 + f(2))` inneren Wert `5`, äußeres Argument `6`, Ergebnis `37` begründen. | Äußerer Rumpf starte sofort; keine allgemeine Textsubstitution für Python. |
| M3 / A2–A3: Python-Aufrufe | FU1–FU8, DR1–DR3 | Lokale Rahmen, aktuelle Anweisung, wartende Rechnung, Ausgabe; Wert zurückgeben und genau dort fortsetzen. | M2 liefert für reine Fälle dasselbe Resultat; Anweisungen und Wirkungen kommen hinzu. | Ausgabe `3`, Wert `None`, dann Fehler bei `f(3) + 1`, wenn `f` nur `print(x)` ausführt. | Ausgabe sei Rückgabe; Grenzen bei Closures, globaler Mutation und Aliasing. |
| M4 / A4: Rekursive Aufrufe und Entwurf | RE1–RE5, DR2–DR3, FU4–FU8 | Dieselben Aufrufrahmen; Basisfall liefert Wert, wartende Arbeit wird auf dem Rückweg fortgesetzt. | Keine neuen Aufrufregeln; Wunschdenken ist eine zusätzliche Entwurfsstrategie. | Für Zeichenzählen auf `"ab"` getrennte Aufrufe mit Rückgaben `0`, `1`, `2` und abnehmender Länge erklären. | Basisfall beende alle Aufrufe; endliche Python-Rekursionstiefe nicht mit semantischer Nichtterminierung verwechseln. |
| M5 / A5: Befehlsinterpretation | SP1, SP2, PY1, PY3, PY4 | Quellposition, Pose, Zeichnung, gespeicherte Posen; nächsten Befehl nach Spezifikation ausführen. | Bekannte Funktionen und Zeichenschleifen tragen einen Interpreter. | Handspur und Implementierungsstelle zuordnen; neuen Befehl spezifizieren und mit gezieltem Test ergänzen. | Sprachwort sei Python-Code; Posenstapel und Aufrufstapel sind nicht dasselbe. |
| M6 / A6: L-System-Ersetzung | LS1, SP1, SP2 | Alte und neue Generation getrennt; jedes alte Symbol einmal ersetzen, erst danach interpretieren. | Zeichenverkettung aus M1; fertiges Wort wird Eingabe von M5. | Für `A → AB`, `B → A`: `A → AB → ABA → ABAAB`, Herkunft aus der alten Generation erklären. | Neues Symbol werde sofort weiter ersetzt; Ersetzung und Zeichnen sind verschiedene Vorgänge. |

Die Tabelle ist ein Wegweiser, keine vollständige Testabdeckung. Vor allem die
Operatoren aus PY2, die einzelnen Rezeptschritte und unterschiedliche
Fehlerursachen brauchen mehrere Aufgaben gemäß Agenda.

## Wiederverwendbare Planungsvorlage

Für eine neue oder überarbeitete Aufgabe eine Zeile anlegen. Eine bloße
Themenüberschrift oder ein Werkzeugname ist noch kein Ausführungsmodell.

| Aufgabe / Modell / Ziel-IDs | Geltungsbereich und Voraussetzungen | Sichtbarer Zustand | Übergangsregel | Anschluss und Erweiterungsgrenze | Erwartete Fehlvorstellung | Diagnose und Aktivität | Erwarteter Nachweis |
| --- | --- | --- | --- | --- | --- | --- | --- |
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |

## Beobachtungsbogen für die Erprobung

Die Felder enthalten noch keine Behauptungen über diese Klasse.
Eine richtige Ausgabe und eine richtige Erklärung werden getrennt beurteilt.
Für die Kursüberarbeitung sind zusammengefasste Beobachtungen ausreichend;
personenbezogene Angaben gehören nicht in das öffentliche Repository.

| Aufgabe / Modell | Ursprüngliche Vorhersage | Begründung / angewandte Regel | Beobachtete Abweichung | Überarbeitete Erklärung | Selbstständiger Transfer | Nächste didaktische Anpassung |
| --- | --- | --- | --- | --- | --- | --- |
| | | | | | | |
| | | | | | | |
| | | | | | | |

## Leitfragen zur Auswertung

- War die angebotene Modellregel unklar oder wurde sie anders verstanden?
- Ist das richtige Ergebnis mit einer unzutreffenden Erklärung entstanden?
- Bleibt die Erklärung ohne Visualisierung und in einem neuen Beispiel tragfähig?
- War der Fehler semantisch, syntaktisch oder durch fehlendes Vorwissen bedingt?
- Hat die Person nach der Rückmeldung ihr Modell erkennbar überarbeitet?
- Braucht die nächste Aufgabe mehr Unterstützung oder mehr eigenständigen Transfer?
- Welche Beobachtung spricht für eine Anpassung des vorläufigen Unterrichtsformats?

## Änderungsprotokoll

| Ausgangsbeobachtung | Geänderte Modellbeschreibung oder Aufgabe | Begründung | Später zu prüfender Nachweis |
| --- | --- | --- | --- |
| | | | |
| | | | |