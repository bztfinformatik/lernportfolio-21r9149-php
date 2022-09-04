# Tag 1

## Inhaltsverzeichnis
1. [Behandelte Themen](#Behandelte_Themen)
2. [Learnings](#Learnings)

## Behandelte Themen
Auf dem Wissen der letzten Lektion aufbauend haben wir heute mit dem ersten Basisprojekt gestartet. Im Plenum haben wir die Struktur und funktionsweise mit Docker besprochen und getestet.<br>
Im [php-einfach](https://www.php-einfach.de/) Skript haben wir die Kapitel [Rechnen mit Variablen](https://www.php-einfach.de/php-tutorial/rechnen-mit-variablen/), [$_GET und $_POST](https://www.php-einfach.de/php-tutorial/_get-und-_post/) und [Arrays](https://www.php-einfach.de/php-tutorial/php-array/) durchgearbeitet. Das wichtigste zu den Kapitel habe ich unter [PHP-Grundlagen](/tag002/php-grundlagen.md) Dokumentiert.

Um das aus dem Skript erlernte, anzuwenden haben wir den ersten [Programmierauftrag](/tag002/programmierauftrag.md.md) gelöst.


## Learnings
Das meiste aus den Kapiteln [Rechnen mit Variablen](https://www.php-einfach.de/php-tutorial/rechnen-mit-variablen/) und [$_GET und $_POST](https://www.php-einfach.de/php-tutorial/_get-und-_post/) war mir aus früheren Modulen bekannt. Beim Arbeiten mit Array habe ich bestimmte Paralellen zu anderen Programiersprachen geshen bei welchen der syntax einfach anders ist. Neu für mich waren funktionen wie ``implode()``, ``in_array()`` usw.

>[!TIP]
>**Nützliche Array Funktionen**
> - ``array_key_exists($key, $array)`` : Überprüft, ob der Schlüssel $key im $array existiert.
> - ``in_array($suchwert, $array)`` : Überprüft, ob der Wert $suchwert im $array existiert.
> - ``sort($array)`` : Sortiert ein Array aufsteigend, vom kleinsten zum größten Wert (A -> Z).
> - ``rsort($array)`` : Sortiert ein Array absteigend, vom größten zum kleinsten Wert (Z -> A).
> - Mehrdimensionale Arrays:
> ````php
><?php
>$mitarbeiter = array();
>$mitarbeiter[] = array("Vorname"=>"Klaus",
>                       "Nachname"=>"Zabel");
>$mitarbeiter[] = array("Vorname"=>"Arnie",
>                       "Nachname"=>"Meier");
>$mitarbeiter[] = array("Vorname"=>"Willi",
>                       "Nachname"=>"Brand");
>//Daten ausgeben
>echo "Vorname: ".$mitarbeiter[0]["Vorname"];
>echo " Nachname: ".$mitarbeiter[0]["Nachname"];
>?>
>````