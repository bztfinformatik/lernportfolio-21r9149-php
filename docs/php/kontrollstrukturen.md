# Strukturen

## If-Anweisungen

````php
<?php
if(Bedingung) 
   {
   Anweisung
   } 
else 
   {
   Anweisung
   }
?>
````
## Vergleichsoperatoren

| Operator      |   Name                               | Erläuterung |
| --------------| ------------------------------------ |-------------|
| ``$a == $b``  | Gleich          | Dieser Vergleich ist erfüllt, falls ``$a`` und ``$b`` den selben Wert beinhaltet. Sind die Typen der Variablen verschieden, so werden die konvertiert. |
| ``$a === $b`` | Identisch       | Dieser Vergleich ist erfüllt, falls ``$a`` und ``$b`` den selben Typ und den Inhalt besitzen. Wäre ein Wert vom Typ ``int`` und der andere from Typ ``String``, so würde false zurück gegeben werden.| 
| ``$a != $b``  | Ungleich        | Dieser Vergleich ist erfüllt, falls ``$a`` und ``$b`` nicht den selben Wert beinhaltet. Sind die Typen der Variablen verschieden, so werden die konvertiert.| 
| ``$a !== $b`` | Nicht identisch | Dieser Vergleich ist erfüllt, falls ``$a`` und ``$b`` einen unterschiedlichen Typ haben oder einen unterschiedlichen Wert.| 
| ``$a < $b``   | Kleiner         | ``$a`` muss kleiner als ``$b`` sein.|
| ``$a <= $b``  | Kleiner Gleich  | ``$a`` muss kleiner oder gleich ``$b`` sein.|
| ``$a > $b``   | Grösser         | ``$a`` muss größer als ``$b`` sein.|
| ``$a >= $b``  | Grösser Gleich  | ``$a`` muss größer oder gleich ``$b`` sein.|

!!! Tip
    Die Funktion ``strpos($text, $suchwort)``  gibt die Position des ``$suchwort`` im ``$text`` zurück. Sollte es nicht gefunden werden, so wird ``false`` zurückgegeben. Nun kann ``strpos()`` aber auch Position *0* zurückgeben, sollte das Suchwort zu Beginn des Textes stehen.

## Logische Operatoren

````php
<?php 
$username = "Nils"; 
$passwort = "php-einfach"; 
if($username == "Nils" AND $passwort == "php-einfach") # (1)
{ 
   echo "Beide Bedingungen waren erfüllt - Zugriff erlaubt. <br />"; 
} 

if($username == "Nils" OR $passwort == "php-einfach") { # (2)
  echo "Eine oder beide Bedingungen waren erfüllt.";
}
?> 
````

1.  Bei ``AND`` (alternativ `&&`) müssen beide Bedinungen zutreffen.
2.  Bei ``OR`` (alternativ `||`) muss nur einer der beiden Bedingungen zutreffen.

## Schleifen

### While-Schleife

````php
<?php
while(Bedingung) {
   Anweisungen
}
?>
````

### Do-Whilfe-Schleife
````php
<?php
do {
   Anweisungen
} while(Bedingung);
?>
````

### For-Schleife
````php
<?php
for(Startwert; Bedingung; Schleifenschritt) {
   Anweisungen
}
?>
````

!!! TIP
    Wie bei der **while-Schleife** lassen sich bei der **for-Schleife** der Schleifenablauf durch die Befehle ``break``  und ``continue``  beeinflussen. Mittels ``break``  wird dabei der weitere Schleifendurchlauf unterbrochen und mittels ``continue``   wird ein Schleifendurchlauf übersprungen:`

    === "break"
        
        ````php
        <?php
        for($i=0; $i < 20; $i++) {
            if($i == 13) {
                echo "Dreizehn ist eine Unglückszahl!!! <br>";
                break; # (1)
            }

            echo "$i, ";
        }
        ?>
        ````

        1.  Die Break-Anweisung hält den gesamten Ablauf der Schleife an.

    === "continue"
        
        ````php
        <?php
        for($i=0; $i < 20; $i++) {
            if($i == 13) {
                echo "Dreizehn ist eine Unglückszahl!!! <br>";
                continue; # (1)
            }

            echo "$i, ";
        }
        ?>
        ````

        1. Die Continue-Anweisung hält nur die aktuelle Iteration der Schleife an.