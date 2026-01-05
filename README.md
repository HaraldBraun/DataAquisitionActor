# DataAquisitionActor
Data aquisition from DAQmx devices with Actor Framework

## Ziel der Entwicklung
Das Ziel der Entwicklung ist es, eine Applikation zu erstellen, die mit dem Actor Framework von National Instruments aufgebaut wird.

---

## Rahmenbedingungen
### Geraete
Es soll moeglich sein, Daten von Sensoren aufzunehmen, welche mit einem DAQmx-System von National Instruments verbunden sind.  
Zur Datenaufzeichnung werden folgende Geraete in der Applikation zur Verfuegung stehen:  
* Spannungsversorgung (DCPower)
* CAN 

### Software
Die Software stellt die folgenden Untereinheiten zur Verfuegung:  
* **Datenaufzeichung**
    * TDMS
    * CSV
    * Datenbank (MySQL, MariaDB, MS SQL)
* **Datenerfassung**  
    * DAQmx
    * CAN
* **Spannungsversorgung**  
    * DC Power
* **User Interface**  
    * Einstellungen
        * Wohin wird gespeichert?
        * Welche Schnittstelle wird vom UUT verwendet?
        * Welches Aufnahmeintervall wird benoetigt?
        * Welche Spannung wird benoetigt? 
    * Datenanzeige
        * Anzeige als Graph
            * Auswahl der Graphwerte
            * Auswahl der Kanaele zur Anzeige
        * Anzeige der Werte als Tabelle
            * Gleicher Wert ueber alle Kanaele
            * Ein Kanal mit allen Werten zum UUT

## Beschreibung des Ablaufs in der Applikation
Das Start-VI (launcher) startet den Root-Actor (Controller). Dieser ruft das Main User Interface auf. Dieses enthaelt als Hauptelement ein Sub-Panel in dem alle weiteren Sub-User Interfaces angezeigt werden.

---

## Aufbau der User Interfaces
### Main User Interface
Die Aufteilung des Main-UI wird im Borderlayout stattfinden. Dazu wird folgende Einteilung vorgenommen:  
* **North**  
Der Bereich wird unterteilt mit einem GridLayout aus 3 Spalten und zwei Zeilen (3 x 2).  
Der Hauptbereich in der Mitte bekommt zentriert den Applikationsnamen. Die Bereiche links und rechts davon werden mit gleicher Groesse erstellt. Der Linke Bereich wird das [Icon](Ressources/Images/ModulareSensorHexagon.png) der Applikation enthalten, im rechten Bereich wird das [Logo](Ressources/Images/logo-hb-signal.svg) des Applikationsentwicklers angezeigt.  
In der zweiten Zeile werden die Buttons zur Auswahl des anzuzeigenden User Interfaces untergebracht inklusive Stop-Button.

* **South**  
Am unteren Rand der Applikation wird es eine Statusanzeige (String-Field) geben. In der rechten unteren Ecke wird ein kleines Feld das aktuelle Datum und die Uhrzeit anzeigen. Eventuell kann dieses Feld noch um die Versionsnummer der Applikation erweitert werden.

* **Center**  
Hier wird nur ein Sub-Panel enthalten sein. Dieses Sub-Panel wird in Abhaengigkeit des aktuellen Zustandes entsprechend mit weiteren User Interfaces belegt. Zu Beginn wird das User Interface mit den Einstellungsoptionen angezeigt. Wenn die Einstellungen vorgenommen und verifiziert sind, wird das User Interface fuer die Datenanzeige angezeigt.

---

## Diagramme
Die Diagramme, welche die Software abbilden sind hier verlinkt.  
[Klassendiagramm](Documentation/Classes.md)    
[Sequenzdiagramm](Documentation/Sequences.md)
