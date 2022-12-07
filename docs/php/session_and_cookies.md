# Sessions
Wir wollen uns auf dem Webserver die “Kunden” merken können

HTTP ist ein zustandsloses Protokoll, das bedeutet, Informationen werden zwischen den verschiedenen Aufrufen eines Besuchers nicht zwischengespeichert. Dies ist natürlich unpraktisch wenn wir gewisse Informationen zu einem Besucher speichern müssen, beispielsweise mit welchem Benutzernamen sich dieser eingeloggt hat. Um dies zu lösen, verwendet man in PHP Sessions

## 3 Varianten von Sessions

1. Die Session-ID wird jeweils über die URL mitgegeben (GET) <- !gar nicht gut!
2. Die Session-ID wird jeweils mittels POST mitgegeben <- !nicht gut!
3. Die Session-ID wird in einem Cookie gespeichert

## Anwendung

**Session Starten:**
```php
<?php
session_start();
?>
```

**Werte auf die Session setzen:**
```php
<?php
$_SESSION['name'] = "wert";
?>
```

**Session löschen / Werte löschen**
````php
<?php
session_destroy(); // Session löschen...alles
unset($_SESSION['name']); // Wert löschen
?>
````

## Beispiel

=== "login.php"

    ````php
    <?php
    session_start(); //Nicht vergessen
    $name = $_POST['name'];
    
    if(!isset($name) OR empty($name)) {
       $name = "Gast";
    }
    
    //Session registrieren
    $_SESSION['username'] = $name;
    
    //Text ausgeben
    echo "Hallo $name <br />
    <a href=\"seite2.php\">Seite 2</a><br />
    <a href=\"logout.php\">Logout</a>";
    ?>
    ````

=== "logout.php"

    ````php
    <?php
    session_start();
    session_destroy();
    echo "Logout erfolgreich";
    ?>
    ````

=== "seite2.php"

    ````php
    <?php
    session_start(); //Ganz wichtig
    
    if(!isset($_SESSION['username'])) {
       die("Bitte erst einloggen"); //Mit die() beenden wir den weiteren Scriptablauf   
    }
    
    //In $name den Wert der Session speichern
    $name = $_SESSION['username'];
    
    //Text ausgeben
    echo "Du heißt immer noch: $name
    <a href=\"logout.php\">Logout</a>";
    ````

=== "formular.html"

    ````html
    <form action="login.php" method="post">
        Dein Name: <br />
        <input type="Text" name="name" />
        <input type="Submit" />
    </form>
    ````

# Cookies
Wir wollen uns auf dem Client Dinge speichern können.

Cookies werden ähnlich wie **Sessions** dazu verwendet um Daten während einer Folge von Aufrufen einer Website festzuhalten.
Allerdings können die Daten über die Sitzung hinaus auf den Client gespiechert werden. Zum Beispiel 100 Tage nach der Speicherung.

## Anwendung
**Cookies setzen**
````php
<?php
setcookie("username","Max",0); // Gültig bis Ende der Sitzung
setcookie("username","Max",time()+(3600*24)); // Gültig bis : aktueller Zeitpunkt plus 24h
?>
````

**Cookie auslesen**
````php
<?php
$cookie = $_COOKIE["username"];
echo "Der Inhalt des Cookies: $cookie";
````
**Cookie löschen**
````php
<?php
setcookie("username","",time() - 3600);
````

# Auftrag
!!! abstract "Formular Bier Auftrag"
    Für eine Homepage sollen Sie einen Gäste-Zähler erstellen, welche die Anzahl Aufrufe der Seite jeweils ausgibt.
    Dabei soll aber verhindert werden, dass jemand durch Aktualisieren des Browserfensters den Zähler erhöhen kann.

    Folgende Vorgaben sind einzuhalten: <br>
    - Arbeiten Sie mit ``Sessions``
    - Der Zählerstand soll in ein File geschrieben werden
    - Erst durch Schliessen des Browsers darf beim nächsten Zugriff darf der Zähler erhöt werden.
    Zugabe: <br>
    - 

??? success "Lösung"

    ### Formular

    === "Auftrag"

        ````php
        <?php
        // Startet die Session
        session_start();

        // liest das File aus
        $count = (int) file_get_contents('./count.txt'); 

        // Überprüfen ob Session-Variable registriert ist
        if (!isset($_SESSION['visited'])) {
           $count++;
           file_put_contents('./count.txt', $count);
           $_SESSION['visited'] = true;
        }

        echo "$count verschiedene Benutzer haben die Website bereits besucht!";
        ?>
        ````

    === "Zugabe"

        ````php
        <?php
        // Startet die Session
        session_start();

        // liest das File aus
        $count = (int) file_get_contents('./count.txt'); 

        // Überprüfen ob Session-Variable registriert ist
        if (!isset($_COOKIE['session'])) {
           $count++;
           file_put_contents('./count.txt', $count);
           setcookie("session",$_SESSION['visited'] = true,time()+(3600*24));
        }

        echo "$count verschiedene Benutzer haben die Website bereits besucht!";
        ?>
        ````