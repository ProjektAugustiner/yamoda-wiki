Abfragesprachen
==========

Metaweb Query Language
------------------------------------------

  * Doc [[http://mql.freebaseapps.com/]]
  * Cookbook [[http://wiki.freebase.com/wiki/MQL_Cookbook]]
  * Abfragen in der Wissens-Graphdatenbank freebase
  * Abfragen im JSON-Format, können sehr komplex werden

    * umfangreiche Filtermöglichkeiten
    * hierarchische Abfragen

  * erste Implementierung auf Serverseite in Python, dann Ocaml
  * Client-Libs in verschiendenen Sprachen, u.a. Python
  * anscheinend nur Closed-Source-Implementierung
  * bisher noch keine genaue Spezifikation gefunden, aber umfangreiche Doku mit Beispielen

OData
---------

  * offener Standard, von Microsoft entwickelt
  * umfangreiche Spezifikation 

    * muss aber von OData-Servern nicht vollständig implementiert werden (was zwingend ist, ist in der spec angegebenen)

  * Beispiele für Request-URIs [[http://www.odata.org/media/30002/OData.html#requestingindividualentities]]

    * ///Suppliers?$filter=Address/City ne 'London'//
    * ///Products?$filter=Price le 100//

  * Request und Responses über JSON möglich (oder XML: ATOM)
  * Client und Server-Libraries für einige Sprachen / Plattformen verfügbar

    * Library für Python (bzw. Google app engine) im Anfangsstadium stecken geblieben...
    * ruby_odata kann man sich mal anschauen

  * JS-Client-Libraries

    * datajs [[http://datajs.codeplex.com/]] 

      * eher Low-Level

    * Jaydata

      * unterstützt neben ODat auch andere Daten-Provider (MongoDB, IndexedDB ...)
      * ähnlich zu ORM DSLs (SQLAlchemy)
        * //northwind.Products//
        * //        .filter(function (product) {//
        * //            return product.ProductID in [1,5,7,8,23,68];//
        * //        })//

GData
---------

  * sollte mit OData konkurrieren
  * von Google früher für Google APIs benutzt
  * anscheinend deprecated und keine Weiterentwicklung bei Libraries
  *  => wahrscheinlich uninteressant

JLINQ
--------

  *  [[http://hugoware.net/projects/jlinq/demo]]
  *  LINQ-Abfragen für Javascript-Arrays

JSONPath
--------------

  * [[http://goessner.net/articles/JsonPath/]]
  * wie XPath, nur für JSON
  * Abfragen in baumstrukturierten Daten
  * Filter-Beispiel: Buch mit Preis < 10
    * //$..book[?(@.price<10)]//

JAQL
-------

  * [[http://code.google.com/p/jaql/wiki/JaqlOverview]]

SearchJS
-------------

  * [[https://github.com/deitch/searchjs]]

JSONIq
---------

  * [[http://jsoniq.org/]]

HTSQL
---------

  * [[http://htsql.org/]]
  * übersetzt URLs in SQL
  * Antwort als JSON, CSV oder XML möglich
  * interessant

RQL (Resource Query Language)
--------------------------------------------------

  * [[http://www.sitepen.com/blog/2010/11/02/resource-query-language-a-query-language-for-the-web-nosql/]]
  * simple URL Queries

MongoDB
-------------

  * [[http://www.mongodb.org/]]
  * benutzt Abfragesprache im JSON-Format


Graph-Plotten in Javascript
================

Sparkline
------------

  * vor allem für Übersichtsplots, z.B. integriert in Tabellenansichten
  * [[http://omnipotent.net/jquery.sparkline/#s-docs]]
  * sieht recht flexibel aus
  * auch Interaktion möglich (mouseover Werte anzeigen)
  * verschiedene Diagrammarten: Linie, Balken, Pie, Boxplots


Speichern von großen Datenmengen
=====================

  * Abspeichern von großen Dateien: z.B. 2D-Arrays (Bilddaten)
  * in Datenbank? Pro / Contra

    * [[http://wiki.postgresql.org/wiki/BinaryFilesInDB]]

  * HDF5

    * h5py [[http://code.google.com/p/h5py/]]
    * PyTables [[http://www.pytables.org/moin]]

