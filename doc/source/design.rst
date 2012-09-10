Abfragen
======

Abfragen von Sets und Datas vom Server nach bestimmten Kriterien

Use Cases
---------------

Welche Arten von Anfragen sind wichtig / interessant?

  * Konkrete Use-Cases:

    * suche alle sets von author:Tim_Adams, zeitraum:datum1-datum2
    * suche  alles author:Tim, probe:ofz66-3 (kann sowohl sets als auch datas   listen, sets aber nur, wenn alle darin enthaltenen datas kriterien   erfüllen)
    * alle datas mit T<30K
    * alle datas mit vsm.T2 im Interfall 20K-40K und B=3T

  * Allgemein Suche nach:

    * author -> wer die Messung durchgeführt hat
    * Messdatum/zeitraum
    * welche Probe
    * nach sets und/oder nach datas suchen
    * beliebige Wertebereiche oder Werte der entries

Abfragen aus Benutzersicht
-----------------------------

  * Benutzer soll Query-Strings direkt in einer möglichst intuitiven Abfragesprache eingeben können (Google- / SQL-like)
  * Alternativ soll die Eingabe über ein Formular möglich sein, mit dem man sich die Anfrage zusammenbauen kann
  * Antwort-Datensätze werden in Tabellen dargestellt
  * Auch interessant für später: code completion und syntax highlighting im Browser

Konzept und Weiterentwicklung
-------------------------------------
                 
  *  Abfragemöglichkeit für Clients über eine Web-API des Yamoda-Servers

    *     GUI-Client
    *     AJAX-Webanwendung
    *     andere (Python-)Skripte
    *     Übersicht: [[https://github.com/ProjektAugustiner/yamoda-wiki/raw/7c52d6f8db871b95d2a78d5e8b331080ad6fce05/design/client-server-interface.png]]                                   

  * Vorerst:  Parser für Abfragesprache im Server implementiert; Webclient schickt  Anfragen in Textform an den Server und bekommt Antwort als statisches  HTML zurück
  * Anschließend: Anworten als JSON, die vom Client verarbeitet werden; dynamische Tabellen
  * Später:   Anfragen auch als JSON verpacken; Sprache clientseitig parsen (syntax  highlighting und code completion anbieten) und daraus JSON-Anfrage   zusammenbasteln
  * Vielleicht: JSON-Anfragen nach OData-Standard


Spezifikation Abfragesprache (AugQL)
=======================

  * Übernimmt einige Ideen aus MQL und SQL
  * Besteht aus Klauseln (//a// : //b//), die entweder durch Kommata oder Zeilenumbruch getrennt sind (wie Objekte in Coffeescript)

    * //a// ist entweder ein Parametername oder ein Schlüsselwort (//find, user, context//, //limit, sort, created//)
    * erlaubte Werte für //b// werden im Folgenden beschrieben

Möglichkeiten
----------------------

  * was zurückgegeben werden soll, wird durch "//find//" angegeben; standardmäßig wird nach Sets gesucht (oder wäre Datas besser?)

  * Suche nach Sets: (//find: sets//)

    * //user//  Einschränkung nach User, der das Set angelegt hat): String
    * //created//  Einschränkung nach Zeitraum: Zeitintervall (siehe Beispiel unten, englische Monatsangaben)
    * //limit//  Max. Anzahl an zurückgegebenen Sets: Integer

  * Suche nach Datas (//find: datas//)

    * //context//  Einschränkung nach Context: String
    * //limit//  Max. Anzahl an zurückgegebenen Datas
    * //sort//  Sortierung: Angabe von Parametern (durch Leerzeichen getrennt), nach denen der Reihenfolge nach sortiert wird. 

      * //`Param_name`.asc//  aufsteigend
      * //`Param_name`.desc//  absteigend
      * Ohne Angabe aufsteigend

    * Einschränkung nach Parameterwerten (siehe unten)

Spezifikation von Einschränkungen nach Parameterwerten
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

  * größer  //T: > 5000//
  * kleiner  //T: < 200//
  * Bereich  //T: 10 to 300//
  * Mehrere Bereiche  //T: 10 to 300 or 400 to 500//

Beispiele
----------

  * Suchen nach Sets

    * //find: sets//
    * //user: tstenzel//
    * //created: 11 August 2012 to 15 August 2012//
    * limit: 4

  * Suchen nach Datas

    * //find: datas//
    * //context: TestContext//
    * //T: 0 to 400 or 500 to 600//
    * //omega: > 1e6//
    * //sort: T omega.desc//
    * //limit: 10//

Erweiterungsmöglichkeiten
--------------------------------

  * Nicht exakte Suche nach User oder Contextnamen (wie LIKE bei SQL)

    * //context: like %Bla%//

  * Nach weiteren Context-Metadaten suchen

    * Vorhandensein bestimmter Parameter
    * Probenname

  * Suche nach Sets, deren Datas bestimmte Kriterien erfüllen

    * all: Alle Datas müssen Kriterium erfüllen
    * any: Irgendein Data erfüllt Kriterium


DB Datenmodell
==========

  * aktuelles Modell als ER-Diagramm (MySQLWorkbench): [[https://github.com/ProjektAugustiner/yamoda-wiki/blob/7c52d6f8db871b95d2a78d5e8b331080ad6fce05/design/er_diagram_from_mysql_db.pdf]]

Was sollte noch ergänzt / geändert werden?

  * Abspeichern von Queries
  * Erweiterung Context für Probennamen und andere Metadaten



