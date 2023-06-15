# install samba dan konfigurasi tambahan
samba merupakan sebuah app yang dapat melakukan sharing file layaknya windows network file sharing.

## install samba
install dengan perintah 

```
$ sudo pacman -S samba
```

## konfigurasi samba
samba sendiri tidak menyediakan file konfigurasinya. oleh karena itu kita perlu membuat sendiri file konfigurasi samba. 
kita perlu mencari dulu salinan dari konfigurasi samba. kalian bisa ke [samba git repository](https://git.samba.org/samba.git/?p=samba.git;a=blob_plain;f=examples/smb.conf.default;hb=HEAD) 
.buat file kosong dengan nama 'smb.conf' dan salin konfigurasi yang ada di samba git, lalu simpan di `usr/samba/smb.conf`

## buat file sharing
selanjutnya kita akan membuat satu folder sharing. caranya masuk ke `smb.conf` dan buat nama folder sharing kalian
```
[rohman]
comment = public share
path = /run/media/rohman
browseable = yes
writable = yes
guest ok = yes  # agar user tamu atau selain user yang tidak ditambahkan bisa akses folder sharing
```

restart service smb dan nmb
```
$ systemctl restart smb nmb
```

## buat samba agar hanya ip tertentu bisa akses  -- opsional
samba memiliki banyak sekali opsi untuk keamanan salah satunya, kita bisa membuat agar bisa mengakses dengan ip yang telah ditentukan

ke smb.conf dan buat perintah [global] seperti ini, di [global kalian bisa menambahkan opsi keamanan lainnya]
```
[global]
hosts allow = 192.168.29.  # mengizinkan semua client dari host .29
interfaces = 192.168.12.29.9 # mengizinkan hanya 1 client jika ingin menambahkan lagi tambahkan tanda ( , )  lalu ip nya
```
tambah user samba agar bisa login ke samba
```
$ sudo smbpasswd -a rohman
New SMB password:
Retype new SMB password:
Added user rohman.
```

restart smb dan nmb
$ systemctl start smb nmb




