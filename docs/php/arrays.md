### Arrays
````php
<?php
// Das ist ein Array
$wochentage = array("Sonntag","Montag","Dienstag",
"Mittwoch","Donnerstag","Freitag");

// Dieser Wert wird nachträglich dem Array hinzugefügt.
// Dabei wird automatisch ein neuer Array erstellt mit dem neuen Wert
$wochentage[] = "Samstag";

echo $wochentage[1];

/* Ausgabe:
Montag
*/
?>
````
!!! Tip
    Die Position *0* ist die *erste* Position.


#### Assoziative Arrays
Anstelle von Nummern/Indexe kann man auch mit Keys arbeiten, das sind assoziative Arrays.

````php
<?php
// Das ist ein assoziativer Array
$wochentage = array(
"so" => "Sonntag",
"mo" => "Montag",
"di" => "Dienstag",
"mi" => "Mittwoch",
"do" => "Donnerstag",
"fr" => "Freitag",
"sa" => "Samstag");

// Dieser Wert wird nachträglich dem Array hinzugefügt.
$wochentage["sa"] = "Samstag";

echo $wochentage["mo"];

/* Ausgabe:
Montag
*/
?>
````

#### Arrays in Strings konvertieren
Mit ``implode($trennzeichen, $array)`` können Elemente eines Array zu einem String verbunden werden.

````php
<?php
$namen = array("Paul", "Max", "Hans");

echo "Namen per Komma trennen: <br>";
$namenStr = implode(", ", $namen);
echo $namenStr; 

echo "<br><br>";
echo "Ein Name pro Zeile: <br>";
echo implode("<br>", $namen);

/* Ausgabe:
Namen per Komma trennen:
Paul, Max, Hans

Ein Name pro Zeile:
Paul
Max
Hans
*/
?>
````

#### Strings in Arrays konvertieren
Im Gegensatz zu ``implode()``  lässt sich mittels ``explode($trennzeichen, $text)``  ein Text (String) in ein Array konvertieren.

````php
<?php
$text = "Paul,Max,Hannes";
$namen = explode(",", $text ); //Konvertierung des Strings in ein Array
echo "<pre>"; var_dump($namen); echo "</pre>"; //Formartierte Ausgabe des Arrays


//Ersetze die 1. Person durch neuen Namen
$namen[1] = "Lisa";

//Verwandel das Array zurück in einen String
$text = implode(", ", $namen);
echo $text;

/* Ausgabe:
array(3) {
  [0]=>
  string(4) "Paul"
  [1]=>
  string(3) "Max"
  [2]=>
  string(6) "Hannes"
}
Paul, Lisa, Hannes
*/
?>
````

#### Mehrdimensionale Arrays
In einem Array können belibig weitere Arrays gespeichert werden.
````php
<?php
$mitarbeiter = array();
$mitarbeiter[] = array("Vorname"=>"Klaus",
                       "Nachname"=>"Zabel");

$mitarbeiter[] = array("Vorname"=>"Arnie",
                       "Nachname"=>"Meier");

$mitarbeiter[] = array("Vorname"=>"Willi",
                       "Nachname"=>"Brand");

//Daten ausgeben
echo "Vorname: ".$mitarbeiter[0]["Vorname"];
echo " Nachname: ".$mitarbeiter[0]["Nachname"];
?>
````

#### Arrays durchsuchen
Mittels ``in_array($suche,$array)`` Arrays durchsuchen.

````php
<?php
$mitarbeiter = array("Bob","Peter","Lisa");
$name = "Bob";
if(in_array($name,$mitarbeiter)) {
   echo "Der Name $name ist in dem Array enthalten";
}
?>
````

#### Array sortieren
Arrays lassen sich mittels der Funktion ``sort()``  aufsteigend sortieren (a nach z). Mittels der Funktion ``rsort()``  lässt sich ein Array absteigend sortieren (z nach a).

!!! Tip
    - ``array_key_exists($key, $array)`` : Überprüft, ob der Schlüssel $key im $array existiert.
    - ``count($array)`` : Gibt die Anzahl der Elemente im Array zurück.
    - ``in_array($suchwert, $array)`` : Überprüft, ob der Wert $suchwert im $array existiert.
    - ``sort($array)`` : Sortiert ein Array aufsteigend, vom kleinsten zum größten Wert (A -> Z).
    - ``rsort($array)`` : Sortiert ein Array absteigend, vom größten zum kleinsten Wert (Z -> A).
    - ``shuffle($array)`` : Mischt zufällig die Elemente des Arrays.