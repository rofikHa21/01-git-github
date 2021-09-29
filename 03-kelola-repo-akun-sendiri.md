# Mengelola Repositori Sendiri

## [**Halaman Awal**](README.md)

## Langkah - langkah :

### Membuat Repositori di Github

1. Membuat Repositori kosng, dengan menekan simbol **+** disamping foto profile.

<!--![01](img/03/menambah-1.jpg)-->

<img src="img/03/menambah-1.jpg" alt="01" style="width: 400px;">

2. memberi nama repositori, mengatur repositori menjadi public, dan tidak mengisi radio button

<img src="img/03/menambah-2.jpg" alt="01" style="width: 500px;">

#
### **Clone Repositori Github ke Local (Git)**

clone merupakan teknik untuk menggandakan repositori dari github ke lokal repositori, jadi user bisa melakukan edit dokumen secara offline.

perintah clone adalah `$ git clone https://github.com/username/nama-repo`

```
mrofi@LUCIENNE-IPS3 MINGW64 ~
$ git clone https://github.com/rofikHa21/awesome-project
Cloning into 'awesome-project'...
warning: You appear to have cloned an empty repository.
```

jika repositori kosong maka akan muncul warning message bahwa repositori yang di clone adalah kosong.

Setiap repo memilik cabang, nama cabang tersebut meiliki nama default yaitu `master` namun pada saat ini banyak team menggunakan `main` saebagai nama default dari repo mereka, user bisa mengaturnya saat melakukan instalasi dengan meilih pilihan kedua. bisa dilihat di [installasi git langkah ke 6](01-install-git.md).
#

### **Cara melakukan branching**

```
mrofi@LUCIENNE-IPS3 MINGW64 ~
$ cd awesome-project

mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (master)
$ git branch -m main

mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (main)
$
```
* `cd awesome-project` merupakan perintah untuk berpindah dari folder root `~` ke folder `awesome project`. Arti `cd` itu sendiri adalah _change directory_.

* Status `(master)` adalah status kita sedang berada di branch yang bernama `master`.
* perintah `git branch -m main` adalah perintah untuk mengganti nama jadi `git branch -m <master> akan berganti ke <main>` .
