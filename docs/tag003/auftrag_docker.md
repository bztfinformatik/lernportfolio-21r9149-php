# Inhaltsverzeichnis
>- [Docker](#docker)
>    - [Was ist Container-Virtalisierung](#Was_ist_Container-Virtalisierung)
>    - [Wofür wird Docker verwendet?](#Wofür_wird_Docker_verwendet?)
>    - [Was ist Container-Virtalisierung](#Was_ist_Container-Virtalisierung)

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