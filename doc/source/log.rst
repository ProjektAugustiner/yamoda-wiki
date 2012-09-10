^^^
Log
^^^

1 - 15.8.2012
========

Tobias:
-----------

  * Einlesen: Yamoda-Code
  * Einlesen / Wiederholung: Flask, SQLAlchemy, Javascript, Webprogrammierung / AJAX allgemein
  * Evaulation existierende Abfragesprachen
  * Testweise Implementierung von Abfrage-Use-Cases als SQLAlchemy-Queries
  * Neben SQLite Yamoda auch mit MySQL und PostgreSQL als Datenbank getestet

21.8.2012
======

Tobias:
-----------

  * Erste Version der Abfragesprache (AugQL) spezifiziert
  * Testweise Parser in Scala implementiert (nicht mehr ganz aktuell am Tagesende wg. Änderungen an der Sprache)
  * Interne Repräsentation der Queries (was vom Parser ausgegeben wird) modelliert
  * Code zum Zusammenbauen der SQLAlchemy-Queries aus der Query-Repräsentation geschrieben

    * bei Sets kann nach User und Zeitraum eingeschränkt werden
    * bei Datas geht

      * nach Parameterwerten einschränken (größer / kleiner / Intervall); or-Verknüpfung fehlt noch
      * nach Kontext einschränken (exakter Namensvergleich)
      * limit

22.8.2012
======

Tobias:
-----------

  * Set-Queries mit Limit möglich
  * Data-Queries: Sortieren geht; Fehler bei der Context-Zuordnung behoben
  * Testimplementierung des AugQL-Parsers in Scala auf neuesten Stand gebracht
  * Erste Implementierung AugQL-Parser in Python funktioniert (mit Parcon implementiert)

23.8.2012
======

Tobias:
-----------

  * Eingabe von Query-Strings über Web-UI und Übermittlung an Server geht (Menüpunkt Search)
  * Darstellung der Ergebnisse geht für sets (über setlist.html)
  * Bei datas wird die Anzahl der Treffer angezeigt (auf der Konsole auch die Entry-Daten)
  * OR geht jetzt auch bei Parameter-Filtern

26.8.2012
======

Tobias:
-----------

  * Einlesen: JQuery, Bootstrap
  * Data-Ergebnisse werden jetzt als Tabelle angezeigt
  * Query-History wird in die DB geschrieben
  * Benutzer bekommt alte Queries angezeigt und kann diese wieder ins Suchformular einfügen lassen

27.8.2012
======

Tobias:
-----------

  * Hilfetexte auf Search-Seite zu Möglichkeiten der Sprache mit Syntaxbeispielen
  * Löschen von alten Queries
  * Queries werden nur auf Wunsch gespeichert
  * Popovers zur Anzeige der Queries in formatierter Form

30.8.2012
======

Tobias:
-----------

  * Javascript für search.html etwas aufgeräumt, testweise nach Coffeescript übersetzt
  * Hilfe kann ausgeblendet werden


5.9.2012
======

Tobias:
-----------

  * Nose-Tests für Query-Parser
  * Query-Repräsentation ein wenig aufgeräumt
  * Fehler korrigiert: int und float-Literale werden jetzt vom Parser immer richtig konvertiert

6.9.2012
======

Tobias:
-----------

  * Ausführen von Queries aus der History
  * Tests für die SQLAlchemy-Query-Erstellung: ok
  * Direktes Ausführen von Queries aus der History

7-8.9.2012
======

Tobias:
-----------

  * Namen für Queries
  * Queries werden nur gespeichert, wenn Name und / oder der Query-String neu sind
  * Speicher-Button funktioniert
  * Ergebnisse können direkt auf der Suchseite angezeigt werden


9.9.2012
======

Tobias:
-----------

  * Testseite für die Anzeige von Daten eingebaut (Data Display Test in der Menüleiste)
  * Sparkline getestet, zeigt auf der Testseite 1D-Daten als Linien-Plot an. Breite passt sich der Tabellenzelle an.
  * 2D-Daten werden auf der Testseite als Matplotlib-Figure (imshow+ colorbar) in verkleinerter Form angezeigt

13.9.2012
======

Tobias:
-----------

Plan:
  * jqPlot und flot anschauen


