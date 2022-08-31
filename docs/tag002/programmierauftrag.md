# 1 Programmierauftrag

> - Gegeben ist der Array aus den Werten 3,7,5,1,8,13,2.
> - Erstellen Sie ein PHP-Script welches die Werte aus dem Array in einer HTML-Tabelle ausgibt

**Lösung:**
````php
<?php
$zahlen = array(3, 7, 5, 1, 8, 13, 2);
echo "<table>";
echo "<tr>";
foreach ($zahlen as $zahl) {
   echo "<td>" . $zahl . "</td>";
   }
echo "</tr>";
echo "</table>";
?>
````
