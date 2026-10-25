# Sprachkonventionen

Dieser Leitfaden gilt für deutschsprachige Kursinhalte, Aufgaben,
Rückmeldungen und Planungsdokumente dieses Repositorys. Er wird beim
Schreiben neuer und beim Überarbeiten bestehender Texte angewendet.
Die bestehenden Texte wurden an diese Konventionen angepasst.

## Verbindliche Festlegungen

### Schweizer Standarddeutsch

- Schweizer Rechtschreibung verwenden: **ss statt ß**, beispielsweise
  «heisst», «anschliessend» und «ausserhalb».
- Umlaute im Fliesstext ausschreiben: «Ausdrücke», nicht «Ausdruecke».
- Für sprachliche Anführungen die Schweizer Guillemets «…» verwenden.
  Programmtext und Python-Zeichenketten behalten ihre korrekte Syntax.
- Dateinamen, URLs, externe Titel, wörtliche Zitate und Code nicht durch
  automatische Rechtschreibanpassungen verändern.

### Anrede in den Unterrichtsmaterialien

- Schüler:innen durchgehend mit **Sie** ansprechen.
- Auch bei Partner- und Gruppenaufgaben die Sie-Anrede beibehalten,
  nicht zu «ihr» wechseln.
- Höflichkeitspronomen grossschreiben: «Sie», «Ihnen», «Ihr», «Ihre».
- Beispiele:
  - «Notieren Sie zuerst Ihre Vorhersage.»
  - «Vergleichen Sie Ihre Begründung mit der Ihrer Partnerperson.»
  - «Prüfen Sie das Ergebnis erst danach mit Python.»

### Bezeichnungen in der internen Planung

- In den Planungsdokumenten **Schüler:innen** verwenden, nicht
  «Lernende», «Studierende» oder das generische «Schüler».
- In der Einzahl «Schüler:in» verwenden. Unnötig schwer lesbare
  Singularformulierungen möglichst umstellen.
- Wenn die unterrichtende Rolle gemeint ist, «Lehrkraft» verwenden.
- Beispiele:
  - «Die Schüler:innen erklären den nächsten Auswertungsschritt.»
  - «Die Lehrkraft sammelt unterschiedliche Begründungen.»

## Redaktionelle Leitlinien

### Klar und konkret schreiben

- Kurze Sätze und überschaubare Absätze bevorzugen. Pro Arbeitsauftrag
  eine klar erkennbare Handlung formulieren.
- Aufgaben so knapp und lokal verständlich formulieren, dass keine
  allgemeine Vorgehenspräambel nötig ist. Nötige Hinweise unmittelbar an
  die jeweilige Handlung stellen; Ausgangsdaten und Antwortform nicht auslassen.
- Auswertungs- und Ausführungsregeln explizit erklären, den didaktischen
  Zweck der Modellbildung im Material nicht oder nur minimal thematisieren.
  Ausführliche Begründungen gehören in Planung oder Lehrkrafthinweise.
- Im Schüler:innen-Text nur auf bereits behandelte Inhalte zurückverweisen.
  Keine Vorverweise auf späteren Stoff oder vorsorglichen Abgrenzungen
  gegenüber noch nicht eingeführten Konzepten verwenden.
- Eine Aufgabe samt Speicher, Code, Eingaben und Prüfschritt im selben
  LiaScript-Abschnitt halten. Innerhalb der Aufgabe fett gesetzte
  Beschriftungen statt seitenbildender Markdown-Zwischenüberschriften verwenden.
- Verben verwenden, die ein beobachtbares Ergebnis verlangen:
  «markieren», «notieren», «begründen», «vergleichen», «verändern».
- Bei Aufgaben angeben, was festgehalten werden soll. Statt nur
  «Überlegen Sie» beispielsweise: «Notieren Sie den nächsten Schritt und
  begründen Sie ihn mit einer Regel.»
- Keine verniedlichenden oder wertenden Zusätze wie «ganz einfach»,
  «natürlich» oder «offensichtlich» zur Beschreibung einer Aufgabe verwenden.

### Fachbegriffe präzise verwenden

- Fachbegriffe bei der ersten Verwendung erklären und danach konsistent
  benutzen. Präzision geht vor stilistischer Abwechslung.
- «Ausdruck», «Wert», «Ausgabe», «Zuweisung» und «Variable» nicht als
  austauschbare Wörter verwenden.
- **«Ausgewerteter Ausdruck» und «Wert» sind in unserem Unterrichtsmodell
  Synonyme.** Dies bei der Einführung ausdrücklich erklären. Den anderen
  Fall als «unausgewerteten Ausdruck» bezeichnen, nicht als «Rechnung» oder
  «offene Rechnung». Für einen Teil eines Ausdrucks «Teilausdruck» verwenden.
- «Auswertungsprotokoll» statt «Spur», «Einsetzspur» oder «Reduktionsspur»
  verwenden. Es hält den Ausgangsausdruck und die einzelnen Schritte bis
  zu einem Wert oder Fehler fest. Bei allgemeiner Anweisungs- oder
  Befehlsausführung von einem «Ablaufprotokoll» sprechen.
- «Speicherzustand» bezeichnet die aktuellen Inhalte, «Speicherprotokoll»
  deren zeitliche Entwicklung. «Ausgabeprotokoll» bleibt die Bezeichnung
  für bereits ausgegebene Texte.
- Ausdrücke werden im dargestellten Programm an Ort und Stelle ersetzt.
  Keine separate Arbeitskopie und keinen «wartenden Ausdruck» als
  zusätzliches Konzept verlangen. Der umgebende Ausdruck bleibt sichtbar.
- Das vereinbarte Box-Modell verwenden: «Der Wert wird in der Variable
  gespeichert» und «Der gespeicherte Wert wird gelesen», nicht «Der Name wird
  an einen Wert gebunden». Speicherzustände als Block mit optionalen
  Unterblöcken «Variablen» und «Funktionen» darstellen: Name-Wert-Paare und
  vollständige statische Definitionen, keine Zuweisungen als Zustandsnotation.
  Das bekannte Speicherprotokoll mit Variablennamen als Spalten bleibt
  für Verläufe erhalten. Darstellung steht in den
  [Speicherregeln](lecture-didactics.md#speicherzustand-und-speicherprotokoll);
  Geltungsbereich und Grenzen stehen in der
  [didaktischen Festlegung](lecture-didactics.md#festlegung-werte-werden-in-variablen-gespeichert).
- «Parameter» für die Definition, «Argument» für den Aufruf verwenden.
- Die angebotene **notionale Maschine** vom individuellen **mentalen Modell**
  der Schüler:innen unterscheiden.
- Code, Namen und Operatoren mit Backticks kennzeichnen, etwa `preis`,
  `return` oder `==`. Erklärpfeile wie `→` nicht als Python-Syntax darstellen.
- Keine Absichten oder Fähigkeiten in die Maschine hineinlesen:
  Statt «Python versteht, was Sie meinen» die konkrete Auswertungsregel nennen.

Die fachlichen Regeln und Grenzen der Modelle stehen in der
[Didaktik](lecture-didactics.md); dieser Leitfaden regelt ihre sprachliche
Darstellung.

## Kurze Prüfung vor der Veröffentlichung

- Ist der Text in Schweizer Standarddeutsch geschrieben?
- Bleibt die Anrede auch in gemeinsamen Aufgaben bei «Sie»?
- Verwenden interne Texte die Bezeichnung «Schüler:innen»?
- Sind Arbeitsaufträge konkret und Fachbegriffe konsistent?
- Sind Code, Zitate, URLs und externe Titel unverändert korrekt?

Weitere Sprachentscheidungen werden hier ergänzt, damit dieser Leitfaden
die zentrale Referenz bleibt.
