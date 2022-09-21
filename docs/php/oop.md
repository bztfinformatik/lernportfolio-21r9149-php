# OOP in PHP

## Klasse definieren
````php
<?php
class EuerKlassenName {
 // ...
}
?>
````

### Eigenschaften
````php
<?php
class EuerKlassenName {
 public $eigenschaft1;
 public $eigenschaft2;
 //...
}
?>
````

### Funktion
````php
<?php
class EuerKlassenName {
 function EuerMethodenName($parmater1, $parameter2, $parameter3) {
 // Euer Code der Methode
 }
}
?>
````

## Fragen
!!! Abstract "1. Wie wird in PHP instanziert?"

??? Check "Solution"

    ````php
    <?php
    class MeineKlasse
    {
        public $gib_laut = 'Hallo Welt';
    }
    
    $meinObjekt = new MeineKlasse(); // erstellt eine neue Instanz
    ?>
    ````

!!! Abstract "2. Was bedeutet der Pfeil"

??? Check "Solution"
    
    Der Objektoperator ``->`` wird im Objektbereich verwendet, um auf Methoden und Eigenschaften eines Objekts zuzugreifen.

    ````php
    <?php
    // Create a new instance of MyObject into $obj
    $obj = new MyObject();

    // Set a property in the $obj object called thisProperty
    $obj->thisProperty = 'Fred';

    // Call a method of the $obj object named getProperty
    $obj->getProperty()
    ?>
    ````

!!! Abstract "3. Was bedeutet ``this``"

??? Check "Solution"
    Mit dem Schlüsselwort ``$this`` können Sie mit dem Objektoperator (``->``) auf die Eigenschaften und Methoden des aktuellen Objekts innerhalb der Klasse zugreifen

    ````php
    $this->property
    $this->method()
    ````

!!! Abstract "4. Welche Möglichkeiten an Zugriffsmodifizierer kennt PHP?"

??? Check "Solution"
    - public
    - private
    - protected
    - abstract
    - final
    - static

!!! Abstract "5. Dokumentieren Sie Beispiele zu Konstruktoren, Methoden, Klassen."

??? Check "Solution"

    ````php
    <?php
    class Fruit {
      // Eingenschaften   
      public $name;
      public $color;
      
      // Konstruktor
      function __construct($name) {
        $this->name = $name;
      }

      // Funktion
      function get_name() {
        return $this->name;
      }
    }
    
    // Instanz der Klasse Fruit
    $apple = new Fruit("Apple");
    // greift mitels -> auf die Funktion zu
    echo $apple->get_name();
    ?>
    ````

!!! Abstract "6. Dokumentieren Sie die Beispiele zur Vererbung mit PHP"

??? Check "Solution"

    ````php
    <?php
    class BaseClass {
        // Konstruktor für die Klasse BaseClass
        function __construct() {
            print "In BaseClass constructor\n";
        }
    }

    class SubClass extends BaseClass {
        // Konstruktor für die Klasse SubClass
        function __construct() {
            // mit ``parent::`` wird die Funktion der Übergeordneten Klasse ausgeführt.
            parent::__construct();
            print "In SubClass constructor\n";
        }
    }

    class OtherSubClass extends BaseClass {
        // vererbt BaseCalss Konstruktor
    }

    // In BaseClass constructor
    $obj = new BaseClass();
    
    // In BaseClass constructor
    // In SubClass constructor
    $obj = new SubClass();

    // In BaseClass constructor
    $obj = new OtherSubClass();
    ?>
    ````