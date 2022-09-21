# Model-View-Controller
Das MVC (*Model-View-Controller*) ist wohl das häufigste Design Pattern in PHP. <br>
Beim MVC-Muster wird das Klassendesign in drei verschiedene  Kategorien unterteil: <br>

- **Model:** Jede "**Entität**" der Datenbankstruktur besitzt eine **eigene Model-Klasse**. Dies sorgt dafür das Daten aus der Datenbank geladen und gespeichert werden könen.

- **View:** Die View ist für die **Darstellung** eurer Daten verantwortlich. In der View befindet sich keine Logik. In der View befinden sich beispielsweise Templates um die Website mittels HTML und CSS auszugeben.

- **Controller:** Die Controller Klassen sind die **Schnitstelle** zwischen dem **Model** und der **View** . In diesen Klassen wird die Logik implementiert.

## Das model

Veim model wird der Zugriff auf die Datenbankstabellen Programmiert.

````php
<?php
//$pdo enthält die Datenbankverbindung
 
class User {
   // Klasse zur Abbildung eurer Benutzer
 
   public static function newUser($email, $vorname, $nachname, $passwort) {
   }
 
   public static function findByEmail($email) {
   }
 
 
   public function delete() {
   }
 
   public function setPassword($newPassword) {
   }
 
}
 
class Product {
   // Klasse zur Darstellung von Produkten im Online-Shop ähnlich wie oben
   //...
}
 
class ProductOrder {
   // Klasse zur Darstellung neuer Produktbestellungen
   public function __constructor(User $user) {
   }
 
   public function addProduct(Product $product) {
   }
 
   public function addProductById($productId) {
   }
 
   public function buy() {
   } 
}
?>
````

## Die View
In der View definiert mann, wie die Daten dargestellt werden sollen. Typischerweise bedeutet dies, dass man gewisse HTML Templates besitzt in der eure Daten reingeladen werden.<br>

Die einfachste Template-Engine ist die Verwendung der ``ìnclude()`` Funktion.

````php
<?php
$max = User::findByEmail("max@muster.de");
 
$order = new ProductOrder($max);
$order->addProductById(23);
$order->addProductById(42);
 
if($order->buy()) {
   include("order-successful.view.php");
} else {
   include("order-failed.view.php");
}
?>
````

=== "order-successful.view.php"
    
    ````php
    Deine Bestellung über <?php echo $order->getPrice(); ?> war <b>erfolgreich</b>.
    ````

=== "order-failed.view.php"

    ````php
    Deine Bestellung ist leider <b>fehlgeschlagen</b>. Bitte kontaktiere unseren Support.
    ````

## Der Controller
Der Controller implementiert eure Anwendungslogik.

````php
<?php
class UserController {
 public function registerNewUser($email, $password) {
 //Entsprechende Überprüfungen und SQL Queries zum Registrieren des Nutzers
 //Gibt z.B. true zurück, falls die Registrierung funktioniert hat
 }
 
 public function changeUserPassword(User $user, $new_password) {
 //Ändert das Benutzerpasswort für den Nutzer $user
 }
 
 public function sendNewPassword(User $user) {
 //Sendet dem Benutzer ein neues Passwort zu
 }
}
?>
````