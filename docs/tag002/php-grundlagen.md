# Inhaltsverzeichnis
> - [PHP-Grundlagen](#php-grundlagen)
>   - [Rechnen mit Variablen](#rechnen-mit-variablen)
>   - [$_GET und $_POST](#get-und-post)
>       - [Datenübergabe mittels $_GET](#datenübergabe-mittels-get)
>       - [Datenübergabe mittels $_POST](#datenübergabe-mittels-post)
>       - [$_Post und $_GET zusammen](#post-und-get-zusammen)
>       - [$_POST oder $_GET](#post-oder-get)
>   - [Arrays](#arrays)
>       - [Assoziative Arrays](#assoziative-arrays)
>       - [Arrays in Strings konvertieren](#arrays-in-strings-konvertieren)
>       - [Strings in Arrays konvertieren](#strings-in-arrays-konvertieren)
>       - [Mehrdimensionale Arrays](#mehrdimensionale-arrays)
>       - [Arrays durchsuchen](#arrays-durchsuchen)
>       - [Arrays sortieren](#array-sortieren)


## PHP-Grundlagen

### Rechnen mit Variablen

**Rechnungsbeispiele:**
````php
<?php
$zahl1 = 10;
$zahl2 = 5;
echo $zahl1 + $zahl2; //addieren
echo "<br />";
echo $zahl1 - $zahl2; //subtrahieren
echo "<br />";
echo $zahl1 * $zahl2; //multiplizieren
echo "<br />";
echo $zahl1 / $zahl2; //dividieren
echo "<br />";
echo pow($zahl1,$zahl2); //Zahl1 hoch Zahl2 (10^5)
echo "<br />";
echo sqrt(64); // Wurzel von 64
echo "<br />";
echo 2*$zahl1 + 5*$zahl2 - 3; //Berechnet 2*10 + 5*5 - 3

````
### $_GET und $_POST

Um Werte von einer Seite zur nächsten zu **übertragen** werden in den meisten Fällen die speziellen Variablen ``$_GET`` und ``$_POST`` verwendet.

#### Datenübergabe mittels $_GET
Bei ``$_GET`` werden die Variablewerte mittels der URL übergeben. Die Variablen werden mit dem Zeichen ``?`` an die *URL* angehängt.
<br>

**Beispiel:**

````
http://www.domain.de/index.html*?name1=wert1
````
Es können auch mehrere Parameter übermittelt werden.
Diese werden mit dem Zeichen ``&`` voneinander getrennt.

````
http://www.domain.de/index.html*?name1=wert1&name2=wert2
````

Code:
````php
<?php
$variable1 = $_GET['name1'];
$variable2 = $_GET['name2'];
echo "$variable1 $variable2";
?>
````

#### Datenübergabe mittels $_POST
Im Gegensatz zu $_GET werden $_POST-Variablen nicht per URL, sondern per Formular übertragen.

**Beispiel:**
*Seite1.php*
````php
<form action="seite2.php" method="post">
Vorname: <input type="text" name="vorname" /><br />
Namename: <input type="text" name="nachname" /><br />
<input type="Submit" value="Absenden" />
</form>
````
Mit ``action`` definiert man die Zielseite. Mit ```Method`` die Methode.

>[!WARNING]
>Es ist wichtig, dass alle Eingabefelder einen **einzigartigen** Namen zugewiesen haben, damit die Daten korrekt abgefragt werden können.

Auf der *seite2.php* können die Daten des Formulares wie folgt abgerufen werden:
````php
<?php
$vorname = $_POST["vorname"];
$nachname = $_POST["nachname"];
echo "Hallo $vorname $nachname";
?>
````

#### $_Post und $_GET zusammen

``$_Post`` und ``$_GET`` können auch zusammen verwendet werden.<br>
**Beispiel:**
*Seite1.php*
````php
<form action="seite2.php?wochentag=Sonntag" method="post">
Vorname: <input type="text" name="vorname" /><br />
Namename: <input type="text" name="nachname" /><br />
<input type="Submit" value="Absenden" />
</form>
````

Neben dem Formular wird zusätzlich noch eine ``GET-Variable`` übergeben *(wochentag=Sonntag)*.

*Seite2.php*
````php
<?php
$vorname = $_POST["vorname"];
$nachname = $_POST["nachname"];
$wochentag = $_GET["wochentag"];

echo "Hallo $vorname $nachname. Treffen wir uns am $wochentag?";
?>
````

#### $_POST oder $_GET
**$_POST**
- Wenn man Eingaben aus einem **Formular** übergeben möchte, so sollte man immer **POST** benutzen.

**$_GET**
- GET wird benutzt, wenn man **einfache Informationen** übergeben möchte. Soll zum Beispiel mit dem Klick auf einen Link eine Auswahl übergeben werden, so benutzt man die Methode **GET**.

``<a href="artikel.php?id=234">Das PHP Einsteiger Buch</a>``

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

>[!TIP]
> Die Position *0* ist die *erste* Position.

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

>[!TIP]
>**Nützliche Array Funktionen**
> - ``array_key_exists($key, $array)`` : Überprüft, ob der Schlüssel $key im $array existiert.
> - ``count($array)`` : Gibt die Anzahl der Elemente im Array zurück.
> - ``in_array($suchwert, $array)`` : Überprüft, ob der Wert $suchwert im $array existiert.
> - ``sort($array)`` : Sortiert ein Array aufsteigend, vom kleinsten zum größten Wert (A -> Z).
> - ``rsort($array)`` : Sortiert ein Array absteigend, vom größten zum kleinsten Wert (Z -> A).
> - ``shuffle($array)`` : Mischt zufällig die Elemente des Arrays.