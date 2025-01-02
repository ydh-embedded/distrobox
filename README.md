# Container

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

```ps
   ~  sudo pacman -S podman distrobox  opencl-nvidia                                         1 ✘
Warnung: podman-5.3.1-1 ist aktuell -- Reinstalliere
Warnung: distrobox-1.8.0-1 ist aktuell -- Reinstalliere
Warnung: opencl-nvidia-550.135-1 ist aktuell -- Reinstalliere
Abhängigkeiten werden aufgelöst …
Nach in Konflikt stehenden Paketen wird gesucht …

Pakete (3) distrobox-1.8.0-1  opencl-nvidia-550.135-1  podman-5.3.1-1

Gesamtgröße der installierten Pakete:  103,01 MiB
Größendifferenz der Aktualisierung:      0,00 MiB

:: Installation fortsetzen? [J/n] j
(3/3) Schlüssel im Schlüsselbund werden geprüft                [##################################] 100%
(3/3) Paket-Integrität wird überprüft                          [##################################] 100%
(3/3) Paket-Dateien werden geladen                             [##################################] 100%
(3/3) Auf Dateikonflikte wird geprüft                          [##################################] 100%
(3/3) Verfügbarer Festplattenspeicher wird ermittelt           [##################################] 100%
:: Pre-transaction-Hooks werden gestartet …
(1/1) Creating Timeshift snapshot before upgrade...
==> skipping timeshift-autosnap due skipRsyncAutosnap in /etc/timeshift-autosnap.conf set to TRUE.
:: Paketänderungen werden verarbeitet …
(1/3) Reinstalliert wird podman                                [##################################] 100%
(2/3) Reinstalliert wird distrobox                             [##################################] 100%
(3/3) Reinstalliert wird opencl-nvidia                         [##################################] 100%
:: Post-transaction-Hooks werden gestartet …
(1/5) Reloading system manager configuration...
(2/5) Reloading user manager configuration...
(3/5) Creating temporary files...
(4/5) Arming ConditionNeedsUpdate...
(5/5) Updating icon theme caches...

```
