# Spotify error GPU process isn't usable. Goodbye

ketika menjalankan spotify lewat desktop app maka otomatis akan keluar sendiri atau layar nya terus keabu-abuan

menjalankan spotify lewat terminal akan mendapat pesan error ini

```
$ spotify
Gtk-Message: 10:55:26.834: Failed to load module "xapp-gtk3-module"
[0611/105527.322875:FATAL:gpu_data_manager_impl_private.cc(440)] GPU process isn't usable. Goodbye.
139666029172512:error:1000007d:SSL routines:OPENSSL_internal:CERTIFICATE_VERIFY_FAILED:../../third_party/boringssl/src/ssl/handshake.cc:393:
[1]    14040 trace trap (core dumped)  spotify
```

jalan spotify dengan command ini

```
spotify --no-zygote
```

ubah juga perintah launcher spotify di desktop. spotify saya install dengan snap dan perlu di ubah permission agar bisa di edit file 
spotify.desktop nya

```
$ cd /var/lib/snapd/snap/spotify/67/usr/share/spotify
$ 
```
