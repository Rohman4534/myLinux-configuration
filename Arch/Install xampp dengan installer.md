# install xampp dengan installer
xampp merupakan software untuk kebutuhan web server. isinya beberapa aplikasi
dari apache2, mysql-server, php, dan perl. 

## download installer xampp
download di official [xampp](https://www.apachefriends.org/download.html)

## install xampp
ke directory download dan install xampp dengan user root
```
$ cd Downloads
$ sudo sudo ./xampp-linux-x64-8.2.4-0-installer.run

```
jalankan installer. pastikan xampp terinstall di `opt/lampp`

tunggu proses install nya

## menjalankan xampp

menjalankan xampp perintah berikut
```
sudo /opt/lampp/lampp start
```
jika pesan seperti ini berarti xampp sudah jalan

```
$ sudo /opt/lampp/lampp start
[sudo] password for rohman:
Starting XAMPP for Linux 8.2.4-0...
XAMPP: Starting Apache.../opt/lampp/share/xampp/xampplib: line 22: netstat: command not found
egrep: warning: egrep is obsolescent; using grep -E
/opt/lampp/share/xampp/xampplib: line 22: netstat: command not found
egrep: warning: egrep is obsolescent; using grep -E
ok.
XAMPP: Starting MySQL...egrep: warning: egrep is obsolescent; using grep -E
/opt/lampp/share/xampp/xampplib: line 22: netstat: command not found
ok.
XAMPP: Starting ProFTPD.../opt/lampp/share/xampp/xampplib: line 22: netstat: command not found
egrep: warning: egrep is obsolescent; using grep -E
ok.
```

## membuat shortcut xampp agar di klik di dekstop

buat file baru lalu salin ini
```
[Desktop Entry]
Type=Application
Icon=xampp
Exec=sudo /opt/lampp/./manager-linux-x64.run
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=Xampp-8.2.4
Name=rofi launcher
Comment[en_US]=Xampp control panel
Comment=Xampp control panel
Path=/opt/lampp
Terminal=true
StartupNotify=false
GenericName=Xampp control panel
```
beri nama Xampp-8.2.4.desktop dan simpan. pindahkan file nya ke /usr/share/application

```
$ sudo mv Xampp-8.2.4.desktop /usr/share/applications
```

dengan ini xampp nya sudah bisa di klik di dekstop.




