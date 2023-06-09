# virt-manager. qemu/KMV still connecting

ketika membuka virtual machine manager, qemu/KVM terus melakukan connecting, ketika di cek service virtqemud status nya berjalan tetapi ada error membaca data

```
$ systemctl status virtqemud
● virtqemud.service - Virtualization qemu daemon
     Loaded: loaded (/usr/lib/systemd/system/virtqemud.service; enabled; preset: disabled)
     Active: active (running) since Fri 2023-06-09 15:22:48 WITA; 1min 13s ago
TriggeredBy: ● virtqemud.socket
             ● virtqemud-ro.socket
             ● virtqemud-admin.socket
       Docs: man:virtqemud(8)
             https://libvirt.org
   Main PID: 2020 (virtqemud)
      Tasks: 19 (limit: 32768)
     Memory: 16.7M
        CPU: 740ms
     CGroup: /system.slice/virtqemud.service
             └─2020 /usr/bin/virtqemud --timeout 120

Jun 09 15:22:48 ROHMANPC systemd[1]: Starting Virtualization qemu daemon...
Jun 09 15:22:48 ROHMANPC systemd[1]: Started Virtualization qemu daemon.
Jun 09 15:23:20 ROHMANPC virtqemud[2020]: libvirt version: 9.4.0
Jun 09 15:23:20 ROHMANPC virtqemud[2020]: hostname: ROHMANPC
Jun 09 15:23:20 ROHMANPC virtqemud[2020]: End of file while reading data: Input/output error
```

msh belum ketemu caranya, tetapi ini beberapa cara sementara
1. reboot dan ketika sudah mencapai dekstop langsung buka virtual-machine manager, qemu/kvm bisa terhubung/ connected


2. dengan menjalan libvirt manual 
```
sudo libvirtd
```
setelah itu kembali ke virtual-machine manager dan clik qemu/kvm connection.


