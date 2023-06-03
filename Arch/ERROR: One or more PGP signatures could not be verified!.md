# One or more PGP signatures could not be verified!

saat saya menginstall `lib32-poppler` terdapat banyak info error tetapi inti utama adalah pesan error ini

```
$ sudo pacman -S lib32-poppler


:: (1/1) Parsing SRCINFO: lib32-poppler
==> Making package: lib32-poppler 23.05.0-1 (Sab 03 Jun 2023 07:37:03 )
==> Checking runtime dependencies...
==> Checking buildtime dependencies...
==> Retrieving sources...
  -> Found poppler-23.05.0.tar.xz
  -> Found poppler-23.05.0.tar.xz.sig
  -> Updating test git repo...
  -> Found pkgconf32
==> Validating source files with sha512sums...
    poppler-23.05.0.tar.xz ... Passed
    poppler-23.05.0.tar.xz.sig ... Skipped
    test ... Skipped
    pkgconf32 ... Passed
==> Verifying source file signatures with gpg...
    poppler-23.05.0.tar.xz ... FAILED (unknown public key 3A6A4DB839EAA6D7)
==> ERROR: One or more PGP signatures could not be verified!
 -> error making: lib32-poppler-exit status 1
 -> Failed to install the following packages. Manual intervention is required:
lib32-poppler - exit status 1
```
failed karena gpg key nya tidak dipercaya. untuk kita perlu menambahkan gpg key secara manual



```
$ gpg --recv-key 3A6A4DB839EAA6D7
```

coba install lagi jika ada info `verifying gpg passed` maka error gpg sudah diperbaiki

```
==> Verifying source file signatures with gpg...
    poppler-23.05.0.tar.xz ... Passed
```
