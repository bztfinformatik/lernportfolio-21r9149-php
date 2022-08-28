# Inhaltsverzeichnis
>- [Docker](#docker)
>    - [Was ist Container-Virtalisierung](#Was_ist_Container-Virtalisierung)
>    - [Wofür wird Docker verwendet?](#Wofür_wird_Docker_verwendet?)
>    - [Was ist Container-Virtalisierung](#Was_ist_Container-Virtalisierung)
>- [PHP Einfuehrung](#php-einfuerung)
>   - [Erste Schritte](#erste-schritte)
>   - [Hello World!](#hello-world)
>   - [Kommentare](#kommentare)
>   - [Variablen](#variablen)

## Docker
Bei Docker handelt es sich um eine Technologie für die containerbasierte Virtualisierung von Software-Anwendungen.

### Was ist Container-Virtalisierung
Container sind virtuell abgetrennte Umgebungen, in denen Software Anwendungen für die Bereitstellung verpackt und isoliert. Container greifen gemeinsam auf einen Betriebssystemkern zu, ohne dass virtuelle Maschinen (VMs) erforderlich sind.

Unterschied Zwischen VM und Docker: <br>
<img src="assets/images/vm-docker.webp" alt="Docker/VM Unterschied" width="500"/> <br>
https://www.opc-router.de/was-ist-docker/

### Wofür wird Docker verwendet?

Mit Docker kann man gesamte Infrastrukturen virtuell erstellen. Bei jedem start wird die Infrastruktur neu erstellt, somit beginnt kann man nach jedem neustart von eine "grünen Wiese" beginnen. Durch das teilen eines Container können andere Personen einfach und ohne grossem Zeitaufwand mit der selben Infrastruktur arbeiten.

### Hello World laufen lassen

````docker
docker run hello-world
````

``docker run`` wird dazuverwendet um Container zu starten. ``hello-world`` ist der Name des Images, das jemand auf dem Dockerhub erstellt hat. Beim ausführen des Befehls wird zuerst lokal nach dem ``hello-world``-Image gesucht und danach im Dockerhub.

## PHP Einfuerung

### Erste Schritte
Um zu sehen, ob auf einem Server überhaupt PHP installiert ist, benötigt man eine PHP-Datei (z.B. phpinfo.php) mit folgendem Inhalt:
````php
<?php
phpinfo();
?>
````

### Hello World!
Mit ``echo`` können ``Strings`` ausgegeben werden.
````php
<?php
echo "Hello World!";
?>
````
Das Semikolon (``;``) beendet die Anweisung ``echo``. Fast jeder Befehl (bis auf wenige Ausnahmen) endet mit einem Semikolon (``;``). Mit ``?>`` beenden wir das PHP-Script.`
<br>
Möchte man *"Hello" World!* ausgeben so muss man die Anführungszeichen bei "World" mit einem Maskierungszeichen versehen. Dazu benutzen wir den Backslash ``\``. Beispiel:

````php
<?php
echo "Hello \"World\"";
?>
````

### Kommentare
````php
// Das ist ein einzeiliger Kommentar

# Das ist auch ein einzeiliger Kommentar

/* Das
ist ein Mehrzeiliger
Komentar */
````

### Variablen
Variablen werden immer mit einem ``$`` gefolgt vom Variablennamen. Variablen können mit einem Unterstrich oder mit einem Buchstaben.<br>
Beispiel:
````php
// Code
<?php
$name = "Paul Meier";
echo "Zuerst heiße ich $name <br />";

$name = "Stefan Müller";
echo "Dann ist mein Name $name";
?>

// Ausgabe
Zuerst heiße ich Paul Meier
Dann ist mein Name Stefan Müller
````

> [!WARNING]
> Variablen dürfen nicht mit einer Zahl beginnen!

Man kann auch an eine bereits vorhandene Variable eine weitere Variable, oder einen Text anhängen.
````php
<?php
$name = "Nils ";
$name .= "Reimers";
echo $name;

// Ausgabe: Nils Reimers

echo "Mein Name ist ".$name." und wohne in Frauenfeld";

// Ausgabe: Mein name ist Nils Reimers und wohne in Frauenfeld.
?>
````

#### Variablentypen
````php
<?php
$integer = 15; //Eine Integer Variable
$string = "Ganz viel Text"; //Ein String
$float = 15.5; //Eine Zahl mit einem Komma
$bool = true;
?>
````