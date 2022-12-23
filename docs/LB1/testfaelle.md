# Testfälle

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

# Testprotokoll

| ID     | Bezeichnung                      | Testdatum  | Tester         | Bemerkung                                                                                                                     | Status |
|--------|----------------------------------|------------|----------------|-------------------------------------------------------------------------------------------------------------------------------|--------|
| UC-001 | Anmeldung                        | 23.12.2022 | Joaquin Koller | Test erfolgreich. Test mit dem Benutzer joaquin.koller.                                                                       | ❎      |
| UC-002 | Nachricht erstellen              | 23.12.2022 | Joaquin Koller | SQL fehler wenn man die Nachricht nur an den Benutzer oder Gruppe sendet.                                                     |        |
| UC-002 | Nachricht erstellen              | 23.12.2022 | Joaquin Koller | Test erfolgreich.                                                                                                             | ❎      |
| UC-003 | Nachricht antworten / Bestätigen | 23.12.2022 | Joaquin Koller | Bedingt erfolgreich. Auf Nachrichten kann man nicht Antworten, man kann aber bestätigen, dass man eine Nachricht gelesen hat. | ✖      |
| UC-004 | Nachrichten an Gruppen senden    | 23.12.2022 | Joaquin Koller | Der Test war erfolgreich. Die Empfänger sind nur Schüler,  da die Gruppen Klassen darstellen.                                 | ❎      |
| UC-005 | Fileupload                       | 23.12.2022 | Joaquin Koller | Wurde aus Zeitgründen nicht eingeführt                                                                                        | ❌      |
