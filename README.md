# distrobox

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
