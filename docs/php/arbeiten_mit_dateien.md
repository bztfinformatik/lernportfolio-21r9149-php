# Arbeiten mit Dateien

## Dateien lesen
Um Dateien auszulesen gibt es die funktion ``file_get_contents()`` und ``file()``. 

### file_get_contents()
Im unterefen Beispiel wird der gesamte Inhalt der Datei ``zitate.txt`` in die Variable ``$zitate`` gespeichert.
````php
<?php
$zitate = file_get_contents('zitate.txt');
echo $zitate;
?>
````

Wenn man den Inhalt nun aber im HTML ausgibt wird alles auf einer Zeile geschriben. Das liegt daran das die Umbrüche in HTML als ``<br>`` angegeben werden müssen.

````php
<?php
$zitate = file_get_contents('zitate.txt');
echo nl2br($zitate);
?>
````
Mit ``nl2br()`` werden die Zeilenbrüche *(new lines)* zu Html-Zeilenumbrüche ``<br>`` umgewandelt.

### file()
Mit ``file()`` wird der Inhalt zeilenweise ausgelesen und speichert jede Zeiel in ein Array-Element.

````php
<?php
$zitate = file("zitate.txt");
for($i=0;$i < count($zitate); $i++){
   echo $i.": ".$zitate[$i]."<br><br>";
}
?>
````

## Dateien schreiebn

### Dateien überschreiebn
Mittels ``file_put_contents()`` kann der Inhalt einer Datei überschrieben werden.
````php
<?php
$name = $_GET["name"];
$zeile = "Per GET wurde der Name $name übergeben \r\n";
file_put_contents("beispiel.txt", $zeile);
echo "beispiel.txt wurde überschrieben";
?>
````

### Text an Datei anhängen
Möchte man eine Datei nicht überschreiben, sondern Wert an die Datei anhängen, so muss man der Funktion ``file_put_contents()`` als drittes Argument die Konstante ``FILE_APPEND`` übergeben.

````php
<?php
$name = $_GET["name"];
$zeile = "Per GET wurde der Name $name übergeben \r\n";
file_put_contents("beispiel.txt", $zeile, FILE_APPEND);
echo "beispiel.txt aktualisiert";
?>
````

