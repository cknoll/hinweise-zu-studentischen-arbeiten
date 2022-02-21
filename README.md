# Subjektive Hinweise zur Anfertigung von Studien-, Diplom- und Masterarbeiten

Stand: 2020-06-26

**Achtung**: Dieses Dokument fasst typische Hinweise aus vergangenen Betreuungsprozessen zusammen. Diese Hinweise sind sehr subjektiv und ersetzen keinesfalls rechtsverbindliche Studiendokumente oder konkrete Absprachen im Betreuungsprozess.

Weitere wichtige Hinweise finden Sie auf der Webseite des Instituts für Regelungs- und Steuerungstheorie: [Hinweise für die Durchführung von Diplom-, Master- und Studienarbeiten](
https://tu-dresden.de/ing/elektrotechnik/rst/studium/diplom-master-studienarbeit/hinweise-fuer-die-durchfuehrung-von-diplom-master-und-studienarbeiten).


## Intellektueller Prozess

- Das Anfertigen einer studentischen Arbeit ist ein aufwendiger und anstrengender Prozess.
- Typischerweise umfasst er folgende (teilweise überlappende) Komponenten, wobei die Gewichtung stark vom Thema abhängt.
    - Literaturrecherche
        - Speichern Sie alle relevante Literatur, so dass sie im Schreibprozess die entsprechende Quelle möglichst schnell wiederfinden.
        - Machen Sie sich (digitale) Anmerkungen. Formulieren Sie Fragen explizit.
    - Konzeption und Berechnung
        - Fertigen Sie ausgiebige handschriftliche Notizen an. Herleitungen, Berechnungen, Skizzen, Blockdiagramme, Variantenabwägungen, offene Fragen etc. Das Aufschreiben von Gedanken hilft beim Präzisieren.
        - Geben Sie jedem Blatt eine Überschrift (z.B. "Stabilitätsbetrachtung"), notieren Sie das Datum und eine (tagesbeozgene) laufende Nummer. So können Sie später (z.B. im Quellcode auf Details verweisen.
        - Heften Sie die Papiere zeitnah zusammen. Lose Blätter sind eine maßgebliche Entropiequelle.
    - Software Entwicklung
        - Nutzen Sie Versionsverwaltung (siehe [Hinweise](https://tu-dresden.de/ing/elektrotechnik/rst/studium/diplom-master-studienarbeit/hinweise-fuer-die-durchfuehrung-von-diplom-master-und-studienarbeiten) oben).
        - Siehe weitere Hinweise unten
    - Hardwareentwicklung, Versuchsvorbereitung und Durchführung von Experimenten
        - Diese Tätigkeiten hängen oft von externen Faktoren ab (Lieferzeiten, Verfügbarkeit des Versuchsstandes, ...) und benötigen typischerweise mehr Zeit als geplant.
- Formulieren Sie die jeweilige Frage, der sie aktuell nachgehen, schriftlich. Z.B. Wie hängt die Lösbarkeit der Gleichung (XYZ) von Parameter *µ* ab? Welche weiteren Quellen verweisen noch auf \[17\]?
- Allgemeine Hinweise zum Lösen von Forschungsfragen finden sich in dem Artikel "[Solving Research Problemes](http://www-personal.umich.edu/~dsbaero/tutorials/SolvingResearchProblemsV1.pdf)" von D. S. Bernstein. Insbesondere die Hinweise Nr. 4, 8, 19, 22 sind hervorzuheben.

## Interaktion mit dem Betreuer

- Zeigen Sie Eigeninitiative, z.B. durch regelmäßige Statusberichte. Es geht um Ihre Arbeit.
- Die Betreuungskapaziät ist beschränkt. Nutzen Sie sie möglichst effektiv.
- Bereiten Sie Betreuungstreffen vor, z.B. durch
    - Aufschreiben konkret zu klärender Fragen,
    - Zusammenstellen der wichtigsten Grafiken,
    - Zusammenfassung der beim letzten Mal angesprochenen Fragen, der seitdem erzielten Fortschritte und der neu aufgetretenen Fragen.
- Das Nutzen eines Kanban-Organisationstools kann beiden Seiten helfen, die Übersicht zu bewahren.

## Zeitplanung

- Grundregel: Die meisten Vorhaben dauern signifikant länger als geplant (Auch trotz Einbezug der dieser Grundregel in die Planung).
- Lange Zeiträume und große Aufgaben sind anfällig für ineffizientes Arbeiten (Bsp: Sechs Monate – Diplomarbeit schreiben). Setzen Sie sich Zwischenziele mit konkreten Terminen. Z.B.: "Bis nächsten Mittwoch: Kapitel 4 fertig zum Korrekturlesen.", "Bis 16:30 Uhr: Software XYZ installiert und getestet."
- Probieren Sie die Nutzung eines Zeiterfassungs-Werkzeuges aus, z.B. "[super productivity](https://super-productivity.com/)".


## Programmierprozess (Python-spezifisch)

- Allgemeine Infos: <https://tu-dresden.de/ing/elektrotechnik/rst/studium/python-in-der-lehre>

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

- Hintergrund: Um zu verhindern, dass beim Erweitern/Korrigieren/Ändern von Software bestehende Funktionalität versehentlich kaputt geht, muss Software getestet werden.
- Manuelle Tests sind kurzfristig schnell, aber weil man sie immer wieder ausführen muss (bzw. müsste) sind sie auf Dauer zeitaufwendig und unzuverlässig.
- Abhilfe: automatisierte Tests. Das ist Software, die Software testet und das Ergebnis mit einem vorgegebenen Ergebnis vergleicht.
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
- Vermeiden Sie hart kodierte absolute Pfade zu Dateien oder Verzeichnissen. Code der solche Pfade enthält auf de facto allen anderen Systemen nicht lauffähig und kann demnach von Ihrem Betreuer so nicht ausgeführt werden. Tipp: Wenn relative Pfade wie `../../data` nicht ausreichen, definieren Sie absolute Pfade zur Laufzeit, z. B. so: 
```
import os
import sys
# get absolute path of directory of this file
current_dir = os.path.dirname(os.path.abspath(sys.modules.get(__name__).__file__))
```
- Wenn Sie Jupyter-Notebooks für einen Zwischen-Bericht oder am Ende der Arbeit einreichen, vergewissern Sie sich, dass jedes Notebook auch wirklich fehlerfrei durchläuft. Hintergrund: Durch das Interaktive arbeiten passiert es oft, dass eine Zelle nachträglich geändert wird, was erst beim nächsten Neustart des Notebook-Kernels auffällt.


## Versionsverwaltung mit git

- Gut nachvollziehbare Dokumentation des Arbeitsfortschritts mit Versionskontrolle hat mehrere Vorteile:
    - Mehr Sicherheit für Sie, denn Sie können jederzeit zu einem früheren Stand zurückkehren
    - Erleichterung des Betreuungsprozesses (was hat sich seit der letzen Besprechung geändert)
    - Ggf. Verwaltung von Parallelitäten in Zweigen ("Branches"), z.B. um ein experimentelles Feature einzubauen
- Nachvollziehbarkeit erreichen Sie durch
    - Thematisch zusammengehörige Änderungen auch zusammen kommittieren.
    - Änderungen die mehrere Themen betreffen möglichst getrennt kommittieren
    - Aussagekräftige und eindeutige Kommit-Nachrichten schreiben
    - Kommit-Geschichte editieren, siehe <https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History>, z.B.:
        - `git comit --amend` verwenden, um nachträglich Kommits zu ändern (Nachricht uder Inhalt)
        - `git rebase --interactive HEAD~5` (die letzten fünf Kommits umsortieren , zusammenlegen, etc.)
    - Bei paralleler Arbeit an mehreren Zweigen möglichst `rebase` statt `merge` verwenden (→ lineare History)
        - Gute Animation: https://onlywei.github.io/explain-git-with-d3/#rebase
    - `git push -f` sehr vorsichtig verwenden (erst pushen, wenn die History gut ist)
- `gitk --all` oder git gui helfen bei der Übersicht, besonders bei mehreren Zweigen
- Im LaTeX-Repo: pdf-Datei nur Kommitten, wenn deren Änderung relevant ist

## Sonstiges

- Manchmal ist es sinnvoll zwei ((Quell-)Text-)Dateien zu vergleichen. Dafür gibt es sog. textbasierte und grafische Diff-Tools. Der Autor verwendet *kdiff3*, aber es gibt verschiedene [Alternativen](https://alternativeto.net/software/kdiff3/). Eine Integration eines solchen Tools mit *git* ist sehr sinnvoll (aber nicht der einzige Anwendungsfall).
- Wenn ein bisher unverstandenes Problem auftritt (Bug in Python, LaTeX-Fehler, ...) ist es meist die beste Strategie, das Problem in einem Minimalbeispiel einzugrenzen. D.h. eine Situtation herzustellen, in der sich das Problem reproduzieren lässt, die aber so wenig wie möglich sonstigen Ballast enthält. Beispiele:
    - Beginn mit fast leerem LaTeX-Dokument und abwechselnd Kompilieren und Hinzufügen von Inhalten aus dem problematischen Original.
    - Blockweies Auskommentieren (mittels Tastenkombination) von großen Teilen des Codes bis das Problem verschwindet, dann Schrittweises Einkommentieren


## Schreibprozess der Arbeit

- Empfehlung: Noch in der ersten Woche der Arbeit ein Dokument (typischerweise in LaTeX) anlegen, aus dem dann Schritt für Schritt die Arbeit wächst
	+ Nutzen Sie die [Vorlage](https://tu-dresden.de/ing/elektrotechnik/rst/studium/diplom-master-studienarbeit/hinweise-fuer-die-durchfuehrung-von-diplom-master-und-studienarbeiten) des Instituts und beachten Sie die weiteren [Hinweise](https://tu-dresden.de/ing/elektrotechnik/rst/studium/diplom-master-studienarbeit/hinweise-fuer-die-durchfuehrung-von-diplom-master-und-studienarbeiten).
	+ Frühzeitiges Anlegen des Dokuments senkt die erfahrungsgemäß signifikante Hürde, mit dem Schreibprozess zu beginnen.
	+ (Vorläufige) Gliederung (Schema: *Einleitung*, *Grundlagen*, *Untersuchungen*, *Ergebnisse*, *Zusammefassung*) anlegen und immer weiter verfeinern, zu einzelnen Abschnitten Stichpunkte aufschreiben, dann ausformulieren und ggf. andere Abschnitte mit Stichpunkten ergänzen
	+ Zwischenergebnisse in Form von Grafiken oder Fragen temporär in das Dokument aufnehmen (z.B. als Grundlage für Betreuungsgespräch)
- Einleitung und Vorwort und Zusammenfassung und Ausblick ziemlich am Ende ausformulieren.
- Nicht die Zeit für das Schreiben unterschätzen. Realistischer Richtwert: 1-3 Seiten pro Tag (wenn Inhalt und Grafiken klar sind).
- Ausreichend Zeit für Korrekturen einplanen (Zeitplan machen und regelmäßig überprüfen, allerspätestens eine Woche vor dem Ausdrucken sollte die Arbeit inhaltlich fertig sein. Korrekturen einzelner Kapitel sollten schon früher beginnen.)
- Möglichst externe Korrekturleser organisieren (für die Sprache, für den Inhalt bzw. Verständlichkeit)
- nicht "beratungsresistent" sein, andere Entscheidungen ggf. begründen
- hilfreich: gute Fachliteratur als Vorbild nehmen (für Formulierungen und Notaion). Orientierung an bisherigen Veröffentlichungen [des Institutsdirektors](https://www.springer.com/de/book/9783662440902) bzw. [des Betreuers](https://tud.qucosa.de/landing-page/?tx_dlf[id]=https%3A%2F%2Ftud.qucosa.de%2Fapi%2Fqucosa%253A29777%2Fmets) 
- Versionsverwaltung (git) auch für den LaTeX-Quellcode sinnvoll. Lokal oder auf einem Server. Nicht das gleiche Repo wie für den Programm-Quelltext verwenden. Häufige Commits sind hilfreich, wenn man später nochmal zurück möchte.
- Wenn es schwierig ist, eine gute/passende Formulierung zu finden, dann erstmal eine "subobtimale" Formulierung in Rot in den Text schreiben und sich nicht so lange damit aufhalten. Später kommt vielleicht eine bessere Idee.


        \usepackage{color}
        \newcommand{\tcred}[1]{\textcolor{red}{#1}} % für tmp-Hervorhebungen
        % ...
        \tcred{subobtimale Formulierung}



### Inhalt

Fogende Eigenschaften sind erstrebenswert und haben Einfluss auf die Bewertung

- Aufgabenstellung möglichst vollständig abgearbeitet. Wenn das nicht geht, dann Begründung in der Einleitung ("nach Rücksprache mit dem Betreuer wurde der Schwerpunkt... ").
- Ggf. Hilfreich: Abschnitt "Präzisierung der Aufgabenstellung" -> konkrete Forschungsfragen formulieren, ggf. nummerieren.
- Arbeit gut und nachvollziehbar gliedern ("roter Faden" muss jederzeit klar erkennbar sein)
- Gut verständlicher Text (kein unbekanntes Wissen voraussetzen: Sie selbst sollten die Arbeit verstehen, auch wenn sie ein anderes Thema bearbeitet hätten)
- Gute Quellenarbeit: Behauptungen, die Sie nicht selber erklären, sollten mit Literatur belegt sein. Möglichst mit Angabe von Abschnitt oder Seite, also z.B. [11, Abschnitt 5.2].

### Formalia

- Bedeutung *aller* Variablen einführen / erklären. Eine Aufführung im Symbolverzeichnis reicht *nicht*.
- Formeln gehören zum jeweils umgebenden Satz, d.h. nach einer Formel muss dann meist auch ein Komma oder ein Punkt stehen. Am besten an Vorbildern (Z.B. Buch von [Prof. Röbenack](https://www.springer.com/de/book/9783662440902) oder [Dissertation des Betreuers](https://nbn-resolving.org/urn:nbn:de:bsz:14-qucosa-209765)) orientieren. Achtung: Manche Veröffentlichungen sind dafür kein gutes Beispiel.
- Bildunterschriften enden mit einem Punkt.
- Eine Grafik oder Tabelle erst im Text erwähnen, bevor sie erscheint. Sonst wundert man sich beim Lesen was auf einmal diese Grafik bedeuten soll.
- Sätze möglichst nicht mit Symbol beginnen. Schlecht: "$m$ bezeichnet dabei die Masse." Besser: "Dabei bezeichnet $m$ die Masse."
- Quellen in Büchern möglichst mit konkreter Angabe, Abschnitt, Seite, etc. Fikitives Beispiel: "Nähere Informationen dazu finden sich in [19, Abschnitt 2.4.1]" (LaTeX: `\cite[Abschnitt 2.4.1]{Mayer2011_Optimierung}`).


### LaTeX Hinweise

- LaTeX bietet optionale Kurzversion für das Abbildungsverzeichnis bei zu langen Bildunterschriften
- \eqref statt \ref für Verweise auf Formeln
- Verwendung von := (Definition von a durch a:= b + c) und \stackrel{!}{=} (Forderung/Bedingung) wo es angebracht ist. Das erleichtert das Verständnis.
- Subequations kann man je nach Label zusammen oder getrennt referenzieren: "Gleichung (24)" oder "Gleichung (24b)"
- Deutsche Anführungszeichen in LaTeX bei Verwendung mit babel: "`Hallo Welt"'
- Ableitungspunkt kommt zentral über die Variable (ohne Indizes): richtig: `\dot{x}_1`, falsch: `\dot{x_1}`.
- Unter Windows sperrt der Acrobat-Reader die PDF-Datei und verhinder deshalb, dass sie von LaTeX neu geschrieben werden kann. Empfehlung: Verwendung des freien und schnellen PDF-Readers [Sumatra PDF](https://www.sumatrapdfreader.org/free-pdf-reader.html)

### Grafiken

- Achsen beschriften!, Symbole und Text lesbar (Schriftgröße/Kontrast), Linien gut erkennbar (Farbe/Linienstil)
  - Minimale Schriftgröße in Abbildungen sollte ca. der Schriftgröße von Fußnoten im Text entsprechen.
- Vektorgrafiken (PDF) oft besser als Pixelgrafiken. Bei Pixelgrafiken ist PNG meist besser als JPG (wegen Kompressionsverlusten bei JPG).
    - Beispiel: `plt.savefig("diagram_i_u.pdf")` oder `plt.savefig("raster_image.png")`
- Zum "Hübsch-Machen" von Grafiken (in matplotlib) müssen typischerweise plot-Parameter angepasst werden, z.B. `plt.rcParams["font.size"] = 14`, `plt.rcParams['figure.subplot.bottom'] = .265`, usw.
- Grafiken müssen typischerweise 10 bis 100 mal erstellt werden bis sie "richtig schön" sind. Deshalb ist es sinnvoll,
die Daten für die Erstellung (z.B. aus Simulation/aufwendiger Berechnung) separat zu speichern (z.B. `numpy.save(...)` oder `pickle.dump(...)`) und die Erstellung der Grafik(en) in einem separaten Skript oder Notebook durchzuführen. Daten laden (`numpy.load(...)`, `pickle.load(...)`) -> Plotten.


## Organisatorisches

- Verlängerungsantrag (bei Diplomarbeiten) muss spätestens 4 Wochen vor offiziellem Abgabetermin beim Vorsitzenden des Prüfungsausschusses sein.
- Abgabe: 2 Exemplare, in einem muss die originale Aufgabenstellung (mit Unterschrift vom Prof.) enthalten sein, im anderen eine Kopie davon.




## Verteidigung


- Verteidigung Diplomarbeit: 30min Vortrag + Fragen
- Verteidigung Studienarbeit: 25min Vortrag + Fragen
- Richtwert: 0.5 bis 1 Folie (mit echtem Inhalt) pro Minute. -> Obergrenze: ca. 30 Folien 

- Es passt nicht alles aus der Arbeit in den Vortrag. Groben Überblick geben und dann ausgewählte Details vorstellen. -> Nachvollziebare Gliederung.
- Folien nicht zu voll packen, damit Publikum nicht erschlagen wird. Bei komplexen Folien: Schrittweiser Aufbau und farbliche Hervorhebungen können didaktisch sehr hilfreich sein (-> Zusatzaufwand beim Erstellen berücksichtigen)
- Typischerweise keine Formelnummerierungen und keine ganzen Sätze (sondern Stichpunkte) auf Folien
- Abbildungsunterschriften eher unüblich (Ausnahme: Angabe fremder Quellen)
- Erkennbarkeit der Grafiken (inkl. Achsbeschriftungen, etc.) noch wichtiger als in der Arbeit (Kontrast auf dem Beamer ist meist schlechter (keine gelben Kurven auf weißem Grund!), Publikum sitzt ggf. weit weg von der Projektionsfläche, weniger Betrachtungszeit). Bei Online-Verteidigungen: ggf. Einbußen bei Übertragungsqualität berücksichtigen.
- Votrag vorher mindestens drei mal üben. ggf. mit Diktiergerät-App aufnehmen und anhören. Der erste Übungsdurchlauf dauert erfahrungsgemäß deutlich länger. Kurze Notizen machen, welche Folien Änderungsbedarf haben.
- Vortrag spätestens ca. drei Tage vor der Verteidigung an Betreuer schicken

- Während des Vortrags mit Zeigestab oder Laserpointer (im Sekretariat ausleihbar) zeigen. Nicht mit der Hand oder dem Schatten, denn dadurch verdeckt man andere Teile der Folie.
- Empfehlenswert, die ersten und die letzten 3-5 Sätze auswendig lernen, den Rest des Vortrags frei auf Basis der eigenen Sachkenntnis und der Folien halten.
- Laut, klar und deutlich sprechen.
- Möglichst Blickkontakt öfter mal zum Publikum aufbauen. Schlecht: die ganze Zeit auf die Beamer-Projektion schauen, mit dem Rücken zum Publikum. Besser: seitlich hinstellen und nur wenn unbedingt nötig auf Projektionsfläche schauen. Blick auf das (entsprechend positionierte) Notebook ist besser (weil da das Gesicht zum Publikum zeigt), Blick zum Publikum ist am besten (aber auch am schwierigsten, weil man dann keine Gedächtnisstütze hat.)
