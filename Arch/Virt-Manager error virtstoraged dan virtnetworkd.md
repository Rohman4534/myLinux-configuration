# service di dalam libvirt error

cek service dari libvirt dan terdapat pesan error ini
```
$ systemctl status virtqemud
● virtqemud.service - Virtualization qemu daemon
     Loaded: loaded (/usr/lib/systemd/system/virtqemud.service; enabled; preset: disabled)
     Active: active (running) since Wed 2023-06-07 08:20:23 WITA; 8min ago
TriggeredBy: ● virtqemud-ro.socket
             ● virtqemud-admin.socket
             ● virtqemud.socket
       Docs: man:virtqemud(8)
             https://libvirt.org
    Process: 3872 ExecReload=/bin/kill -HUP $MAINPID (code=exited, status=0/SUCCESS)
   Main PID: 2166 (virtqemud)
      Tasks: 19 (limit: 32768)
     Memory: 16.3M
        CPU: 457ms
     CGroup: /system.slice/virtqemud.service
             └─2166 /usr/bin/virtqemud --timeout 120

Jun 07 08:20:24 ROHMANPC virtqemud[2166]: Failed to connect socket to '/var/run/libvirt/virtstoraged-sock': No such file or directory
Jun 07 08:20:24 ROHMANPC virtqemud[2166]: Failed to connect socket to '/var/run/libvirt/virtstoraged-sock': No such file or directory
Jun 07 08:20:30 ROHMANPC virtqemud[2166]: Failed to connect socket to '/var/run/libvirt/virtnetworkd-sock': No such file or directory
Jun 07 08:20:30 ROHMANPC virtqemud[2166]: Failed to connect socket to '/var/run/libvirt/virtstoraged-sock': No such file or directory
Jun 07 08:20:35 ROHMANPC virtqemud[2166]: Failed to connect socket to '/var/run/libvirt/virtstoraged-sock': No such file or directory
Jun 07 08:20:38 ROHMANPC virtqemud[2166]: Failed to connect socket to '/var/run/libvirt/virtstoraged-sock': No such file or directory
Jun 07 08:20:48 ROHMANPC virtqemud[2166]: Failed to connect socket to '/var/run/libvirt/virtstoraged-sock': No such file or directory
Jun 07 08:21:04 ROHMANPC virtqemud[2166]: Failed to connect socket to '/var/run/libvirt/virtstoraged-sock': No such file or directory
Jun 07 08:28:18 ROHMANPC systemd[1]: Reloading Virtualization qemu daemon...
Jun 07 08:28:18 ROHMANPC systemd[1]: Reloaded Virtualization qemu daemon.
```

buat file libvirt-sock dan coba restart lagi service libvirt

```
$ touch /var/run/libvirt/libvirt-sock
$ $ systemctl status virtqemud
```

error sudah tidak ada lagi

```
$ systemctl status virtqemud
● virtqemud.service - Virtualization qemu daemon
     Loaded: loaded (/usr/lib/systemd/system/virtqemud.service; enabled; preset: disabled)
     Active: active (running) since Wed 2023-06-07 08:38:30 WITA; 3s ago
TriggeredBy: ● virtqemud-ro.socket
             ● virtqemud-admin.socket
             ● virtqemud.socket
       Docs: man:virtqemud(8)
             https://libvirt.org
   Main PID: 4900 (virtqemud)
      Tasks: 19 (limit: 32768)
     Memory: 3.5M
        CPU: 53ms
     CGroup: /system.slice/virtqemud.service
             └─4900 /usr/bin/virtqemud --timeout 120

Jun 07 08:38:30 ROHMANPC systemd[1]: Starting Virtualization qemu daemon...
Jun 07 08:38:30 ROHMANPC systemd[1]: Started Virtualization qemu daemon.
```



