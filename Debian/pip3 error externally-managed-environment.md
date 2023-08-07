# pip3 error externally-managed-environment

error install gns3-gui dari pip 3

```
$ pip3 install gns3-gui
error: externally-managed-environment

× This environment is externally managed
╰─> To install Python packages system-wide, try apt install
    python3-xyz, where xyz is the package you are trying to
    install.
    
    If you wish to install a non-Debian-packaged Python package,
    create a virtual environment using python3 -m venv path/to/venv.
    Then use path/to/venv/bin/python and path/to/venv/bin/pip. Make
    sure you have python3-full installed.
    
    If you wish to install a non-Debian packaged Python application,
    it may be easiest to use pipx install xyz, which will manage a
    virtual environment for you. Make sure you have pipx installed.
    
    See /usr/share/doc/python3.11/README.venv for more information.

note: If you believe this is a mistake, please contact your Python installation or OS distribution provider. You can override this, at the risk of breaking your Python installation or OS, by passing --break-system-packages.
hint: See PEP 668 for the detailed specification.
```

karena `gns3-gui` bukan dari package debian

## solusi pertama bisa menginstall dengan pipx

```
$ pipx install gns3-gui
  installed package gns3-gui 2.2.41, installed using Python 3.11.2
  These apps are now globally available
    - gns3
done! ✨ 🌟 ✨
$ 

```

## solusi kedua bisa dengan memakai python venv
buat arahkan dulu folder konfigurasi gns3 venv nya
```
$ python3 -m venv ~/.venv/gns3
$
```

lalu aktifkan venv yang ada di gns3
```
$ source ~/.venv/gns3/bin/activate
(gns3) $
```
terakhir tinggal install gns3-gui dengan pip3 di dalam venv
```
(gns3) $ pip3 install gns3-gui
Collecting gns3-gui
  Using cached gns3_gui-2.2.41-py3-none-any.whl
Requirement already satisfied: sentry-sdk<1.18,==1.17.0 in /home/rohman/.venv/gns3/lib/python3.11/site-packages (from gns3-gui) (1.17.0)
Requirement already satisfied: psutil==5.9.4 in /home/rohman/.venv/gns3/lib/python3.11/site-packages (from gns3-gui) (5.9.4)
Requirement already satisfied: distro>=1.8.0 in /home/rohman/.venv/gns3/lib/python3.11/site-packages (from gns3-gui) (1.8.0)
Requirement already satisfied: jsonschema<4.18,>=4.17.3 in /home/rohman/.venv/gns3/lib/python3.11/site-packages (from gns3-gui) (4.17.3)
Requirement already satisfied: setuptools>=60.8.1 in /home/rohman/.venv/gns3/lib/python3.11/site-packages (from gns3-gui) (66.1.1)
Requirement already satisfied: certifi in /home/rohman/.venv/gns3/lib/python3.11/site-packages (from sentry-sdk<1.18,==1.17.0->gns3-gui) (2023.7.22)
Requirement already satisfied: urllib3>=1.26.11 in /home/rohman/.venv/gns3/lib/python3.11/site-packages (from sentry-sdk<1.18,==1.17.0->gns3-gui) (2.0.4)
Requirement already satisfied: attrs>=17.4.0 in /home/rohman/.venv/gns3/lib/python3.11/site-packages (from jsonschema<4.18,>=4.17.3->gns3-gui) (23.1.0)
Requirement already satisfied: pyrsistent!=0.17.0,!=0.17.1,!=0.17.2,>=0.14.0 in /home/rohman/.venv/gns3/lib/python3.11/site-packages (from jsonschema<4.18,>=4.17.3->gns3-gui) (0.19.3)
Installing collected packages: gns3-gui
Successfully installed gns3-gui-2.2.41
(gns3) $
```
untuk menjalankan gns3 di venv anda perlu mengaktifkan venv dan jika sudah selesai menggunakan gn3 anda juga bisa menghentikan venv
```
$ source ~/.venv/gns3/bin/activate
(gns3) $ deactivate
$ 
```
jika cara menjalankan venv dirasa repot, anda bisa membuat laucher yang exekusi program nya bisa diarahkan ke bin file di dalam folder gns3 venv
yang terletak di ~/.venv


