# Prepared-Statements
Bei Prepared-Statements wird das Statement zuerst vorbereitet und erst dann ausgeführt.
Durch Prepared-Statements können SQL Injeections verhindert werden. 

## Ablauf
1. Eine SQL-Anweisungsvorlage wird erstellt und an die DB gesendet. Werte werden nicht angegeben und als Parameter bezeichnet``:platzhalter``.
2. Die Datenbank analysiert, kompiliert und führt eine Abfrageoptimierung für die SQL-Anweisungsvorlage durch und speichert das Ergebnis, ohne es auszuführen.
3. Zu einem späteren Zeitpunkt bindet die Anwendung die Werte an die Parameter, und die DB führt die Anweisung aus.

# Prepared-Statements vs traditioneller Zugriff

## traditioneller Zugriff
In unserem fall verwenden wir PDO welches rein OOP ist und denn Datenbankzugriff auf unterschieliche SQL-basierte Datenbanken ermöglicht, wie zum Beispiel MySQL, PostgreSQL oder SQLite.
````php
<?php
public function get_klasseFilterID($id)
    {
        $this->db->query("SELECT * FROM klasse WHERE klasse_id = $id");
        $results = $this->db->single();

        return $results;
    }
````

## Prepared-Statements in php
````php
<?php
public function get_klasseFilterID($id)
    {
        $this->db->query("SELECT * FROM klasse WHERE klasse_id = :id");
        $this->db->bind(':id', $id);
        $results = $this->db->single();

        return $results;
    }
````

Im ersten Beispiel wird der Parameter direkt angegeben und ausgeführt. Beim Prepared-Statement haltet man den Parameter mit einem Platzhalter `:id` frei.
Mit `bind(':id', $id);` wird der Platzhalter dann ersetzt. 
Dadurch das beim Prepared-Statement der Parameter validiert wird, wird eine SQL injection verhindert.