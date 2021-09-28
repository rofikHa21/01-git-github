# Konfigurasi Git

[**Halaman Awal**](README.md)

Saat mengkonfigurasi git user bisa melakukan nya dengan 2 cara bisa menggunakan cli dengan menuliskan :
```
$ git config --global user.name "Nama Anda di GitHub"
$ git config --global user.email email@domain.tld
```

pada bagian user.name user akan mengisi dengan username pada akun  github (_tanpa  menggunakan tanda kutip_), dan untu user.email user akan mengisi dengan akun email yang terdaftar dengan aku github.

Atau user bisa juga dengan mencari letak file config nya di Drive C: dengan path **C:\Users\nama-user**, akan ada file bernama **.gitconfig**, kemudian kilik dua kali maka akan langsung membuka file config tersebut, user tinggal mengedit kolom :

```
[user]
	name = username
	email = email@domain.tld
```

jika sudah mengedit file config user bisa melihat nya dengan membuka git bash kemudian ketikkan : 
`git config --list`

maka akan tampil : 
```
$ git config --list
user.name=username
user.email=email@domain.tld
```

[**Halaman Awal**](README.md)