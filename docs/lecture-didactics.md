# Lecture Didactics — Notionale Maschinen und mentale Modelle

## Status und Leitentscheidung

Dieses Dokument plant die Didaktik, nicht die späteren Kursseiten.
Zielgruppe und überprüfbare Ziele stehen in der
[Outline](lecture-outline.md), die Lernfolge in der
[Agenda](lecture-agenda.md). Der [Modellbogen](paradigmen-matrix-template.md)
verbindet erwartete Erklärungen mit tatsächlichen Beobachtungen.

**Leitentscheidung:** Die Schüler:innen sollen eine explizite Vorstellung davon
entwickeln, wie die betrachteten Programme schrittweise ausgeführt werden.
Erfolgreiches Schreiben allein belegt dieses Verständnis nicht.

Eine **notionale Maschine** ist das bewusst ausgewählte, menschenlesbare
Ausführungsmodell. Ein **mentales Modell** ist die Vorstellung, die eine
Person davon tatsächlich aufgebaut hat. Die Lehrkraft kann ein korrektes
Modell anbieten, ohne dass Schüler:innen es bereits konsistent anwenden.
Deshalb gehören Diagnose, Erklärung und Überarbeitung zum Unterricht.

**Begriffsentscheidung:** «Ausgewerteter Ausdruck» und «Wert» bezeichnen
in unserem Unterrichtsmodell denselben Fall und werden synonym verwendet.
Ein «unausgewerteter Ausdruck» muss dagegen noch ausgewertet werden.
Ein solcher Ausdruck kann bereits ausgewertete Teilausdrücke enthalten:
In `2 * (3 + 4)` sind `2`, `3` und `4` Werte, der gesamte Ausdruck ist
noch unausgewertet. Wir sprechen von Ausdrücken und Teilausdrücken,
nicht von Rechnungen.

Wir führen die gedachte Maschine in **zwei aufeinander aufbauenden Versionen**
ein. Zuerst erklärt eine Einsetzmaschine reine Ausdrucksfunktionen. Danach
erweitern wir sie um das Ausführen von Anweisungen und eigene lokale Speicher
der am Aufrufort eingeblendeten Funktionsrümpfe. Die Schüler:innen sollen angeben können, welche
Komponenten den aktuellen Zustand bilden und welche Regel ihn als Nächstes
verändert. Ziel sind Vorhersagen über Werte, Speicheränderungen, Ausgaben und
Fehler, nicht das Nachzeichnen physischer Hardware.

## Forschungsgrundlage und Reichweite

Zentrale Quelle: Shriram Krishnamurthi und Kathi Fisler (2019),
[*Programming Paradigms and Beyond*](https://cs.brown.edu/people/sk/Publications/Papers/Published/kf-prog-paradigms-and-beyond/),
in *The Cambridge Handbook of Computing Education Research*.
Die verlinkte [PDF-Fassung](https://cs.brown.edu/people/sk/Publications/Papers/Published/kf-prog-paradigms-and-beyond/paper.pdf)
ist laut Autorenseite ein vorveröffentlichter Entwurf; die publizierte
Fassung wurde weiter redigiert. Abschnittsangaben beziehen sich auf den Entwurf.

| Grundlage im Kapitel | Aussage und Evidenzstatus | Konsequenz für diesen Entwurf |
| --- | --- | --- |
| §4: Notional Machines | Die Autoren schlagen menschenlesbare operationale Semantik als Ordnungsprinzip vor. Für eine Sprache können mehrere Modelle sinnvoll sein. | Modellzustand und Regeln explizit benennen, nicht bloss Funktionen als Syntax einführen. |
| §4: Lernen von Modellen | Das Kapitel berichtet Studien zugunsten aktiver Auseinandersetzung und früher expliziter Ablaufverfolgung; passives Betrachten einer Visualisierung genügt nicht als Lernhandlung. | Eigene Vorhersagen und begründete Schritte vor dem Werkzeugvergleich verlangen. |
| §4 und §5.2 | Welche Modelle in welcher Reihenfolge am besten wirken und wie Modelle weiterentwickelt werden, sind ausdrücklich offene Forschungsfragen. | Die unten vorgeschlagene Progression als Unterrichtsentwurf prüfen, nicht als bewiesene optimale Sequenz darstellen. |
| §4.1: Mutation and State | Zustandsänderung, zeitliche Reihenfolge und Aliasing machen scheinbar einfache Modelle komplex. | Das bekannte Box-Modell für den vereinbarten Teilbereich beibehalten und seine Grenze bei gemeinsam verwendeten veränderbaren Objekten ausdrücklich festhalten. |
| §4.2: Transfer | Mathematischer Transfer braucht passende Verhaltensmodelle; algebraische Variablen und Variablen mit durch Zuweisung veränderbaren Werten sind nicht gleichzusetzen. | Den mathematischen Einstieg auf einen expliziten reinen Teilbereich beschränken. |
| §5.1–5.3 | Alltagssprache, visuelle Syntax und Sprachwechsel können individuelle Fehlvorstellungen beeinflussen. Blocksyntax erklärt nicht automatisch die Ausführungssemantik. | Snap!-Vorerfahrung aktivieren, aber semantisches Verständnis gesondert diagnostizieren. |
| §6.2: Repetition | Die Autoren kritisieren unergiebige Rekursionsbeispiele und unterscheiden strukturelle von generativer Rekursion; strukturelle Rekursion wird als zugänglicherer Einstieg begründet. | Ein strukturell kleiner werdendes Datenproblem als Einstieg prüfen; Zahlenrätsel und generative Grafik nicht automatisch an den Anfang setzen. |

Die konkrete Python-Teilmenge, die Darstellung der Aufrufe, das Design-Rezept
und die unten vorgeschlagenen Lernzyklen sind **unsere didaktischen
Entscheidungen**. Das Kapitel belegt weder ihre lokale Wirksamkeit in dieser
Klasse noch die Überlegenheit eines bestimmten Unterrichtsformats.
Es ist eine Forschungsübersicht mit Argumenten und offenen Fragen, keine
einzelne Interventionsstudie für diesen Kurs.

Explizit sind die Auswertungs- und Ausführungsregeln, nicht die ständige
Ankündigung ihres didaktischen Zwecks. Die Schüler:innen bilden ihr Modell
durch Vorhersagen, Auswertungsprotokolle und begründete Vergleiche.
Kurze lokale Arbeitsaufträge ersetzen allgemeine Vorgehenspräambeln.
Die Quelle belegt weder die Überlegenheit knapper Formulierungen noch
die der hier gewählten Darstellung an Ort und Stelle.

## Festlegung: Werte werden in Variablen gespeichert

Die Schüler:innen kennen Variablen bereits als benannte Boxen, in denen Werte
gespeichert werden. **Dieses Box-Modell behalten wir für die Einheit bei.**
Wir sprechen von «Variablen», «gespeicherten Werten», «Werte lesen» und
«Werte speichern», nicht von «Bindungen». Eine neue Referenzterminologie ist
für die vorgesehenen Lernziele nicht erforderlich.

Für die Unterrichtsdarstellung gelten folgende Regeln:

- Eine Zuweisung wertet zuerst den rechten Ausdruck aus und speichert
  anschliessend das Ergebnis in der links genannten Variable. Ein bisher
  gespeicherter Wert wird ersetzt.
- Die Verwendung einer Variable in einem Ausdruck liest ihren aktuell
  gespeicherten Wert.
- Bei `b = a + 1` wird der Wert des Ausdrucks `a + 1` in `b` gespeichert,
  nicht der unausgewertete Ausdruck. Eine spätere Zuweisung an `a`
  verändert den in `b` gespeicherten Wert nicht.
- Bei `b = a` enthält `b` im Modell danach denselben Wert wie `a`.
  Daraus folgt keine dauerhafte Verbindung zwischen diesen Variablen.
- In der zweiten Maschinenversion hat jeder Funktionsaufruf eigene lokale
  Variablen. Die ausgewerteten Argumentwerte werden in den zugehörigen
  Parametervariablen gespeichert. Auch rekursive Aufrufe erhalten jeweils
  eigene Boxen. Die erste Version erklärt reine Aufrufe stattdessen durch
  Einsetzen und benötigt noch keine sichtbaren lokalen Speicher.

**Geltungsbereich:** Das Modell wird für Zahlen, Wahrheitswerte, Zeichenketten
und den Rückgabewert `None` verwendet. Bei diesen Beispielen liefert es die
benötigten Vorhersagen zu Ausdrücken, Zuweisungen, Aufrufen und Rekursion.
Auch die Verkettung von Zeichenketten berechnet einen neuen Wert; sie verändert
nicht eine gemeinsam verwendete Zeichenkette.

**Grenze für die Lehrkraft:** Dies ist eine bewusste didaktische
Vereinfachung, keine Beschreibung der allgemeinen Python-Objektsemantik oder
der physischen Speicherung. Python-Namen können dasselbe Objekt bezeichnen.
Wird ein gemeinsam verwendetes veränderbares Objekt, etwa eine Liste,
verändert, erklärt ein Modell voneinander unabhängiger Werteboxen das
Verhalten nicht mehr. Eine Zuweisung kopiert in Python nicht allgemein ein
Objekt. Solche Mutation, Objektidentität und Aliasing sind kein Lerngegenstand
dieser Einheit. Vor ihrer Einführung muss das Modell erweitert werden.

Der bereitgestellte Turtle-Interpreter darf intern veränderbaren Zustand und
einen Posenstapel verwenden. Diese Schnittstelle wird über ihre festgelegten
Operationen erklärt, nicht als Beleg für unabhängige Kopien beliebiger Objekte.
Aufgaben zur Interpreter-Erweiterung verlangen keine Vorhersagen zu geteilten
veränderbaren Objekten. Falls sie solche Vorhersagen benötigen, muss zuerst
der Modellumfang angepasst werden.

Das Beibehalten des Box-Modells ist unsere lokale didaktische Entscheidung
zum Anschluss an das Vorwissen. Es ist keine Empfehlung dieses konkreten
Modells durch Krishnamurthi und Fisler. Die bewusste Begrenzung folgt der
oben eingeordneten Forderung, Modellgrenzen nicht zu verschleiern.

## Anschluss an Snap! und die bisherige Einheit

Das [Snap!-Material](https://computingeducation.de/algorithmen-mit-snap/)
verbindet projektbezogene Wahlmöglichkeiten mit gemeinsamer Konzeptabdeckung.
Die Klasse hat ausserdem Snap!-Programme nach Python übersetzt.
Wir übernehmen weder eine reine Anfängereinführung noch die Annahme, damit
seien alle Ausführungsfragen geklärt.

| Möglicher Anschluss | Diagnose statt Annahme | Didaktische Reaktion |
| --- | --- | --- |
| Blockformen unterscheiden wertliefernde Ausdrücke und Befehle. | Kann die Person in Python Ausdruck und Anweisung unterscheiden? | Kontrastpaar mit gleichem Zweck, aber unterschiedlicher Syntax bearbeiten. |
| Verzweigungen und Wiederholung sind bekannt. | Wird genau ein Zweig gewählt? Welche Werte durchläuft die Schleifenvariable? | Einen konkreten Ablauf protokollieren, nur nötige Lücken sichern. |
| Variablen sind als Werteboxen bekannt. | Wird bei einer Zuweisung ein berechneter Wert oder vermeintlich eine dauerhafte Gleichung gespeichert? | `a = 3; b = a + 1; a = 8` mit getrennten Speicherständen erklären. |
| Eigene Blöcke könnten bekannt sein. | Wurden sie tatsächlich eingesetzt? Werden Parameter und getrennte Aufrufe verstanden? | Zunächst Erfahrung erheben; eigene lokale Variablen pro Aufruf nicht voraussetzen. |

Die alten Präsentationen enthalten bereits brauchbare Bausteine:
Reduktionspfeile und mathematische Aufrufe (1201), das sechsstufige Rezept
(1203), Wunschdenken (1205), Spezifikation und Interpreter (1207) sowie
Ersetzung und Turtle-Deutung (1209). Diese werden explizit verbunden, nicht
lediglich um neue Begriffe ergänzt.

Ein Teil der Programme liegt in den PDFs nur als Bild vor. Die Arbeitsblätter
und Demoquellen, auf die sie verweisen, liegen nicht vollständig vor. Aussagen
über deren genaue Implementierung bleiben deshalb offen; eine spätere
Übernahme setzt Sichtprüfung beziehungsweise Einsicht in den Code voraus.

## Zwei Versionen derselben gedachten Maschine

### Motivation und Zuordnung

Die erste Version knüpft an das Auswerten mathematischer Ausdrücke an.
Funktionsaufrufe werden durch geklammerte Ausdrücke ersetzt. So können die
Schüler:innen Argumentauswertung, Parameterersetzung und das Erhalten des
umgebenden Ausdrucks untersuchen, ohne gleichzeitig einen Aufrufstapel
verwalten zu müssen.

Diese Vereinfachung hat eine sichtbare Grenze: Ein Rumpf mit mehreren
Anweisungen, lokalen Zuweisungen oder Ausgaben lässt sich nicht einfach als
ein Rückgabeausdruck einsetzen. Das motiviert die zweite Version. Sie erklärt,
wie der Rückgabewert durch das Ausführen eines Funktionsrumpfs entsteht.
Für den reinen Teilbereich müssen beide Versionen dieselben Werte vorhersagen.
Die erste Version wird nicht als falsch verworfen, sondern als begrenzte
Ansicht eingeordnet.

Die Abschnitte M1–M6 bezeichnen dabei **Modellbereiche**, nicht sechs
unabhängige Python-Maschinen:

| Maschinenversion | Zugeordnete Bereiche | Erweiterung |
| --- | --- | --- |
| Version 1: Ausdrucks- und Einsetzmaschine | M1 und M2 | Ausdrücke reduzieren und reine Funktionsaufrufe aufklappen. |
| Version 2: Anweisungs- und Aufrufmaschine | M3; darauf aufbauend M4 | Funktionsrümpfe am Aufrufort einblenden, Anweisungen mit eigenen lokalen Speichern ausführen; dieselben Regeln für Rekursion verwenden. |

M5 und M6 ergänzen später den Zustand einer interpretierten Sprache
beziehungsweise einer Wortersetzung. Sie sind keine weiteren grundlegenden
Versionen der Python-Maschine.

Diese Modellfolge ist unsere didaktische Entscheidung. Die Forschungsgrundlage
motiviert explizite Modelle und ihre Grenzen, belegt aber nicht die
Überlegenheit dieser konkreten Zweiteilung.

### Version 1: Komponenten und Zustand

| Komponente | Inhalt |
| --- | --- |
| Dargestelltes Programm und Definitionen | Ausdrücke werden an Ort und Stelle ersetzt; verfügbare reine Funktionsdefinitionen bleiben unverändert. |
| Bekannte Variablenwerte | Werte in den vereinbarten Boxen, die für die betrachtete Ausdrucksauswertung gelesen werden dürfen. |
| Markierung | Der gemäss Auswertungsreihenfolge als Nächstes zu bearbeitende Teilausdruck. |

Die Auswertung findet im dargestellten Programm statt: Unausgewertete
Teilausdrücke werden dort durch Werte ersetzt. Eine separate Arbeitskopie
ist keine Komponente des Unterrichtsmodells. Das bedeutet nicht, dass Python
die Quelldatei auf dem Datenträger verändert.
Die verfügbare Funktionsdefinition bleibt erhalten; nur am Aufrufort wird
ihr Rückgabeausdruck mit eingesetzten Argumentwerten eingeblendet.
Lokale Speicher und Aufrufstapel sind in dieser Version nicht sichtbar;
Parameter werden nach der Regel aus M2 ersetzt.

Ein gewöhnlicher unausgewerteter Teilausdruck wird durch seinen Wert ersetzt. Beim
**Aufklappen eines Funktionsaufrufs** entsteht dagegen zunächst ein neuer
Ausdruck, der anschliessend weiter ausgewertet wird. Diese beiden Schrittarten
werden im Auswertungsprotokoll unterschieden, auch wenn beide mit `→`
notiert werden.

### Version 2: Komponenten und Zustand

| Komponente | Inhalt |
| --- | --- |
| Dargestelltes Programm und Definitionen | Ersetzungen und Aufrufeinblendungen an Ort und Stelle; verfügbare Definitionen bleiben unverändert. |
| Globaler Speicher | Globale Variablen als Boxen mit ihren gespeicherten Werten. |
| Aufrufeinblendungen mit lokalen Speichern | Pro noch nicht beendetem Aufruf ein eigener eingeblendeter Rumpf mit eigenen Parametervariablen und lokalen Variablen. |
| Aktuelle Anweisung | Position im gerade ausgeführten Block und die zu bearbeitende Anweisung. |
| Ausdruckskontext | Umgebender Ausdruck und bereits ausgewertete Teilwerte bleiben am Aufrufort sichtbar; dort wird der Rückgabewert eingesetzt. |
| Kontrollinformation | Die aktuelle Stelle im Block und bei Schleifen der Stand der Wiederholung beziehungsweise der Iteration. |
| Ausgabeprotokoll | Bereits ausgegebene Texte in ihrer Reihenfolge. |
| Ausführungsstatus | Laufend, regulär beendet oder mit Fehler beendet. |

Der lokale Speicher gehört räumlich zur jeweiligen Aufrufeinblendung.
Der erhaltene umgebende Ausdruck zeigt die Rückgabestelle und bereits
berechnete Teilwerte. Ein zusätzlicher «wartender Ausdruck», eine separate
Fortsetzungskarte oder eine Rückkehradresse sind keine Pflichtkomponenten.
Ein optionales Aufrufstapelbild zeigt dieselben Aufrufe, keine zusätzliche
Art der Ausführung. Jeder Aufruf behält seinen eigenen lokalen Speicher;
die räumliche Verschachtelung macht äussere lokale Variablen nicht automatisch
im inneren Aufruf verfügbar.

Bei einer Zeichenschleife gehört beispielsweise dazu, welche Zeichen noch
zu bearbeiten sind. Eine Funktionsrückgabe ist zunächst ein Abschluss des
aktuellen Aufrufs, nicht das reguläre Ende des gesamten Programms.

### Ausdrücke auswerten, Anweisungen ausführen

**Ausdrücke werden ausgewertet.** Ihre erfolgreiche Auswertung liefert einen
Wert, also einen ausgewerteten Ausdruck. Für die vereinbarten
zusammengesetzten Ausdrücke gilt:

1. Die unmittelbaren Teilausdrücke von links nach rechts auswerten.
   Ein bereits ausgewerteter Teilausdruck ist ein Wert und muss nicht erneut
   ausgewertet werden.
2. Sobald die Operanden Werte sind, die Operation ausführen und den
   zusammengesetzten Ausdruck durch seinen Wert ersetzen.
3. Diese Regel auf jeder Verschachtelungsebene anwenden. Im dargestellten
   Programm bleibt der umgebende Ausdruck bei jedem Ersetzen unverändert.

**Unmittelbare Teilausdrücke** sind die direkt zusammengehörenden Bestandteile
einer Operation. Bei `(2 + 3) * (4 + 5)` sind dies die beiden Summenausdrücke.
Die Maschine wertet zuerst den linken aus. Dessen unmittelbare Teilausdrücke
`2` und `3` sind bereits Werte, deshalb kann die Addition ausgeführt werden:

```text
(2 + 3) * (4 + 5)
→ 5 * (4 + 5)
→ 5 * 9
→ 45
```

Klammern und Operatorrangfolge bestimmen die **Struktur** des Ausdrucks.
Links-nach-rechts-Auswertung bedeutet nicht, die Operationszeichen in ihrer
Reihenfolge im Text abzuarbeiten. Bei `2 + 3 * 4` sind die unmittelbaren
Teilausdrücke der Addition `2` und `3 * 4`. Der linke ist bereits ein Wert;
der rechte muss noch ausgewertet werden:

```text
2 + 3 * 4
→ 2 + 12
→ 14
```

Bei Funktionsaufrufen werden nach Bestimmung des Aufrufziels zuerst die
Argumentausdrücke von links nach rechts zu Werten ausgewertet. Dann wird der
Aufruf in Version 1 durch den geklammerten Rückgabeausdruck mit eingesetzten
Argumentwerten ersetzt. Dieser neue Ausdruck wird nach denselben Regeln
weiter ausgewertet. In Version 2 kann die Auswertung des Aufrufs stattdessen
die Ausführung eines Funktionsrumpfs erfordern.

Die Schritte werden bis zu einem einzelnen Wert oder einem Fehler wiederholt.
Eine nichtterminierende Ausdrucksauswertung kann ohne abschliessenden Wert
weiterlaufen. Tritt bereits bei einem Teilausdruck ein Fehler auf, werden
die nachfolgenden Teilausdrücke nicht mehr ausgewertet.

**Modellgrenze:** Die Regel, zuerst alle unmittelbaren Teilausdrücke
auszuwerten, gilt für die hier vereinbarten Operationen, nicht für sämtliche
Python-Ausdrücke. `and`, `or`, bedingte Ausdrücke und verkettete Vergleiche
können Teile unausgewertet lassen und benötigen bei ihrer Einführung eigene
Regeln. Sie gehören nicht zu diesem Teilbereich; einzelne Vergleiche wie
`3 < 5` dagegen schon.

**Anweisungen werden ausgeführt.** Ihre Regel kann Speicher und Ausgabe
verändern, Ausdrücke auswerten oder enthaltene Anweisungen ausführen.
Eine Zuweisung wertet beispielsweise zuerst die rechte Seite aus, speichert
den Ergebniswert und setzt danach die Anweisungsfolge fort.

Eine Schleife ist eine zusammengesetzte Anweisung. Ihr Rumpf ist ein Block
mit weiteren Anweisungen. Nach **regulärem Abschluss** der ganzen Schleife
steht die Fortsetzung durch die umgebende Programmstruktur fest. Damit ist
weder garantiert, dass die Schleife endet, noch festgelegt, wie oft der Rumpf
ausgeführt wird. `return` verlässt den aktuellen Funktionsaufruf; ein Fehler
verhindert ohne Fehlerbehandlung die normale Fortsetzung.

**Wiederholte Ausführung:** Erneut benötigter Code wird in seiner
ursprünglichen, unausgewerteten Form dargestellt. Bei `while` gilt das für
die Bedingung vor jeder erneuten Prüfung und für den Rumpf vor jedem weiteren
Durchgang. Speicher und Ausgabeprotokoll werden dabei nicht zurückgesetzt.
Die Bedingung liest deshalb die jeweils aktuellen Werte.
Bei `for` wird der Iterationsausdruck einmal ausgewertet; danach wird zum
nächsten Iterationswert fortgeschritten und der Rumpf für den nächsten
Durchgang wiederhergestellt. Ein neuer Funktionsaufruf blendet ebenfalls
den ursprünglichen Rumpf frisch ein, nicht den ausgewerteten Stand eines
früheren Aufrufs.

### Übergang zwischen den Versionen

Für die Funktion `quadrat(x)` mit dem Rumpf `return x * x` betrachten wir:

```python
ergebnis = (2 + 3) * quadrat(4)
```

Version 1 erklärt den rechten Ausdruck durch Einsetzen und weiteres Auswerten.
Version 2 beginnt die Zuweisungsanweisung und wertet deren rechte Seite aus.
Nach dem Auswerten der linken Summe ist folgender Stand sichtbar:

```text
ergebnis = 5 * quadrat(4)
```

Am Ort von `quadrat(4)` wird der Rumpf mit eigenem lokalem Speicher `x: 4`
eingeblendet. Die Zuweisung und die bereits ausgewertete `5` bleiben darum
herum sichtbar. Die Maschine führt `return x * x` aus, wertet dabei
`x * x` zu `16` aus und ersetzt den gesamten Aufruf samt Einblendung durch
`16`. Danach steht dort `ergebnis = 5 * 16`. Die Multiplikation ergibt
`80`, das anschliessend in `ergebnis` gespeichert wird. Es entsteht keine
Ausgabe.

Die erhaltene Programmstruktur zeigt, wo die Auswertung weitergeht.
`2 + 3` wird nach der Rückgabe nicht erneut ausgewertet. Bei Rekursion
werden dieselben Regeln auf mehrere eingeblendete Aufrufe angewandt.

## Gemeinsame Darstellungsregeln

- `→` bezeichnet einen erlaubten Auswertungsschritt, `=` eine Zuweisung,
  `==` einen Vergleich. Mathematische Definitionen werden als solche beschriftet.
- Wir trennen **Ausdruckskontext**, **aktuelle Anweisung**, **lokale
  Variablen des jeweiligen Aufrufs** und **Ausgabe**.
  Nur die jeweils benötigten Teile werden sichtbar gemacht.
- Ersetzungen erfolgen an Ort und Stelle im dargestellten Programm.
  Erneut benötigter Code wird wiederhergestellt, nicht der Speicher.
  Verfügbare Funktionsdefinitionen bleiben unverändert.
- Ein Zustandsübergang braucht eine Regel als Begründung. «Der Computer weiss,
  was gemeint ist» ist keine Erklärung.
- Reduktionsschritte und Visualisierungsereignisse müssen nicht dieselbe
  Granularität haben. Entscheidend ist, dass beide dieselben Variablenwerte,
  Reihenfolgen, Ergebnisse und Ausgaben vorhersagen.
- Fehler sind mögliche Ergebnisse eines Schritts. Fehlerursache und schon
  erfolgte Ausgaben werden getrennt festgehalten.

### Speicherzustand und Speicherprotokoll

Ein **Speicherzustand** zeigt die aktuell gespeicherten Werte und verfügbaren
Funktionen. Wir stellen ihn als Markdown-Blockzitat mit optionalen Unterblöcken
dar. Leere Unterblöcke entfallen; Beschriftungen werden fett gesetzt, nicht
als Markdown-Überschriften geschrieben:

> **Speicher**
>
> > **Variablen**
> >
> > ```text
> > a    2
> > ```
>
> > **Funktionen**
> >
> > ```python
> > def quadrat(x):
> >     return x * x
> > ```

Name-Wert-Paare zeigen einen Zustand, keine Zuweisungsanweisungen.
Funktionsdefinitionen werden vollständig als statischer Python-Code ohne
GLPython-Makro aufgelistet. Der Parameter `x` besitzt durch die Definition
noch keinen lokalen Wert. Globale Speicher und die lokalen Speicher
einzelner Aufrufe bleiben getrennt; lokale Speicher stehen bei der
jeweiligen Einblendung.

Ein **Speicherprotokoll** zeigt dagegen den zeitlichen Verlauf. Die bekannte
Tabellenform bleibt bestehen: Variablennamen sind Spaltenüberschriften,
darunter werden die Werte aufgeführt, welche die Variablen im Verlauf
angenommen haben. Sie wird nicht durch eine weitere Standardtabelle
«Variable | Gespeicherter Wert» ersetzt.
Bei solchen Tabellen werden automatische Diagramme und Sortierung mit
`<!-- data-type="none" data-sortable="false" -->` unmittelbar vor der Tabelle
abgeschaltet. Sortieren darf die zeitliche Reihenfolge nicht verändern.
Technische Referenzen:
[Blockquotes](https://github.com/LiaScript/docs/blob/master/README.md#blockquotes),
[Diagramme abschalten](https://github.com/LiaScript/docs/blob/master/README.md#none)
und [Tabellenattribute](https://github.com/LiaScript/docs/blob/master/README.md#attributes).

## M1 — Ausdrücke werden zu Werten ausgewertet

**Geltungsbereich:** Zunächst Zahlen, Zeichenketten, bekannte Variablen und die
vereinbarten arithmetischen beziehungsweise Vergleichsoperationen.
Zuweisungen und Kontrollfluss werden als Anweisungen daneben behandelt.

**Sichtbarer Zustand:** Noch auszuwertender Ausdruck, Variablen mit ihren gespeicherten Werten und
den markierten nächsten unausgewerteten Teilausdruck.

**Regeln:** Die unmittelbaren Teilausdrücke gemäss der oben beschriebenen
Struktur von links nach rechts auswerten. Werte benötigen keine weitere
Auswertung. Bei einer Variable den gespeicherten Wert lesen; bei einer
Operation zuerst die Operanden zu Werten auswerten, dann die Operation
ausführen. Den ausgewerteten Teilausdruck an Ort und Stelle durch seinen
Wert ersetzen und den übrigen Ausdruck erhalten. Wiederholen, bis ein Wert
übrig ist oder ein Fehler entsteht.
Eine noch nicht definierte Variable oder eine nicht erlaubte Operation führt
zum entsprechenden Fehler, nicht zu einem geratenen Wert.

**Angestrebtes mentales Modell:** «Ich kann sagen, was als Nächstes berechnet
wird und welcher Teil des Ausdrucks dadurch unverändert bleibt.»

**Diagnose und Nachweis:** `3 * (2 + 4)` schrittweise reduzieren; die
Zuweisungsfolge aus der Snap!-Diagnose protokollieren. Erwartet werden
`3 * 6 → 18` und am Ende die gespeicherten Werte `a: 8`, `b: 4`.

**Fehlvorstellung:** Zuweisung ändere rückwirkend den Wert einer anderen Variable oder
die Maschine arbeite Operationszeichen unabhängig von der Ausdrucksstruktur
in ihrer Reihenfolge im Text ab.

**Anschluss und Grenze:** Anschluss an bekannte Ausdrücke und mathematisches
Rechnen. Dieses Modell beschreibt noch keinen mehrzeiligen Funktionsablauf.

## M2 — Reine Ausdrucksfunktionen als Einsetzen

**Geltungsbereich:** Bekannte Funktionen mit gewöhnlichen positionellen
Parametern, deren Rumpf aus genau einer Anweisung `return ausdruck` besteht.
Der Ausdruck enthält Parameter, feste Werte, vereinbarte reine Operationen
und geeignete reine Funktionsaufrufe. Keine Ausgabe, Mutation, Abhängigkeiten
von veränderlichen globalen Variablen oder weiteren Python-Signaturformen.
Eine einzelne `return`-Anweisung allein garantiert diese Einschränkungen
nicht. Beispiel: mathematisch `f(x) = x² + 1`,
in Python `def f(x): return x * x + 1`.

**Sichtbarer Zustand:** Definition, Aufruf, ausgewertete Argumentwerte und
der verbleibende umgebende Ausdruck.

**Regeln:**

1. Das Aufrufziel bestimmen und die Argumentausdrücke von links nach rechts
   zu Werten auswerten. Einen unbekannten Funktionsnamen oder eine falsche
   Argumentanzahl als Fehler behandeln.
2. Im Rückgabeausdruck die Parametervorkommen durch die zugehörigen
   Argumentwerte ersetzen. Dies betrifft keine Teilwörter oder Zeichen
   innerhalb von Zeichenkettenliteralen.
3. Den Funktionsaufruf durch den so entstandenen, **geklammerten Ausdruck**
   ersetzen.
4. Die schrittweise Ausdrucksauswertung fortsetzen.

Die Argumente sind dabei die von links nach rechts auszuwertenden
Teilausdrücke des Aufrufs. Für `summe(a, b)` mit `return a + b` ergibt sich:

```text
summe(2 + 3, 4 + 5)
→ summe(5, 4 + 5)
→ summe(5, 9)
→ (5 + 9)
→ 14
```

Erst nachdem beide Argumente Werte sind, wird der Rückgabeausdruck eingesetzt.
Der neu eingesetzte Ausdruck ist zunächst unausgewertet; die Argumentwerte
darin müssen nicht nochmals ausgewertet werden.

Der Rumpf wird nicht schon bei der Definition ausgeführt. Die Klammerung
erhält die Gruppierung des eingesetzten Ausdrucks:

```text
2 * quadrat(4)
→ 2 * (4 * 4)
→ 2 * 16
→ 32

quadrat(2 + 3)
→ quadrat(5)
→ (5 * 5)
→ 25
```

Für `nachfolger(x)` mit `return x + 1` ist die Klammer besonders wichtig:

```text
2 * nachfolger(4)
→ 2 * (4 + 1)
→ 2 * 5
→ 10
```

Ohne Klammerung würde fälschlich `2 * 4 + 1` entstehen. Eingesetzt werden
ausgewertete Argumentwerte, nicht unausgewertete Argumentausdrücke.

**Angestrebtes mentales Modell:** «Ein Argument kann ein unausgewerteter
Ausdruck sein. Sein Wert wird eingesetzt, nicht der unausgewertete Ausdruck.»

**Diagnose und Nachweis:** Für `f(1 + f(2))` die Auswertung des inneren Aufrufs, den Wert `5`,
das äussere Argument `6` und schliesslich das Ergebnis `37` erklären.
Ein unbekannter Funktionsname ist als Fehler zu begründen. Die Schüler:innen
sollen ausserdem erklären, warum `quadrat(2 + 3)` zuerst zu `quadrat(5)` wird
und weshalb der Aufruf von `nachfolger` geklammert ersetzt werden muss.

**Fehlvorstellung:** Der äussere Rumpf beginne vor der Auswertung der Argumente;
Definition und Aufruf seien dasselbe.

**Anschluss und Grenze:** M1 bleibt gültig. Das Einsetzen ist eine gezielte
Rechenansicht für den reinen Teilbereich, keine textuelle Implementierung
beliebiger Python-Aufrufe. Sobald lokale Zuweisungen, Ausgabe und mehrere
Anweisungen relevant werden, ergänzen wir M3 ausdrücklich.

## M3 — Aufrufe mit lokalen Variablen und Rückkehrstelle

**Geltungsbereich:** Einfache benannte Funktionen, positionelle Argumente,
lokale Variablen, Verzweigungen, Schleifen, `print`, `return`, `pass`.
Globale Mutation, Closures und Aliasing veränderbarer Container bleiben aussen vor.

**Sichtbarer Zustand:** Aktuelle Anweisung; pro aktivem Aufruf ein eigener
am Aufrufort eingeblendeter Rumpf mit lokalen Variablen und ihren Werten;
erhaltener Ausdruckskontext und Ausgabeprotokoll.
Definitionen sind getrennt verfügbar. Ein Rahmen ist eine Erklärungshilfe,
keine Behauptung über die interne Speicherorganisation jeder Python-Laufzeit.
Die vollständige Komponentenübersicht steht bei Version 2. Die Ausführung
beginnt im globalen Speicher; während eines Aufrufs werden dessen lokale
Variablen verwendet. Für die vereinbarten einfachen Beispiele können nicht
lokale Lesezugriffe auf globale Variablen zugreifen. Eine Zuweisung an eine
lokale Variable verändert keine gleichnamige globale Variable; komplexere
Gültigkeitsbereichsregeln werden nicht durch zusätzliche Aufgaben eingeführt.

**Regeln:**

1. Eine Funktionsdefinition macht die Funktion unter ihrem Namen verfügbar,
   führt aber den Rumpf nicht aus.
2. Beim Aufruf wird das Aufrufziel bestimmt; die Argumentausdrücke werden von
   links nach rechts ausgewertet. Bei einem Fehler wird der Rumpf nicht betreten.
3. Nach erfolgreicher Zuordnung der Argumente beginnt ein neuer Aufruf.
   Eine frische Instanz des Rumpfs wird am Aufrufort eingeblendet.
   Die Argumentwerte werden in seinen eigenen Parametervariablen gespeichert.
   Falsche Argumentanzahl führt im betrachteten Teilbereich
   zu `TypeError`.
4. Der umgebende Ausdruck bleibt einschliesslich bereits berechneter
   Teilwerte erhalten. Lokale Zuweisungen speichern Werte in den lokalen
   Variablen dieses Aufrufs.
5. `print` schreibt in das Ausgabeprotokoll; sein Rückgabewert ist `None`.
   Ausgabe ersetzt keine Rückgabe eines berechneten Wertes.
6. Bei `return ausdruck` wird zuerst `ausdruck` ausgewertet. Danach endet
   dieser Aufruf; sein Wert ersetzt ihn samt Einblendung am Aufrufort. Nachfolgende
   Anweisungen dieses Aufrufs werden nicht mehr ausgeführt.
7. Ein erreichtes Funktionsende ohne `return` sowie ein nacktes `return`
   liefern `None`. `pass` tut nichts und setzt die Ausführung danach fort.
8. Nach regulärem Abschluss einer Anweisung wird die umgebende Anweisungsfolge
   fortgesetzt. Für Verzweigungen und Schleifen steuern deren Regeln die
   enthaltenen Blöcke. `return` und Fehler sind keine reguläre Fortsetzung
   an der nächsten Anweisung; nicht behandelte Fehler beenden das Programm,
   ohne bereits erfolgte Ausgaben rückgängig zu machen.

**Angestrebtes mentales Modell:** «Jeder Aufruf hat eigene lokale Variablen.
Der Aufrufer wartet auf einen Wert; ausgegebener Text ist eine andere Wirkung.»

**Diagnose und Nachweis:** Eine Funktion mit `print(x)` und ohne explizites
`return` im Ausdruck `f(3) + 1` verfolgen: erst Ausgabe `3`, dann `None` als
Funktionswert, anschliessend `TypeError`. In einem zweiten Beispiel mit
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
Ergebnis liefern. Die Werteboxen erklären nur den oben vereinbarten
Teilbereich. Vor Beispielen mit geteilten veränderbaren Objekten müsste das
Modell um Referenzen und Aliasing erweitert werden.

## M4 — Rekursion ist kein neuer Aufrufmechanismus

**Geltungsbereich:** Kleine, nachvollziehbare rekursive Aufrufe mit ausdrücklich
vereinbartem Eingabebereich. Erst ein rekursiver Teilauftrag, später
gegebenenfalls mehrere.

**Sichtbarer Zustand:** Dieselben Rahmen wie in M3, nun mit mehreren
Einblendungen derselben Definition, jeweils eigenem lokalen Speicher und
erhaltenem Ausdruckskontext.
Rekursion gehört damit zu Version 2 und erfordert keine dritte
Maschinenversion oder neue Aufrufregel.

**Regeln:** Ein Selbstaufruf arbeitet genauso wie ein anderer Aufruf. Er erhält
eigene Parametervariablen mit den übergebenen Werten. Der innere Aufruf wird
an seinem Aufrufort im äusseren Rumpf eingeblendet. Sein Rückgabewert ersetzt
diese Einblendung; danach geht die Auswertung im erhaltenen Kontext weiter.
Im Basisfall entsteht ein Ergebnis ohne weiteren Selbstaufruf.

**Angestrebtes mentales Modell:** «Die Definition ist einmal vorhanden,
aber mehrere Aufrufe können gleichzeitig noch nicht beendet sein. Ihre
Arbeit wird beim Rückweg fortgesetzt.»

**Diagnose und Nachweis:** Für einen vorgegebenen Vertrag «Zeichen zählen»
den Aufruf auf `"ab"` verfolgen: Rahmen für `"ab"`, `"b"`, `""`;
beim Rückweg Ergebnisse `0`, `1`, `2`. Dabei angeben, wo jeweils noch `1 + …`
wartet. Die nötigen Operationen für Leerprüfung und Restzeichenkette werden
vorher bereitgestellt; Indexierung und Slicing gelten nicht als Vorwissen.

**Wunschdenken als Entwurf:** Getrennt von diesem Ablauf annehmen, dass die
Funktion den strikt kleineren Rest gemäss Vertrag löst. Dann bestimmen, wie
dieses Ergebnis zum Gesamtergebnis ergänzt wird. Diese Annahme braucht
Eingabebereich, Basisfall und eine abnehmende Grösse; sie ist keine Behauptung,
Python errate das Resultat.

**Fehlvorstellungen:** Ein Selbstaufruf überschreibe den äusseren Parameter;
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
keinen Aufrufrahmen. Summation kann anschliessend den alten Ansatz verbinden.
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

**Angestrebtes mentales Modell:** «Eine Spezifikation legt das Verhalten
fest. Ein Python-Programm kann dieses Verhalten ausführen. Das Quellwort ist
dabei Eingabe und wird nicht selbst zu Python-Code.»

**Diagnose und Nachweis:** Einen kurzen Befehlsstring von Hand verfolgen;
einen neuen Befehl erst mit einer Wirkung und einem unterscheidenden Test
beschreiben, dann in der bereitgestellten Implementierung ergänzen.
Ein Test muss mehr prüfen als nur «das Programm läuft».

**Fehlvorstellungen:** Bedeutung und Implementierung seien dasselbe;
gespeicherte Posen würden in Speicherreihenfolge statt LIFO entnommen;
Rücksetzen lösche bereits gezeichnete Äste.

**Anschluss und Grenze:** Bekannte Zeichenschleifen und Funktionen tragen den
Interpreter. Befehls- und Aufrufstapel sind trotz ähnlicher LIFO-Ordnung
verschiedene Zustände. Die nötigen Stapeloperationen werden bereitgestellt.
Vor der Umsetzung ist festzulegen, ob ungültige Klammerfolgen ausgeschlossen
oder mit klarer Fehlermeldung behandelt werden. Es gibt kein stilles
«Reparieren» einer unterspezifizierten Eingabe.

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

**Angestrebtes mentales Modell:** «Wachstumsregeln erzeugen ein Wort.
Zeichenbefehle geben diesem Wort anschliessend eine grafische Bedeutung.»

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

Das vollständige Rezept wird mit Version 2 erklärt. Bereits der Platzhalter
`pass` liegt ausserhalb der eingeschränkten Rümpfe von Version 1; das gilt
auch für mehrzeilige Fallunterscheidungen und ausgebende Funktionen.
Reine fertige Lösungen können zusätzlich mit der Einsetzmaschine geprüft
werden.

| Schritt | Arbeitsprodukt | Erwartung an den Zwischenstand |
| --- | --- | --- |
| 1. Namen wählen | Benannte Definition, zunächst ohne Parameter und mit `pass`. | Die Datei ist syntaktisch gültig; noch keine Ergebnisprüfung. |
| 2. Parameter bestimmen | Signatur mit benannten Eingaben und vereinbartem Eingabebereich. | Definition bleibt ausführbar; spätere Aufrufe müssen zur Signatur passen. |
| 3. Zweck beschreiben | Kommentar mit Parametern, Ergebnis und gegebenenfalls Wirkungen. | `pass` bleibt als Platzhalter erhalten. |
| 4. Beispiele formulieren | Mindestens drei konkrete Fälle aus dem bisherigen Rezept, als direkte `assert`-Vergleiche mit erwarteten Werten. | Der Platzhalter liefert `None`; unerfüllte Tests dürfen nun `AssertionError` auslösen. |
| 5. Rumpf implementieren | Lösung nach Vertrag; bei Rekursion Basisfall, kleinerer Teilauftrag und Kombination. | Weiterhin gültiges Python; noch scheiternde Tests werden bearbeitet. |
| 6. Prüfen und überarbeiten | Tests ausführen, Abweichungen erklären, weitere Fälle ergänzen. | Die fertige Lösung besteht die vereinbarten Tests und wird erklärt. |

«Ausführbar» meint bis zur fertigen Lösung nicht «inhaltlich fertig».
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
anschliessen; gemeinsame Modell- und Lernzielnachweise bleiben verbindlich.

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
Das [GLPython-Makro](https://github.com/glpython-edu/glpython-liascript)
stellt Ausführung, Visualisierung und Turtle-Einbettung bereit.
Es ist ein Prüfwerkzeug, nicht die Definition der notionalen Maschine.

- Vor einem Lauf steht ein überprüfbarer eigener Gedanke; wahlloses
  Wiederholen der Ausführung ersetzt keine Erklärung.
- Für Aufrufrahmen werden nur tatsächlich verfügbare Visualisierungsansichten
  versprochen. Ob lokale Variablenwerte, Aufruforte und Zwischenausdrücke
  geeignet sichtbar sind, muss bei der späteren Inhaltserstellung geprüft
  werden; andernfalls ergänzen wir eine konsistente, im Kurs ausfüllbare
  manuelle Darstellung.
- Die Visualisierung muss nicht beide Maschinenversionen darstellen.
  Geklammerte Auswertungsprotokolle können in einem Texteingabefeld manuell neben
  der Python-Ausführung entstehen.
  Der Vergleich prüft übereinstimmende Ergebnisse, nicht eine identische
  Darstellung interner Ausführungsschritte.
- Die Makro-Laufzeiten der Blöcke sind isoliert. Spätere Beispiele müssen ihre
  benötigten Definitionen selbst enthalten.
- Einrückung und Syntaxhilfen unterstützen die Arbeit, übernehmen aber nicht
  die Modellbildung. Für Diagnosen werden auch Aufgaben ohne automatische
  Ausführung oder vorgegebenes Werkzeugprotokoll benötigt.

### Aufgaben vollständig im Kurs bearbeiten

Alle schriftlichen Bearbeitungsschritte müssen in der LiaScript-Umgebung
durchführbar sein. Papier oder eine externe Entwicklungsumgebung dürfen
keine Voraussetzung sein. Für Vorhersagen, Auswertungsprotokolle, Speicher- und
Ausgabeprotokolle, Begründungen, Überarbeitungen und eigenen Code wird
jeweils eine passende Eingabemöglichkeit vorgesehen. Gespräche und
Partnervergleiche bleiben möglich; ihre schriftlichen Ergebnisse können
ebenfalls im Kurs festgehalten werden.

| Bearbeitung | Vorgesehene Umsetzung |
| --- | --- |
| Eindeutige Antwort oder Zuordnung | Native LiaScript-Quizformate mit passender Rückmeldung. |
| Offene Vorhersage oder kurze Begründung | Native Texteingabe (Survey), beispielsweise `[[___]]`, ohne vorgegebene Lösung. |
| Mehrzeiliges Auswertungsprotokoll, Speicherprotokoll oder Erklärung | Mehrzeilige Texteingabe, beispielsweise `[[___ ___ ___ ___]]`; bei Bedarf mit einer statischen Vorlage für die Darstellung. |
| Ursprüngliche Vorhersage und spätere Korrektur | Getrennte Eingabebereiche, damit die erste Erklärung beim Überarbeiten erhalten bleibt. |
| Code verändern, entwerfen und prüfen | Editierbarer, mit dem passenden GLPython-Makro ausführbarer Codeblock im vorgesehenen Arbeitsschritt. |
| Bearbeitungsstand selbst kontrollieren | Task-Checkboxen; sie ersetzen weder Antwortfelder noch fachliche Nachweise. |

Offene Texteingaben werden nicht automatisch auf Richtigkeit geprüft.
Auch eine automatische Übermittlung an die Lehrkraft wird damit nicht
vorausgesetzt. Musterlösungen, Prüfkriterien oder ein begründeter Vergleich
unterstützen die Rückmeldung.

Wenn Code am Aufgabenanfang nur gelesen und sein Verhalten vorhergesagt
werden soll, steht er in einem gewöhnlichen Python-Codeblock **ohne
GLPython-Makro**. Beim ausdrücklich benannten Prüfschritt folgt ein separater
ausführbarer beziehungsweise visualisierbarer Block. Dieser enthält alle
benötigten Definitionen und Ausgangswerte, da die Makro-Laufzeiten isoliert
sind. Die Reihenfolge «vorhersagen, dann ausführen» ist eine didaktische
Vorgabe, keine technische Ausführungssperre.

«Von Hand» und «werkzeugfrei» bedeuten in diesen Materialien: ohne
automatische Programmausführung oder vorgegebenes Werkzeugprotokoll, nicht
ausserhalb des Kurses. Die Schüler:innen tragen beispielsweise ihr selbst
entwickeltes Auswertungsprotokoll in ein Texteingabefeld ein, bevor sie
das Ergebnis mit Python prüfen.

Technische Referenzen im offiziellen LiaScript-Manual:
[Text-Inputs](https://github.com/LiaScript/docs/blob/master/README.md#text-inputs),
[Quiz Types](https://github.com/LiaScript/docs/blob/master/README.md#quiz-types),
[Tasks](https://github.com/LiaScript/docs/blob/master/README.md#tasks) und
[Code](https://github.com/LiaScript/docs/blob/master/README.md#code).
Bei der späteren Materialerstellung werden Darstellung und Bedienbarkeit
der gewählten Eingaben im gerenderten Kurs geprüft.

### Knappe Aufgaben auf vollständigen Seiten

Jede Aufgabe enthält ihre konkreten Ausgangsdaten, Arbeitsaufträge,
Eingabefelder und den zugehörigen Prüfschritt im selben LiaScript-Abschnitt.
Auch Unterüberschriften erzeugen eigene Seiten. Innerhalb einer Aufgabe
werden deshalb fett gesetzte Beschriftungen statt weiterer
Markdown-Überschriften verwendet.

Eine vorgegebene Speicherbelegung bleibt mit allen zugehörigen Aktivitäten,
Hilfen und Rückmeldungen auf derselben Seite. Unabhängige Folgeaufgaben
geben ihren benötigten Speicher und Code erneut an. Allgemeine Regeln
dürfen vorher eingeführt werden; konkrete Ausgangsdaten werden nicht als
über Seiten hinweg sichtbar vorausgesetzt.

Aufträge sind knapp und unmittelbar verständlich, ohne allgemeine
Vorgehenspräambel. Nötige Hinweise stehen bei der jeweiligen Handlung.
Fachliche Regeln bleiben explizit; dass die Tätigkeit ein mentales Modell
aufbauen soll, wird im Material nicht oder nur minimal thematisiert.
Die didaktische Begründung gehört in diese Planung oder Lehrkrafthinweise.
Knappheit darf weder notwendige Informationen noch Eingabemöglichkeiten
verdrängen. Bei der späteren Materialprüfung wird jede gerenderte
Aufgabenseite einzeln auf Vollständigkeit kontrolliert.

## Formative Diagnose, Differenzierung und Überarbeitung

Für jedes Modell sammeln wir eine Vorhersage, eine regelbasierte Erklärung
und eine kleine Transferleistung. Ein richtiges Resultat ohne passende
Begründung reicht nicht; eine falsche Vorhersage mit sichtbarer Korrektur ist
ein wertvoller Lernnachweis.

Hilfen: teilausgefüllte Speicherprotokolle, markierte Aufruforte, bereitgestellte
String- und Turtle-Operationen. Vertiefung: eigene Gegenbeispiele, zusätzliche
Verzweigungen oder ein weiterer Sprachbefehl. Die Kernziele gelten für alle.

In der [Modellmatrix](paradigmen-matrix-template.md) werden typische
Fehlvorstellungen und Veränderungen im Erklären dokumentiert. Nach dem Einsatz
prüfen wir besonders:

- Bleibt die Trennung von Ausgabe und Rückgabe auch in neuen Kontexten erhalten?
- Werden rekursive Rückgaben ohne vollständiges Werkzeugprotokoll erklärt?
- Wird ein neuer Interpreterbefehl aus seiner Spezifikation heraus geprüft?
- Werden Ersetzung und Interpretation auch bei neuen Regeln getrennt?

Offen bleiben Unterrichtsumfang, Prüfungsrahmen, genaue Projekterfahrungen,
die endgültige Rekursionsaufgabe und der Umgang mit ungültigen Befehlswörtern.
Diese Entscheidungen sind vor der entsprechenden Kursausarbeitung zu treffen.