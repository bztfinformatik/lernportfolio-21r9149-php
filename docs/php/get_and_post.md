# $_GET und $_POST

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

!!! warning
    Es ist wichtig, dass alle Eingabefelder einen **einzigartigen** Namen zugewiesen haben, damit die Daten korrekt abgefragt werden können.


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
