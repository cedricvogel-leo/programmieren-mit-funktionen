# Lecture Didactics — Notionale Maschinen und mentale Modelle

## Status und Leitentscheidung

Dieses Dokument plant die Didaktik, nicht die späteren Kursseiten.
Zielgruppe und überprüfbare Ziele stehen in der
[Outline](lecture-outline.md), die Lernfolge in der
[Agenda](lecture-agenda.md). Der [Modellbogen](paradigmen-matrix-template.md)
verbindet erwartete Erklärungen mit tatsächlichen Beobachtungen.

**Leitentscheidung:** Die Lernenden sollen eine explizite Vorstellung davon
entwickeln, wie die betrachteten Programme schrittweise ausgeführt werden.
Erfolgreiches Schreiben allein belegt dieses Verständnis nicht.

Eine **notionale Maschine** ist das bewusst ausgewählte, menschenlesbare
Ausführungsmodell. Ein **mentales Modell** ist die Vorstellung, die eine
Person davon tatsächlich aufgebaut hat. Die Lehrkraft kann ein korrektes
Modell anbieten, ohne dass Lernende es bereits konsistent anwenden.
Deshalb gehören Diagnose, Erklärung und Überarbeitung zum Unterricht.

## Forschungsgrundlage und Reichweite

Zentrale Quelle: Shriram Krishnamurthi und Kathi Fisler (2019),
[*Programming Paradigms and Beyond*](https://cs.brown.edu/people/sk/Publications/Papers/Published/kf-prog-paradigms-and-beyond/),
in *The Cambridge Handbook of Computing Education Research*.
Die verlinkte [PDF-Fassung](https://cs.brown.edu/people/sk/Publications/Papers/Published/kf-prog-paradigms-and-beyond/paper.pdf)
ist laut Autorenseite ein vorveröffentlichter Entwurf; die publizierte
Fassung wurde weiter redigiert. Abschnittsangaben beziehen sich auf den Entwurf.

| Grundlage im Kapitel | Aussage und Evidenzstatus | Konsequenz für diesen Entwurf |
| --- | --- | --- |
| §4: Notional Machines | Die Autoren schlagen menschenlesbare operationale Semantik als Ordnungsprinzip vor. Für eine Sprache können mehrere Modelle sinnvoll sein. | Modellzustand und Regeln explizit benennen, nicht bloß Funktionen als Syntax einführen. |
| §4: Lernen von Modellen | Das Kapitel berichtet Studien zugunsten aktiver Auseinandersetzung und früher expliziter Ablaufverfolgung; passives Betrachten einer Visualisierung genügt nicht als Lernhandlung. | Eigene Vorhersagen und begründete Schritte vor dem Werkzeugvergleich verlangen. |
| §4 und §5.2 | Welche Modelle in welcher Reihenfolge am besten wirken und wie Modelle weiterentwickelt werden, sind ausdrücklich offene Forschungsfragen. | Die unten vorgeschlagene Progression als Unterrichtsentwurf prüfen, nicht als bewiesene optimale Sequenz darstellen. |
| §4.1: Mutation and State | Zustandsänderung, zeitliche Reihenfolge und Aliasing machen scheinbar einfache Modelle komplex. | Bereits bekannte Zuweisung präzise aufgreifen; keine falschen Kopier- oder Kistenmetaphern für ganz Python etablieren. |
| §4.2: Transfer | Mathematischer Transfer braucht passende Verhaltensmodelle; algebraische Variablen und veränderliche Programmbindungen sind nicht gleichzusetzen. | Den mathematischen Einstieg auf einen expliziten reinen Teilbereich beschränken. |
| §5.1–5.3 | Alltagssprache, visuelle Syntax und Sprachwechsel können individuelle Fehlvorstellungen beeinflussen. Blocksyntax erklärt nicht automatisch die Ausführungssemantik. | Snap!-Vorerfahrung aktivieren, aber semantisches Verständnis gesondert diagnostizieren. |
| §6.2: Repetition | Die Autoren kritisieren unergiebige Rekursionsbeispiele und unterscheiden strukturelle von generativer Rekursion; strukturelle Rekursion wird als zugänglicherer Einstieg begründet. | Ein strukturell kleiner werdendes Datenproblem als Einstieg prüfen; Zahlenrätsel und generative Grafik nicht automatisch an den Anfang setzen. |

Die konkrete Python-Teilmenge, die Darstellung der Aufrufe, das Design-Rezept
und die unten vorgeschlagenen Lernzyklen sind **unsere didaktischen
Entscheidungen**. Das Kapitel belegt weder ihre lokale Wirksamkeit in dieser
Klasse noch die Überlegenheit eines bestimmten Unterrichtsformats.
Es ist eine Forschungsübersicht mit Argumenten und offenen Fragen, keine
einzelne Interventionsstudie für diesen Kurs.

## Anschluss an Snap! und die bisherige Einheit

Das [Snap!-Material](https://computingeducation.de/algorithmen-mit-snap/)
verbindet projektbezogene Wahlmöglichkeiten mit gemeinsamer Konzeptabdeckung.
Die Klasse hat außerdem Snap!-Programme nach Python übersetzt.
Wir übernehmen weder eine reine Anfängereinführung noch die Annahme, damit
seien alle Ausführungsfragen geklärt.

| Möglicher Anschluss | Diagnose statt Annahme | Didaktische Reaktion |
| --- | --- | --- |
| Blockformen unterscheiden wertliefernde Ausdrücke und Befehle. | Kann die Person in Python Ausdruck und Anweisung unterscheiden? | Kontrastpaar mit gleichem Zweck, aber unterschiedlicher Syntax bearbeiten. |
| Verzweigungen und Wiederholung sind bekannt. | Wird genau ein Zweig gewählt? Welche Werte durchläuft die Schleifenvariable? | Einen konkreten Ablauf protokollieren, nur nötige Lücken sichern. |
| Variablen wurden verwendet. | Wird eine Zuweisung als Bindungsänderung oder als dauerhafte Gleichung verstanden? | `a = 3; b = a + 1; a = 8` mit getrennten Schritten erklären. |
| Eigene Blöcke könnten bekannt sein. | Wurden sie tatsächlich eingesetzt? Werden Parameter und getrennte Aufrufe verstanden? | Zunächst Erfahrung erheben; lokale Bindungen nicht voraussetzen. |

Die alten Präsentationen enthalten bereits brauchbare Bausteine:
Reduktionspfeile und mathematische Aufrufe (1201), das sechsstufige Rezept
(1203), Wunschdenken (1205), Spezifikation und Interpreter (1207) sowie
Ersetzung und Turtle-Deutung (1209). Diese werden explizit verbunden, nicht
lediglich um neue Begriffe ergänzt.

Ein Teil der Programme liegt in den PDFs nur als Bild vor. Die Arbeitsblätter
und Demoquellen, auf die sie verweisen, liegen nicht vollständig vor. Aussagen
über deren genaue Implementierung bleiben deshalb offen; eine spätere
Übernahme setzt Sichtprüfung beziehungsweise Einsicht in den Code voraus.

## Gemeinsame Darstellungsregeln

- `→` bezeichnet einen erlaubten Auswertungsschritt, `=` eine Zuweisung,
  `==` einen Vergleich. Mathematische Definitionen werden als solche beschriftet.
- Wir trennen **verbleibenden Ausdruck**, **aktuelle Anweisung**, **lokale
  Namensbindungen**, **wartende Aufrufe mit Rückkehrstellen** und **Ausgabe**.
  Nur die jeweils benötigten Teile werden sichtbar gemacht.
- Ein Zustandsübergang braucht eine Regel als Begründung. „Der Computer weiß,
  was gemeint ist“ ist keine Erklärung.
- Reduktionsschritte und Visualisierungsereignisse müssen nicht dieselbe
  Granularität haben. Entscheidend ist, dass beide dieselben Bindungen,
  Reihenfolgen, Ergebnisse und Ausgaben vorhersagen.
- Fehler sind mögliche Ergebnisse eines Schritts. Fehlerursache und schon
  erfolgte Ausgaben werden getrennt festgehalten.

## M1 — Ausdrücke werden zu Werten ausgewertet

**Geltungsbereich:** Zunächst Zahlen, Zeichenketten, bekannte Namen und die
vereinbarten arithmetischen beziehungsweise Vergleichsoperationen.
Zuweisungen und Kontrollfluss werden als Anweisungen daneben behandelt.

**Sichtbarer Zustand:** Noch auszuwertender Ausdruck, bekannte Bindungen und
die markierte nächste Teilrechnung.

**Regeln:** Namen nachschlagen; Teilrechnungen gemäß Python-Reihenfolge und
Präzedenz auswerten; das Ergebnis an derselben Stelle einsetzen; den übrigen
Ausdruck erhalten. Ein unbekannter Name oder eine nicht erlaubte Operation
führt zum entsprechenden Fehler, nicht zu einem geratenen Wert.

**Angestrebtes mentales Modell:** „Ich kann sagen, was als Nächstes berechnet
wird und welcher Teil der Rechnung dadurch unverändert bleibt.“

**Diagnose und Nachweis:** `3 * (2 + 4)` schrittweise reduzieren; die
Zuweisungsfolge aus der Snap!-Diagnose protokollieren. Erwartet werden
`3 * 6 → 18` und am Ende die Bindungen `a: 8`, `b: 4`.

**Fehlvorstellung:** Zuweisung ändere rückwirkend eine andere Bindung oder
Rechnen erfolge unabhängig von der Klammerung immer strikt von links nach rechts.

**Anschluss und Grenze:** Anschluss an bekannte Ausdrücke und mathematisches
Rechnen. Dieses Modell beschreibt noch keinen mehrzeiligen Funktionsablauf.

## M2 — Reine Ausdrucksfunktionen als Einsetzen

**Geltungsbereich:** Bekannte Funktionen mit gewöhnlichen positionellen
Parametern, Zahlen oder Zeichenketten und einem reinen Rückgabeausdruck.
Keine Ausgabe, Mutation, freien veränderlichen Abhängigkeiten oder weiteren
Python-Signaturformen. Beispiel: mathematisch `f(x) = x² + 1`,
in Python `def f(x): return x * x + 1`.

**Sichtbarer Zustand:** Definition, Aufruf, ausgewertete Argumentwerte und
der verbleibende umgebende Ausdruck.

**Regeln:** Aufrufziel bestimmen, Argumente von links nach rechts auswerten,
Werte den Parametern zuordnen, im reinen Ausdrucksmodell einsetzen und weiter
auswerten. Der Rumpf wird nicht schon bei der Definition ausgeführt.

**Angestrebtes mentales Modell:** „Ein Argument kann selbst eine Rechnung
sein. Deren Wert wird eingesetzt, nicht ihr noch unausgewerteter Text.“

**Diagnose und Nachweis:** Für `f(1 + f(2))` die innere Rechnung, den Wert `5`,
das äußere Argument `6` und schließlich das Ergebnis `37` erklären.
Ein unbekannter Funktionsname ist als Fehler zu begründen.

**Fehlvorstellung:** Der äußere Rumpf beginne vor der Auswertung der Argumente;
Definition und Aufruf seien dasselbe.

**Anschluss und Grenze:** M1 bleibt gültig. Das Einsetzen ist eine gezielte
Rechenansicht für den reinen Teilbereich, keine textuelle Implementierung
beliebiger Python-Aufrufe. Sobald lokale Zuweisungen, Ausgabe und mehrere
Anweisungen relevant werden, ergänzen wir M3 ausdrücklich.

## M3 — Aufrufe mit lokalen Bindungen und Rückkehrstelle

**Geltungsbereich:** Einfache benannte Funktionen, positionelle Argumente,
lokale Bindungen, Verzweigungen, Schleifen, `print`, `return`, `pass`.
Globale Mutation, Closures und Aliasing veränderbarer Container bleiben außen vor.

**Sichtbarer Zustand:** Aktuelle Anweisung; pro aktivem Aufruf ein eigener
Rahmen mit lokalen Bindungen; wartende Fortsetzungen; Ausgabeprotokoll.
Definitionen sind getrennt verfügbar. Ein Rahmen ist eine Erklärungshilfe,
keine Behauptung über die interne Speicherorganisation jeder Python-Laufzeit.

**Regeln:**

1. Eine Funktionsdefinition bindet einen Namen, führt aber den Rumpf nicht aus.
2. Beim Aufruf wird das Aufrufziel bestimmt; die Argumentausdrücke werden von
   links nach rechts ausgewertet. Bei einem Fehler wird der Rumpf nicht betreten.
3. Nach erfolgreicher Argumentbindung beginnt ein neuer Aufruf mit eigenen
   lokalen Bindungen. Falsche Argumentanzahl führt im betrachteten Teilbereich
   zu `TypeError`.
4. Die aufrufende Rechnung wartet an einer bestimmten Stelle. Lokale
   Zuweisungen verändern die Bindungen dieses Aufrufs.
5. `print` schreibt in das Ausgabeprotokoll; sein Rückgabewert ist `None`.
   Ausgabe ersetzt keine Rückgabe eines berechneten Wertes.
6. Bei `return ausdruck` wird zuerst `ausdruck` ausgewertet. Danach endet
   dieser Aufruf und liefert den Wert an die wartende Stelle. Nachfolgende
   Anweisungen dieses Aufrufs werden nicht mehr ausgeführt.
7. Ein erreichtes Funktionsende ohne `return` sowie ein nacktes `return`
   liefern `None`. `pass` tut nichts und setzt die Ausführung danach fort.

**Angestrebtes mentales Modell:** „Jeder Aufruf hat eigene lokale Namen.
Der Aufrufer wartet auf einen Wert; ausgegebener Text ist eine andere Wirkung.“

**Diagnose und Nachweis:** Eine Funktion mit `print(x)` und ohne explizites
`return` im Ausdruck `f(3) + 1` verfolgen: erst Ausgabe `3`, dann `None` als
Funktionswert, anschließend `TypeError`. In einem zweiten Beispiel mit
`return x + 1` wird der zurückgegebene Wert ohne automatische Ausgabe verwendet.

**Weitere Kontraste:** Zwei Aufrufe mit demselben Parameternamen; ein `print`
nach `return`; unbekannter Name gegenüber falscher Argumentanzahl.
An einem gültigen Mehrparameteraufruf lässt sich die Reihenfolge mit zwei
ausgebenden Hilfsfunktionen sichtbar machen. Diese wirken absichtlich und
gehören deshalb zu M3, nicht zum reinen Teilbereich M2.

**Fehlvorstellungen:** Alle gleichnamigen Parameter seien dieselbe Variable;
`print` liefere den angezeigten Wert; `return` zeige automatisch etwas an;
der Aufrufer starte nach der Rückgabe von vorn.

**Anschluss und Grenze:** M2 und M3 müssen für reine Beispiele dasselbe
Ergebnis liefern. Gebunden werden Werte, nicht pauschal Kopien beliebiger
Objekte. Vor Beispielen mit geteilten veränderbaren Objekten müsste das Modell
um Referenzen und Aliasing erweitert werden.

## M4 — Rekursion ist kein neuer Aufrufmechanismus

**Geltungsbereich:** Kleine, nachvollziehbare rekursive Aufrufe mit ausdrücklich
vereinbartem Eingabebereich. Erst ein rekursiver Teilauftrag, später
gegebenenfalls mehrere.

**Sichtbarer Zustand:** Dieselben Rahmen wie in M3, nun mit mehreren
Aktivierungen derselben Definition; noch ausstehende Rechnungen und Rückgaben.

**Regeln:** Ein Selbstaufruf arbeitet genauso wie ein anderer Aufruf. Er erhält
eigene Parameterbindungen. Der aktuelle Aufruf wartet, bis der innere einen
Wert zurückgibt. Erst danach kann die ausstehende Rechnung fertig werden.
Im Basisfall entsteht ein Ergebnis ohne weiteren Selbstaufruf.

**Angestrebtes mentales Modell:** „Die Definition ist einmal vorhanden,
aber mehrere Aufrufe können gleichzeitig noch nicht beendet sein. Ihre
Arbeit wird beim Rückweg fortgesetzt.“

**Diagnose und Nachweis:** Für einen vorgegebenen Vertrag „Zeichen zählen“
den Aufruf auf `"ab"` verfolgen: Rahmen für `"ab"`, `"b"`, `""`;
beim Rückweg Ergebnisse `0`, `1`, `2`. Dabei angeben, wo jeweils noch `1 + …`
wartet. Die nötigen Operationen für Leerprüfung und Restzeichenkette werden
vorher bereitgestellt; Indexierung und Slicing gelten nicht als Vorwissen.

**Wunschdenken als Entwurf:** Getrennt von diesem Ablauf annehmen, dass die
Funktion den strikt kleineren Rest gemäß Vertrag löst. Dann bestimmen, wie
dieses Ergebnis zum Gesamtergebnis ergänzt wird. Diese Annahme braucht
Eingabebereich, Basisfall und eine abnehmende Größe; sie ist keine Behauptung,
Python errate das Resultat.

**Fehlvorstellungen:** Ein Selbstaufruf überschreibe den äußeren Parameter;
der Basisfall beende sofort alle Aufrufe; Wunschdenken ersetze die Begründung,
warum das Problem kleiner wird.

**Grenze:** Ein fehlender Basisfall oder ein Aufruf mit unverändertem Problem
kann im Modell unbegrenzt weiterlaufen. Python meldet typischerweise vorher
`RecursionError`. Auch eine terminierende Definition kann an der endlichen
Rekursionstiefe scheitern; dieser Fehler allein beweist keine Nichtterminierung.

**Beispielentscheidung:** Zeichenketten als leerer Fall oder erstes Zeichen
plus Rest bieten einen zu prüfenden strukturellen Einstieg. Das ist eine
konkrete lokale Ableitung aus §6.2, kein dort getestetes Python-Curriculum.
Die bisherigen Dominos können Wunschdenken illustrieren, ersetzen aber
keinen Aufrufrahmen. Summation kann anschließend den alten Ansatz verbinden.
Manhattan-Routen bleiben als späterer Transfer mit zwei kleineren Problemen
erhalten; die zusätzlichen Anforderungen und Eingabebereiche sind auszuweisen.

## M5 — Eine kleine Sprache interpretieren

**Geltungsbereich:** Eine festgelegte Zeichenbefehls-Sprache mit einer zunächst
bereitgestellten Python-Implementierung. Für jeden Befehl ist die Wirkung
bekannt; unbekannte Zeichen werden nur dann ignoriert, wenn dies spezifiziert ist.

**Sichtbarer Zustand:** Quellwort und Leseposition; Turtle-Position,
Ausrichtung und gezeichnete Linien; bei `[` und `]` zusätzlich ein Stapel
gespeicherter Posen. Daneben bleibt der Python-Aufrufzustand des Interpreters.

**Regeln:** Das nächste Quellzeichen bestimmen und die spezifizierte Wirkung
ausführen; dann die Leseposition weiterstellen. `[` speichert die aktuelle
Pose; `]` entnimmt die zuletzt gespeicherte Pose und stellt sie wieder her,
ohne beim Zurücksetzen eine Verbindungslinie zu zeichnen.

**Angestrebtes mentales Modell:** „Eine Spezifikation legt das Verhalten
fest. Ein Python-Programm kann dieses Verhalten ausführen. Das Quellwort ist
dabei Eingabe und wird nicht selbst zu Python-Code.“

**Diagnose und Nachweis:** Einen kurzen Befehlsstring von Hand verfolgen;
einen neuen Befehl erst mit einer Wirkung und einem unterscheidenden Test
beschreiben, dann in der bereitgestellten Implementierung ergänzen.
Ein Test muss mehr prüfen als nur „das Programm läuft“.

**Fehlvorstellungen:** Bedeutung und Implementierung seien dasselbe;
gespeicherte Posen würden in Speicherreihenfolge statt LIFO entnommen;
Rücksetzen lösche bereits gezeichnete Äste.

**Anschluss und Grenze:** Bekannte Zeichenschleifen und Funktionen tragen den
Interpreter. Befehls- und Aufrufstapel sind trotz ähnlicher LIFO-Ordnung
verschiedene Zustände. Die nötigen Stapeloperationen werden bereitgestellt.
Vor der Umsetzung ist festzulegen, ob ungültige Klammerfolgen ausgeschlossen
oder mit klarer Fehlermeldung behandelt werden. Es gibt kein stilles
„Reparieren“ einer unterspezifizierten Eingabe.

## M6 — L-Systeme ersetzen Wörter, der Interpreter zeichnet sie

**Geltungsbereich:** Ein Axiom, festgelegte kontextfreie deterministische
Ersetzungsregeln und wenige Generationen zur manuellen Bearbeitung.
Für Symbole ohne Regel muss ausdrücklich eine Identitätsregel gelten.

**Sichtbarer Zustand:** Unveränderte alte Generation, Leseposition darin und
neu aufgebautes Wort. Das spätere Zeichnen hat einen eigenen Zustand nach M5.

**Regeln:** Jedes Symbol der alten Generation einmal ersetzen und die
Ergebnisse in Reihenfolge verknüpfen. Neu erzeugte Symbole werden erst in der
nächsten Generation bearbeitet. Die so beschriebene parallele Ersetzung kann
technisch durch eine Schleife über das alte Wort umgesetzt werden.
Erst nach Fertigstellung wird das neue Wort interpretiert.

**Angestrebtes mentales Modell:** „Wachstumsregeln erzeugen ein Wort.
Zeichenbefehle geben diesem Wort anschließend eine grafische Bedeutung.“

**Diagnose und Nachweis:** Für `A → AB`, `B → A` ab `A` die Generationen
`AB`, `ABA`, `ABAAB` angeben und jeweils auf die Quellgeneration verweisen.
Für diese Ersetzungsdiagnose ist keine Turtle-Bedeutung nötig.

**Fehlvorstellungen:** Ein neu erzeugtes `A` werde sofort nochmals ersetzt;
Ersetzen zeichne bereits Linien; Rekursion im Python-Aufrufmodell und
Generationenwachstum seien derselbe Ausführungsvorgang.

**Anschluss und Grenze:** Zeichenketten, Verkettung und getrennte Zustände
werden wiederverwendet. Manuelle Generationen sind Pflicht, ein eigener
Ersetzungsmotor nicht. Die bereitgestellte Gesamtimplementierung darf gelesen
werden; erweitert werden soll die vereinbarte Befehlsinterpretation.

## Design-Rezept und ausführbare Zwischenstände

Das bisherige Rezept bleibt der Ausgangspunkt:

| Schritt | Arbeitsprodukt | Erwartung an den Zwischenstand |
| --- | --- | --- |
| 1. Namen wählen | Benannte Definition, zunächst ohne Parameter und mit `pass`. | Die Datei ist syntaktisch gültig; noch keine Ergebnisprüfung. |
| 2. Parameter bestimmen | Signatur mit benannten Eingaben und vereinbartem Eingabebereich. | Definition bleibt ausführbar; spätere Aufrufe müssen zur Signatur passen. |
| 3. Zweck beschreiben | Kommentar mit Parametern, Ergebnis und gegebenenfalls Wirkungen. | `pass` bleibt als Platzhalter erhalten. |
| 4. Beispiele formulieren | Mindestens drei konkrete Fälle aus dem bisherigen Rezept, als direkte `assert`-Vergleiche mit erwarteten Werten. | Der Platzhalter liefert `None`; unerfüllte Tests dürfen nun `AssertionError` auslösen. |
| 5. Rumpf implementieren | Lösung nach Vertrag; bei Rekursion Basisfall, kleinerer Teilauftrag und Kombination. | Weiterhin gültiges Python; noch scheiternde Tests werden bearbeitet. |
| 6. Prüfen und überarbeiten | Tests ausführen, Abweichungen erklären, weitere Fälle ergänzen. | Die fertige Lösung besteht die vereinbarten Tests und wird erklärt. |

„Ausführbar“ meint bis zur fertigen Lösung nicht „inhaltlich fertig“.
Zwischenstände dürfen keine absichtlichen Syntax-, Namens- oder Typfehler
enthalten. Die Lehrkraft stellt dafür passende Testformen bereit:
`assert volumen(2, 3, 4) == 24` scheitert am Platzhalter durch `AssertionError`;
`assert volumen(2, 3, 4) + 1 == 25` erzeugt dort dagegen einen unerwünschten
`TypeError`. Tests nach dem ersten Fehler werden zunächst nicht erreicht.
Geprüft wird in einer Umgebung ohne deaktivierte Assertions.

Die Mindestzahl von Beispielen ist kein Korrektheitsbeweis. Die Auswahl soll
relevante Fälle abdecken: verschiedene Zweige, Basisfall, ein- und mehrfache
Verkleinerung, zulässige Randfälle. Beispiele dürfen nicht einfach aus der
Implementierung abgeschrieben werden. Ein Vertrag, der selbst `None` liefert,
braucht andere Beobachtungen; für den Rezept-Einstieg verwenden wir bewusst
wertliefernde Funktionen.

Bei Rekursion ergänzen wir die Entwurfsfragen innerhalb des Rezepts:
Welche Eingaben sind direkt lösbar? Was wird kleiner? Was darf ich für den
kleineren Fall annehmen? Wie baue ich dessen Ergebnis ein?
Dies sind Entwurfsfragen, keine neuen Ausführungsregeln.

## Unterrichtsformat: kurze Lernzyklen als vorläufiger Vorschlag

Ein Zyklus verbindet:

1. **Vorhersagen:** Ergebnis, Ausgabe oder nächsten Zustand einzeln festhalten.
2. **Verfolgen:** Einen kleinen Ablauf von Hand nach Modellregeln protokollieren.
3. **Erklären:** Mit einer Partnerperson Unterschiede an einer Regel klären.
4. **Prüfen:** Ausführen oder visualisieren, Abweichungen untersuchen und die
   ursprüngliche Erklärung sichtbar überarbeiten.
5. **Verändern oder entwerfen:** Einen gezielten Kontrast beziehungsweise eine
   eigene kleine Lösung nach Design-Rezept erstellen.

Das ist kein starres Ritual für jede Aufgabe. Ein knapper Lehrkraftimpuls kann
ein Modell einführen oder eine gemeinsame Fehlvorstellung klären. Mit
wachsenden Fähigkeiten werden Hilfen reduziert und längere Arbeitsphasen
möglich. Aufgabenwahl und eigene Kontexte können an die Snap!-Erfahrung
anschließen; gemeinsame Modell- und Lernzielnachweise bleiben verbindlich.

| Format | Mögliche Stärke | Risiko und Umgang |
| --- | --- | --- |
| Bisher: Präsentation, danach Übungen | Gemeinsame Einführung, zusammenhängende Erklärung. | Individuelle Modelle bleiben während der Präsentation unsichtbar; Vorhersagen und Zwischenfragen einbauen. |
| Vorschlag: kurze Lernzyklen | Frühe diagnostische Evidenz, direkter Vergleich von Annahme und Ausführung. | Zu kleinschrittige Steuerung kann Eigenständigkeit bremsen; Hilfen abbauen und selbstständigen Transfer vorsehen. |
| Projektphasen mit Modell-Checkpoints | Eigene Kontexte und Motivation, Anschluss an Snap!. | Ein funktionierendes Produkt kann Verständnislücken verdecken; individuelle Erklärungen verlangen. |

Die Auswahl bleibt vorläufig. Nach einer Erprobung vergleichen wir nicht nur
Produkte, sondern individuelle Erklärungen, Transfer ohne Werkzeug und
selbstständige Anwendung des Rezepts. Daraus wird über Beibehalten,
Kombinieren oder Ändern entschieden.

## Rolle von LiaScript und GLPython

LiaScript soll später Vorhersagen, Erklärungen, Code und Rückmeldung verbinden.
Das [GLPython-Makro](https://github.com/cedricvogel-leo/glpython-liascript)
stellt Ausführung, Visualisierung und Turtle-Einbettung bereit.
Es ist ein Prüfwerkzeug, nicht die Definition der notionalen Maschine.

- Vor einem Lauf steht ein überprüfbarer eigener Gedanke; wahlloses
  Wiederholen der Ausführung ersetzt keine Erklärung.
- Für Aufrufrahmen werden nur tatsächlich verfügbare Visualisierungsansichten
  versprochen. Ob lokale Bindungen, Rückkehrstellen und Zwischenausdrücke
  geeignet sichtbar sind, muss bei der späteren Inhaltserstellung geprüft
  werden; andernfalls ergänzen wir eine konsistente manuelle Darstellung.
- Die Makro-Laufzeiten der Blöcke sind isoliert. Spätere Beispiele müssen ihre
  benötigten Definitionen selbst enthalten.
- Einrückung und Syntaxhilfen unterstützen die Arbeit, übernehmen aber nicht
  die Modellbildung. Für Diagnosen werden auch werkzeugfreie Aufgaben benötigt.

## Formative Diagnose, Differenzierung und Überarbeitung

Für jedes Modell sammeln wir eine Vorhersage, eine regelbasierte Erklärung
und eine kleine Transferleistung. Ein richtiges Resultat ohne passende
Begründung reicht nicht; eine falsche Vorhersage mit sichtbarer Korrektur ist
ein wertvoller Lernnachweis.

Hilfen: teilausgefüllte Zustandstabellen, markierte Fortsetzungen, bereitgestellte
String- und Turtle-Operationen. Vertiefung: eigene Gegenbeispiele, zusätzliche
Verzweigungen oder ein weiterer Sprachbefehl. Die Kernziele gelten für alle.

In der [Modellmatrix](paradigmen-matrix-template.md) werden typische
Fehlvorstellungen und Veränderungen im Erklären dokumentiert. Nach dem Einsatz
prüfen wir besonders:

- Bleibt die Trennung von Ausgabe und Rückgabe auch in neuen Kontexten erhalten?
- Werden rekursive Rückwege ohne vollständige Werkzeugspur erklärt?
- Wird ein neuer Interpreterbefehl aus seiner Spezifikation heraus geprüft?
- Werden Ersetzung und Interpretation auch bei neuen Regeln getrennt?

Offen bleiben Unterrichtsumfang, Prüfungsrahmen, genaue Projekterfahrungen,
die endgültige Rekursionsaufgabe und der Umgang mit ungültigen Befehlswörtern.
Diese Entscheidungen sind vor der entsprechenden Kursausarbeitung zu treffen.