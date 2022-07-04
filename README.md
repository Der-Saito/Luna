# Luna Engine

## Definition
Mit der Luna Engine ist es möglich einfache bis recht komplexe Web-Applikationen im Bauksten-Prinzip nach dem Observer Design Pattern zu erstellen ohne tiefgehende Kenntnisse in den folgenden Sprachen zu besitzen und der OOP.
- PHP
- MySQL
- HTML
- Javascript
- Smarty
- Jquery
- CSS3
- Bootstrap

## Aufbau

### Allgemein
Es handelt sich um eine recht simple MCV-Applikationen, die sehr stark reduziert wurde und daher auch nicht über allzuviele Sicherheitsvorkehrungen verfügt. Daher sollte die Luna Engine **niemals** öffentlich zugänglich sein. Die erzeugten Projekte hingegen besitzen diese Vorkehrungen um vor XSS und SQL-Injections zu schützen, desweiteren besitzt jeder Controller und Aktion ein gewisses "Sicherheitslevel" um auch gewisse Aktionen die zu einem Controller gehören für etwaige Fälle öffentlich zugänglich machen zu können.
Einfach dargstellt durchläuft jede Applikation die mit Luna erstellt wurde folgenden Workflow
1. Request > Händelt die GET/POST Anfragen und validiert übergebene Parameter.
2. Router > Ermittelt den richtigen Controller und seine Aktion und übergibt die validierten Daten an den Controller.
3. Controller > Prüft ob der Zugriff erlaubt ist, wenn ja wird die angefragte Aktion ausgeführt und gibt sein Ergebnis an Response weiter.
4. Response > Setzt jenach Ergebnis des Controllers den entsprechenden HTTP Response-Code
5. Controller > Lädt das Template und rendert die Anzeige, wenn der Response-Code 200 ist.

### ORM Builder
Diese Klasse (stark angelehnt an **Doctrine**) hat 2 Hauptfunktionen.
1. Erschafft durch den Zugriff auf die Datenbank *informations_schema* unter repositories/models/ die gesamte Datenbankabstraktionsschicht.
2. Erschafft auf Basis der Beziehungen zwischen den Tabellen größere Repositorities unter repositories/**Name**
> Hier ist zu beachten das Name den kleinsten gemeinsamen Teilbereich verwandter Tabellen darstellt und hierfür einen eigenen Ordner kreiert.
> **WICHTIG** Die so geschaffenen Repositories haben automatisch Zugriff auf die entsprechenden Tabellen und die Funktionen sind an Doctrine angelehnt. Desweiteren geben diese Das gesamte Bezeihungsgebilde wieder und geschaffene **Uniques** im Datenbank Design sind als Funktion ebenfalls verfügbar mit ihrem Namen.
