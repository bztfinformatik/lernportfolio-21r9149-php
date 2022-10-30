# Abgabe 1

## Architekturkonzept - allgemein

### MVC
Beschreibung zu MVC -> [hier](http://localhost:8000/php/mvc/)

### Twig
Beschreibung zu Twig -> [hier](http://localhost:8000/php/twig_template/)

### SSR
Beschreibung zu SSR -> [hier](http://localhost:8000/appendix/SSR_%26_CSR/)

## Architekturkonzept - angewendet

### Aufgabenstellung / Skizze

**Schüler/Lehrmeister/Lehrperson - Komunikations/Austausch-Software**

Die Klassenlehrperson hat beispielsweise mehrere Klassen mit den entsprechenden Schüler. Jeder Schüler gehört zu einem Lehrmeister. Die Software dient zur Komunikation zwischen den Parteien. Eine Lehrperson kann so beispielsweise so direkt eine Meldung an alle Lehrmeister einer Klasse machen und entscheiden ob der Schüler diese Meldung auch erhalten soll. Neben Text soll auch ein Fileupload möglich sein. Vor dem abschicken der Nachricht kann man auswählen ob der Empfänger das Lesen der Nachricht bestätigen muss oder nicht. Die Lehrperson soll eigene Gruppen erstellen können damit er die Personen nicht jedes mal einzeln auswählen muss.
<br>
Der Aufbau des Formulars sollte ähnlich wie diese Skizze aussehen:

<img src="/assets/skizze.png" alt="Skizze" width="1000"/> 
[*Eigene Skizze*]()

### MVC anwendung

Die untere auflistung dient als grobe Übersicht welche sich im Verlauf des Projekt noch ändern kann.

#### Controller
- HomeController
- LoginController
#### Model
- User
- Nachracht
- Gruppe
#### View
- HomeAdmin
- HomeLehrmeister
- HomeLehrer
- HomeSchüler
- Formular neue Nachricht
- AlteNachricht

### Twig anwendung
- Baselayout
    - Footer
    - Header
    - Nachrichten auflistung
- Nachricht geöffnet
- Formular neue Nachricht

## Use-Cases, Akteure und Diagramm

### Use-Cases
| ID                   | UC-001                                                          |
|----------------------|-----------------------------------------------------------------|
| Name                 | Anmeldung                                                       |
| Ziel                 | Ein Benutzer kann sich mit seinem Benutzer anmelden             |
| Essenzielle Schritte | - Login View - Benutzer bereits erstellt - Passwort Überprüfung |

| ID                   | UC-002                                                             |
|----------------------|--------------------------------------------------------------------|
| Name                 | Nachricht erstellen                                                |
| Ziel                 | Ein Benutzer kann eine Nachricht erstellen                         |
| Essenzielle Schritte | - Home View - Button ruft Formular auf - Funktionierendes Formular |

| ID                   | UC-003                                                                            |
|----------------------|-----------------------------------------------------------------------------------|
| Name                 | Nachricht antworten / Bestätigen                                                  |
| Ziel                 | Benutzer kann auf eine Nachricht antworten oder bestätigen das er sie gelesen hat |
| Essenzielle Schritte | - UC-002 - Nachrichten empfangen funktioniert                                     |

| ID                   | UC-004                                                |
|----------------------|-------------------------------------------------------|
| Name                 | Nachrichten an Gruppen senden                         |
| Ziel                 | Benutzer kann eine Nachricht an ganze Gruppen senden  |
| Essenzielle Schritte | - Eigene/Vorgefertigte Gruppen erstellen - UC-001-003 |

| ID                   | UC-005                                       |
|----------------------|----------------------------------------------|
| Name                 | Fileupload                                   |
| Ziel                 | Benutzer kann ein File als Anhangverschicken |
| Essenzielle Schritte | - Fileupload                                 |

### Akteure
- Admin
- Lehrmeister
- Schüler
- Lehrperson

### Diagramm
<img src="/assets/Diagramm Use-Cases.png" alt="Diagramm" width="1000"/> 
[*Mit Plantuml erstellt*](https://plantuml.com/de/use-case-diagram)

## Funktionale Anforderungen
- Alle Benutzer können sich anmelden
- Benutzer können Nachrichten verschicken
- Benutzer die eine Nachricht erhalten können darauf antworten und wenn nötig bestätigen das Sie es gelesen haben
- Ein Benutzer kann eigene Gruppen erstellen und an diese eine Nachricht senden.
- Files können im Anhang einer Nachricht mitgesendet werden.

## Testszenarios
| Use-Case | Testszenario                                                                                 |
|----------|----------------------------------------------------------------------------------------------|
| UC-001   | User: test.Lehrer PW: Test@123  Versuchen anzumelden                                         |
| UC-002   |  Nachricht von test.Lehrer an test.Lehrmeister                                               |
| UC-003   | test.Lehrmeister muss auf die nachricht antworten und bestätigen das er sie gelesen hat      |
| UC-004   | test.lehrer erstellt eine Gruppe IN2021b und verschickt den Schuelern eine Nachricht.        |
| UC-005   | Nachricht mit einem PDF im Anhang verschicken. Die andere seite Soll das File öffnen können. |