# "The emulator may not have search permissions for the path" 

edit `/etc/libvirt/qemu.conf`. tambahkan username ke group libvirt 

```
$ sudo nano /etc/libvirt/qemu.conf
```

cari yang membahas tentang user dan group

```
# Some examples of valid values are:
#
#       user = "qemu"   # A user named "qemu"
#       user = "+0"     # Super user (uid=0)
#       user = "100"    # A user named "100" or a user with uid=100
#
#user ="qemu"

# The group for QEMU processes run by the system instance. It can be
# specified in a similar way to user.
#group ="qemu"
```

uncomment `#user ="qemu"` dan `#group ="qemu"`, ganti dengan nama user atau lebih aman bisa diganti root, jika virt-manager ingin dijalankan sebagai root

```
# Some examples of valid values are:
#
#       user = "qemu"   # A user named "qemu"
#       user = "+0"     # Super user (uid=0)
#       user = "100"    # A user named "100" or a user with uid=100
#
#user ="qemu"
user = "rohman"

# The group for QEMU processes run by the system instance. It can be
# specified in a similar way to user.
#group ="qemu"
group = "rohman"
```
