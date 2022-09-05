# PHP und Datentypen

``` php
<?php
echo 2 + 4.3; # (1)
echo "<br/>";

echo "22manjunath" + 22; # (2)
echo "<br/>";

echo 2 * "4a" # (3)
echo "<br/>";

echo 2 * "a2"; # (4)
echo "<br/>";

echo 4 * 2.5; # (5)
echo "<br/>";

echo "2" + "2"; # (6)
echo "<br/>";
?>
```

1.  2.0 + 4.3 = 6.3 <br>
    ``int`` und ``float``: Umwandlung in ``float``.

2.  22 + 22 = 44 <br>
    Die Zahl 22 wird aus dem ``String`` entnommen und zu einem ``int`` umgewandelt.

3.  2 * 4 = 8 <br>
    Die Zahl 4 wird aus dem ``String`` entnommen und zu einem ``int`` umgewandelt.

4.  2 * 0 = 0 <br>
    Wenn die Zahl nicht an erster Stelle steht kann funktioniert die Addierung nicht.

5.  4.0 * 2.5 = 10.0
    ``int`` und ``float``: Umwandlung in ``float``.

6.  2 + 2 = 4
    Die Zahl 2 wird aus beiden ``Strings`` zu einem ``int`` umgewandelt.

!!! warning
    PHP gibt vor keine Datentypen zu kennen. Im hintergrund werden jedoch Datentypen verwendet. Das nicht deklarieren kann zu Problemen führen.

!!! Tip
    Mit ``var_dump()`` kann man den Datentyp einer Variable überprüfen.

!!! info inline end "Ausgabe"
    string(3) "100"
    int (100)

```` php
<?php
$a = '100';
$b = (int)$a;
var_dump($a, $b);
?>
````