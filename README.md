<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="style.css"> <!-- Link to your CSS file -->
    <title>Collapsible Section Example</title>
</head>
<body>

<button class="collapsible">Click to expand</button>

<div class="content">
    <p>This is the hidden text that will be revealed when you click the button. You can put a lot of text here.</p>
</div>

<script>
    const coll = document.getElementsByClassName("collapsible");
    for (let i = 0; i < coll.length; i++) {
        coll[i].addEventListener("click", function() {
            this.classList.toggle("active");
            const content = this.nextElementSibling;
            if (content.style.display === "block") {
                content.style.display = "none";
            } else {
                content.style.display = "block";
            }
        });
    }
</script>

# Container

![ship](./screen/ships.webp)

## distrobox

### Wir erstellen eine neuen Container [rocky:9]

```ps
    distrobox create --name container_rocky_9 --image docker.io/library/rockylinux:9
```

### Wir starten den Container

```ps
    distrobox enter container_ubuntu
```

### Wir lassen uns die Container mit Details auflisten

```ps
    distrobox list --no-color
```

### Bei manchen distros müssen wir (super)user manuel hinzufügen

```ps
    sudo usermod -aG sudo your_username
```

### Wir können auch die Container löschen

```bash
    distrobox rm container_rocky_9
```

## podman distrobox

### Wir installieren podman distrobox mit Grafik-Treibern

```ps
    sudo pacman -S podman distrobox  opencl-nvidia
```

<details open>
<summary>Click to expand</summary>
...
```ps
   ~  sudo pacman -S podman distrobox  opencl-nvidia                                         1 ✘
Warnung: podman-5.3.1-1 ist aktuell -- Reinstalliere
Warnung: distrobox-1.8.0-1 ist aktuell -- Reinstalliere
Warnung: opencl-nvidia-550.135-1 ist aktuell -- Reinstalliere
Abhängigkeiten werden aufgelöst …
Nach in Konflikt stehenden Paketen wird gesucht …

Pakete (3) distrobox-1.8.0-1 opencl-nvidia-550.135-1 podman-5.3.1-1

Gesamtgröße der installierten Pakete: 103,01 MiB
Größendifferenz der Aktualisierung: 0,00 MiB

:: Installation fortsetzen? [J/n] j
(3/3) Schlüssel im Schlüsselbund werden geprüft [##################################] 100%
(3/3) Paket-Integrität wird überprüft [##################################] 100%
(3/3) Paket-Dateien werden geladen [##################################] 100%
(3/3) Auf Dateikonflikte wird geprüft [##################################] 100%
(3/3) Verfügbarer Festplattenspeicher wird ermittelt [##################################] 100%
:: Pre-transaction-Hooks werden gestartet …
(1/1) Creating Timeshift snapshot before upgrade...
==> skipping timeshift-autosnap due skipRsyncAutosnap in /etc/timeshift-autosnap.conf set to TRUE.
:: Paketänderungen werden verarbeitet …
(1/3) Reinstalliert wird podman [##################################] 100%
(2/3) Reinstalliert wird distrobox [##################################] 100%
(3/3) Reinstalliert wird opencl-nvidia [##################################] 100%
:: Post-transaction-Hooks werden gestartet …
(1/5) Reloading system manager configuration...
(2/5) Reloading user manager configuration...
(3/5) Creating temporary files...
(4/5) Arming ConditionNeedsUpdate...
(5/5) Updating icon theme caches...

```
</details>

### Unterschiede

    Die Unterschiede liegen nicht in der Befehlsanweisung sondern im Backend.
    In erster Linie in der zugrundeliegenden Container-Verwaltungstechnologie,
    welche verwendet wird und in der Art und Weise, wie sie aufgerufen werden

    "distrobox:" Verwendet das auf Ihrem System konfigurierte Standard-Container-Backend (kann Podman, Docker usw. sein).
    "podman distrobox:" Verwendet explizit Podman als Container-Backend.
    Daemonlos vs. Daemonbasiert:

    Podman arbeitet in einem daemonlosen Modus,
    das Bedeutet es benötigt keinen lang laufenden Dienst zur Verwaltung von Containern,
    was bestimmte Arbeitsabläufe vereinfachen und die Sicherheit verbessern kann.

### Container Management Backends

#### Podman --Daemonlos--

    Podman ist so konzipiert, dass es ohne Daemon auskommt, d. h. es benötigt keinen langlaufenden Hintergrunddienst zur Verwaltung von Containern. Jeder Podman-Befehl wird als separater Prozess ausgeführt, was die Sicherheit verbessern und die Arbeitsabläufe vereinfachen kann. Dies ist eine der Hauptfunktionen von Podman, die es Benutzern ermöglicht, Container ohne einen zentralen Daemon auszuführen.

#### Docker --Deamon-basiert:

    Docker hingegen verwendet eine Client-Server-Architektur, bei der der Docker-Client mit dem Docker-Daemon (dockerd) kommuniziert. Der Daemon ist für die Verwaltung von Containern, Images, Netzwerken und Volumes zuständig. Das bedeutet, dass der Docker-Daemon ausgeführt werden muss, damit Sie Docker-Befehle verwenden können.

</body>
</html>
```
