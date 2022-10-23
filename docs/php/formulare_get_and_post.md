# Formulare mit $_Get und $_Post

## $_Get

!!! example
    ``/test/demo_form.php?name1=value1&name2=value2``

    - Get request can be cached
    - Get request remain in the browser history
    - Get request can be bookmarked
    - Get request should never be ussed when dealing with sensitive data
    - Get request have lenght restrictions
    - Get request is only used to request data (not modify)

### Auswertung von Formularen

=== "Code"
    ``` php
    <?php
    echo "Eingetragener Vorname: ". $_GET['vorname']; # (1)
    ?>
    
    <form action="index.php" method="get">
       <p>Ihr Vorname: 
       <input type="text" name="vorname">
       </p>
    
       <p>
          <input type="submit" value="absenden">
       </p>
    </form>
    ```

    1.  Variable wird aus der URL ausgelesen.

=== "Formular"
    <figure markdown>
      ![Get-Formular](/assets/get_formular.png)
      <figcaption>http://localhost:8080/index.php?vorname=test</figcaption>
    </figure>

## $_Post

!!! example
    ````
    POST /test/demo_form.php HTTP/1.1
    HOST: w3schools.com
    name1=value1&name2=value2
    ````

    - POST requests are never cached
    - POST requests do noto remain in the browser history
    - POST requests cannot be bookmarked
    - POST requests have no restrictions on data lenght

### Auswertung von Formularen

=== "Code"

    ``` php
    <?php
    echo "Eingetragener Vorname: ". $_GET['vorname']; # (1)
    ?>
    
    <form action="index.php" method="get">
       <p>Ihr Vorname: 
       <input type="text" name="vorname">
       </p>
    
       <p>
          <input type="submit" value="absenden">
       </p>
    </form>
    ```

    1.  Variable wird aus der URL ausgelesen.

=== "Formular"

    <figure markdown>
      ![Get-Formular](/assets/get_formular.png)
      <figcaption>http://localhost:8080</figcaption>
    </figure>

!!! Tip

    ````php
    <?php
    isset(variable) // true / false
    // Übeprüft, ob eine Variable vorhanden ist

    empty // true / false
    // Überprüft, ob eine Variable keinen Inhalt hat

    print_r($_POST)
    // Zeigt den Inhalt einer Variable in lesbarer Form

    var_dump($_POST)
    // Zeigt den Inhalt mehrerer Variablen in lesbarer Form ganz deteilliert
    ?>
    ````    
