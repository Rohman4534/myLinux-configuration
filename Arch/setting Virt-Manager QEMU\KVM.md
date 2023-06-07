# Virt-manager fails to connect to system QEMU/KVM
virt-manager untuk menjalankan qemu emulator secara gui, untuk menggunakan nya virt-manager perlu di sambungkan ke qemu

## pesan error saat menyambung qemu
saat pertama kali install qemu biasanya akan error seperti ini
```
Unable to connect to libvirt qemu:///system.

authentication unavailable: no polkit agent available to authenticate action 'org.libvirt.unix.manage'
```

user belum ditambahkan ke group libvirt, install terlebih dahulu libvirt dan setelah itu tambahkan ke nama $user ke group nya

```
$ sudo pacman -S libvirt
$ sudo usermod -aG libvirt rohman
```

nyalakan dan restart semua service dari libvirt
```
$ systemctl enable virtqemud
$ systemctl enable virtnodedevd
$ systemctl enable virtstoraged
$ systemctl enable virtnetworkd

$ systemctl restart virtqemud
$ systemctl restart virtnodedevd
$ systemctl restart virtstoraged
$ systemctl restart virtnetworkd
```

reboot dan tes ke virtual-manager lagi
