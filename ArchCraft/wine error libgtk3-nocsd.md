# wine error
## “ERROR: ld.so: object ‘/libgtk3-nocsd.so.0’ from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored.”

running wine

```
$ wine
```

error nya

```
ERROR: ld.so: object '/usr/${LIB}/libgtk3-nocsd.so.0' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored.
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
```

ketik ini untuk melihat apakah ada libgtk3-nocsd.so.0

```
$ echo ${LD_PRELOAD}
```

akan tampil seperti ini

```
/usr/${LIB}/libgtk3-nocsd.so.0
```

hilangkan `/usr/${LIB}/libgtk3-nocsd.so.0` dan cek lagi

```
$ export LD_PRELOAD=""
$ echo ${LD_PRELOAD}

$
```

tes jalankan wine

```
$ wine
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
```

berhasil !!

