# Hinweise zur Anfertigung von Studien-, Diplom- und Masterarbeiten

Stand: 2020-03-04 15:01:43

**Achtung**: Diese Hinweise sind sehr subjektiv und ersetzen keinesfalls rechtsverbindliche Studiendokumente oder konkrete Absprachen im Betreuungsprozess.


## Programmierprozess (Python-spezifisch)

- Jupyter-Notebooks und Python-Skripte (bzw. -Module) haben unterschiedliche Vor- und Nachteile:
- **Notebooks:** (`.ipynb-Dateien)
    - (+) Code und Ergebnis (Text/Grafik) in *einem* Dokument.
    - (+) Interaktives Arbeiten (ausprobieren) funktioniert gut
    - (+) Niedrigschwelliges Anlegen neuer Notebooks
    - (-) Keine/Schlechte Untersstützung durch IDE (Pycharm, MS-Visual-Studio-Code, Spyder, ...)
    - (-) Umständliches Debuggen von Funktionen
    - (-) Keine direkte Möglichkeit zum Anwenden von Unittests auf Notebook-Code
    - (-) Tendenz zur Unübersichtlichkeit (Viele Notebooks in einem Verzeichnis, kein aussagekräftiger Name)
    - (-) Tendenz zur Code-Duplikation (Viele ähnliche Notebooks, die sich nur in kleinen aber ggf. wichtigen Details unterscheiden)

- **Python Skripte:** (`.py-Dateien)
    - Enthalten nur Code (inkl. Kommentaren und Docstrings), Keine Ergebnisse
    - (+) Lassen sich von anderen Skripten/Notebooks importieren -> Ermöglicht Wiederverwendung von Code
    - (+) Können (und sollten) mit Unittests überprüft werden (siehe unten)
    - (+) Lassen sich ohne Maus über Kommandozeile aufrufen und mit Kommandozeilen-Argumenten steuern.
    - (+) Sind meist etwas/deutlich schneller in der Ausführung als Notebooks.

    - (-) Interaktives Arbeiten (ausprobieren), ggf. umständlich, weil komplettes Skript immer wieder neu ausgeführt werden muss
        - Mögliche Abhilfe: `ipydex.IPS()` (Startet interaktive Kommandozeilen-Shell)
    - (-) Importierbarkeit hängt ggf. von der Verzeichnis-Struktur und `sys.path` ab.
        - Abhilfe: `sys.path.append(...)` oder `pip install -e .` (Pythonpaket lokal installieren, sodass Änderungen direkt wirksam werden)

- **Fazit:**
    - Notebooks sinnvoll für:
        - Ausprobieren neuer Ideen
        - Nachvollziehbare Implementierung von konkreten Beispielen (mit möglichst wenig allgemeinem Code)
    - Skripte/Module sinnvoll für
        - Allgemeinen Code, der unabhängig von konkreten Beispielen ist und länger leben soll.
        - Skripte zum Plotten von Grafiken für die Arbeit


### Automatisierte Software-Tests

- Hintergrund: Um zu verhindern, dass beim Erweitern/Korrigieren/Ändern von Software bestehende Funktionalität versehentlich kaputt geht muss Software getestet werden.
- Manuelle Tests sind kurzfristig schnell, aber weil man sie immer wieder ausführen muss (bzw. müsste) sind sie auf Dauer zeitaufwendig und unzuverlässig
- Abhilfe: automatisierte Tests. Das ist Software, die Software teste und das Ergebnis mit einem vorgegebenen Ergebnis vergleicht.
- In Python: [unittest-Modul](https://docs.python.org/3/library/unittest.html)
- Siehe auch: [Testgetriebene Entwicklung](https://de.wikipedia.org/wiki/Testgetriebene_Entwicklung)
    - Für die Wissenschaft und Anfänger:innen nur sehr bedingt geeignet
    - Der Ansatz verdeutlicht aber die Wichtigkeit von guter Test-Abdeckung (vor allem bei Code, der längere Zeit verwendet werden soll).


### Code-Qualität

Quellcode, der längere Verwendung finden und möglichst wenig Probleme bereiten soll, orientiert sich an folgenden Eigenschaften:

- PEP8-Kompatibilität (insbesondere Verwendung von Leerzeichen)
    - https://www.python.org/dev/peps/pep-0008/
    - https://realpython.com/python-pep8/

- Ordentlich formatierte Docstrings für jede Funktion/Klasse
- Aussagekräftige Bezeichner (Namen für Variablen, Funktionen Klassen). Abkürzungen können verwendet werden sollten aber in Kommentaren uder Docstrings erläutert werden.
- Kommentare die komplizierte Stellen beschreiben (Bei Bedarf: was passiert, meist sinnvoll: warum passiert das hier).
- In den meisten Fällen sind englische Bezeichner und Kommentare sinnvoll. Für den Einsatz in der Lehre kann davon ggf. abgewichen werden.


## Sonstiges

- Manchmal ist es sinnvoll zwei ((Quell-)Text-)Dateien zu vergleichen. Dafür gibt es sog. textbasierte und grafische Diff-Tools. Der Autor verwendet *kdiff3*, aber es gibt verschiedene [Alternativen](https://alternativeto.net/software/kdiff3/). Eine Integration eines solchen Tools mit *git* ist sehr sinnvoll (aber nicht der einzige Anwendungsfall).
- Wenn ein bisher unverstandenes Problem auftritt (Bug in Python, LaTeX-Fehler, ...) ist es meist die beste Strategie, das Problem in einem Minimalbeispiel einzugrenzen. D.h. eine Situtation herzustellen, in der sich das Problem reproduzieren lässt, die aber so wenig wie möglich sonstigen Ballast enthält. Beispiele:
    - Beginn mit fast leerem LaTeX-Dokument und abwechselnd Kompilieren und Hinzufügen von Inhalten aus dem problematischen Original.
    - Blockweies Auskommentieren (mittels Tastenkombination) von großen Teilen des Codes bis das Problem verschwindet, dann Schrittweises Einkommentieren


## Schreibprozess der Arbeit

- Gliederung anlegen und immer weiter verfeinern, zu einzelnen Abschnitten Stichpunkte aufschreiben, dann ausformulieren und ggf. andere Abschnitte mit Stichpunkten ergänzen
- Einleitung und Vorwort und Zusammenfassung und Ausblick ziemlich am Ende ausformulieren.
- Nicht die Zeit für das Schreiben unterschätzen. Realistischer Richtwert: 1-5 Seiten pro Tag.
- Ausreichend Zeit für Korrekturen einplanen (Zeitplan machen und regelmäßig überprüfen, spätestens eine Woche vor dem Ausdrucken sollte die Arbeit inhaltlich fertig sein.)
- Möglichst externe Korrekturleser organisieren (für die Sprache, für den Inhalt bzw. Verständlichkeit)
- nicht "beratungsresistent" sein, andere Entscheidungen ggf. begründen
- hilfreich: gute Fachliteratur als Vorbild nehmen (für Formulierungen und Notaion)
- Versionsverwaltung (git) für den LaTeX-Quellcode sinnvoll. Lokal oder auf einem Server. Nicht das gleiche Repo wie für den Programm-Quelltext verwenden. Häufige Commits sind hilfreich, wenn man später nochmal zurück möchte.
- Wenn es schwierig ist, eine gute/passende Formulierung zu finden, dann erstmal eine "subobtimale" Formulierung in Rot in den Text schreiben und sich nicht so lange damit aufhalten. Später kommt vielleicht eine bessere Idee.


        \usepackage{color}
        \newcommand{\tcred}[1]{\textcolor{red}{#1}} % für tmp-Hervorhebungen
        % ...
        \tcred{subobtimale Formulierung}




## Inhalt

Fogende Eigenschaften sind erstrebenswert und haben Einfluss auf die Bewertung

- Aufgabenstellung möglichst vollständig abgearbeitet. Wenn das nicht geht, dann Begründung in der Einleitung ("nach Rücksprache mit dem Betreuer wurde der Schwerpunkt... ").
- Ggf. Hilfreich: Abschnitt "Präzisierung der Aufgabenstellung" -> konkrete Forschungsfragen formulieren, ggf. nummerieren.
- Arbeit gut und nachvollziehbar gliedern ("roter Faden" muss jederzeit klar erkennbar sein)
- Gut verständlicher Text (kein unbekanntes Wissen voraussetzen: Sie selbst sollten die Arbeit verstehen, auch wenn sie ein anderes Thema bearbeitet hätten)
- Gute Quellenarbeit: Behauptungen, die Sie nicht selber erklären, sollten mit Literatur belegt sein. Möglichst mit Angabe von Abschnitt oder Seite, also z.B. [11, Abschnitt 5.2].

## Formalia

- Bedeutung *aller* Variablen einführen / erklären. Eine Aufführung im Symbolverzeichnis reicht *nicht*.
- Formeln gehören zum jeweils umgebenden Satz, d.h. nach einer Formel muss dann meist auch ein Komma oder ein Punkt stehen. Am besten an Vorbildern (Z.B. Buch von Prof. Röbenack, Dissertation vom Betreuer) orientieren. Achtung: Manche Veröffentlichungen sind dafür kein gutes Beispiel.
- Bildunterschriften enden mit einem Punkt.
- Eine Grafik oder Tabelle erst im Text erwähnen, bevor sie erscheint. Sonst wundert man sich beim Lesen was auf einmal diese Grafik bedeuten soll.
- Sätze möglichst nicht mit Symbol beginnen. Schlecht: "$m$ bezeichnet dabei die Masse." Besser: "Dabei bezeichnet $m$ die Masse."
- Quellen in Büchern möglichst mit konkreter Angabe, Abschnitt, Seite, etc. Fikitives Beispiel: "Nähere Informationen dazu finden sich in [19, Abschnitt 2.4.1]" (LaTeX: \cite[Abschnitt 2.4.1]{Mayer2011_Optimierung}).


## LaTeX Hinweise

- LaTeX bietet optionale Kurzversion für das Abbildungsverzeichnis bei zu langen Bildunterschriften
- \eqref statt \ref für Verweise auf Formeln
- Verwendung von := (Definition von a durch a:= b + c) und \stackrel{!}{=} (Forderung/Bedingung) wo es angebracht ist. Das erleichtert das Verständnis.
- Subequations kann man je nach Label zusammen oder getrennt referenzieren: "Gleichung (24)" oder "Gleichung (24b)"
- Deutsche Anführungszeichen in LaTeX bei Verwendung mit babel: "`Hallo Welt"'

## Grafiken

- Achsen beschriften!, Symbole und Text lesbar (Schriftgröße/Kontrast), Linien gut erkennbar (Farbe/Linienstil)
- Vektorgrafiken (PDF) oft besser als Pixelgrafiken. Bei Pixelgrafiken ist PNG meist besser als JPG (wegen Kompressionsverlusten bei JPG).
    - Beispiel: `plt.savefig("diagram_i_u.pdf")`
- Zum "Hübsch-Machen" von Grafiken (in matplotlib) müssen typischerweise plot-Parameter angepasst werden, z.B. plt.rcParams["font.size"] = 14, plt.rcParams['figure.subplot.bottom'] = .265, usw.
- Grafiken müssen typischerweise 10 bis 100 mal erstellt werden bis sie "richtig schön" sind. Deshalb ist es sinnvoll,
die Daten für die Erstellung (z.B. aus Simulation/aufwendiger Berechnung) separat zu speichern (z.B. numpy.save(...) oder pickle.dump(...)) und die Erstellung der Grafik(en) in einem separaten Skript oder Notebook durchzuführen. Daten laden (numpy.load(...), pickle.load(...)) -> Plotten.


## Organisatorisches

- Verlängerungsantrag (bei Diplomarbeiten) muss spätestens 4 Wochen vor offiziellem Abgabetermin beim Vorsitzenden des Prüfungsausschusses sein.
- Abgabe: 2 Exemplare, in einem muss die originale Aufgabenstellung (mit Unterschrift vom Prof.) enthalten sein, im anderen eine Kopie davon.




## Verteidigung


- Verteidigung Diplomarbeit: 30min Vortrag + Fragen
- Verteidigung Studienarbeit: 25min Vortrag + Fragen
- Richtwert: 0.5 bis 1 Folie (mit echtem Inhalt) pro Minute. -> ca. 30 Folien für den Vortrag

- Es passt nicht alles aus der Arbeit in den Vortrag. Groben Überblick geben und dann ausgewählte Details vorstellen. -> Nachvollziebare Gliederung.
- Folien nicht zu voll packen damit Publikum nicht erschlagen wird. Schrittweiser Aufbau und farbliche Hervorhebungen können didaktisch sehr hilfreich sein (-> Zusatzaufwand)
- Typischerweise keine Formelnummerierungen und keine Ganzen Sätze (sondern Stichpunkte) auf Folien
- Abbildungsunterschriften eher unüblich (Ausnahme: Angabe fremder Quellen)
- Erkennbarkeit der Grafiken noch wichtiger als in der Arbeit (Kontrast auf dem Beamer ist meist schlechter (keine gelben Kurven auf weißem Grund!), Publikum sitzt ggf. weit weg von der Projektionsfläche, weniger Betrachtungszeit)
- Votrag vorher mindestens drei mal üben. ggf. mit Diktiergerät-App aufnehmen und anhören. Der erste Übungsdurchlauf dauert erfahrungsgemäß deutlich länger. Kurze Notizen machen, welche Folien Änderungsbedarf haben.
- Vortrag spätestens ca. drei Tage vor der Verteidigung an Betreuer schicken

- Während des Vortrags mit Zeigestab oder Laserpointer (im Sekretariat ausleihbar) zeigen. Nicht mit der Hand oder dem Schatten, denn dadurch verdeckt man andere Teile der Folie.
- Empfehlenswert, die ersten und die letzten 3-5 Sätze auswendig lernen, den Rest des Vortrags frei auf Basis der eigenen Sachkenntnis und der Folien halten.
- Laut, klar und deutlich sprechen.
- Möglichst Blickkontakt öfter mal zum Publikum aufbauen. Schlecht: die ganze Zeit auf die Beamer-Projektion schauen, mit dem Rücken zum Publikum. Besser: seitlich hinstellen und nur wenn unbedingt nötig auf Projektionsfläche schauen. Blick auf das (entsprechend positionierte) Notebook ist besser (weil da das Gesicht zum Publikum zeigt), Blick zum Publikum ist am besten (aber auch am schwierigsten, weil man dann keine Gedächtnisstütze hat.)
