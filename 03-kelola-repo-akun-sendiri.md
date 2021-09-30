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

```bash
mrofi@LUCIENNE-IPS3 MINGW64 ~
$ git clone https://github.com/rofikHa21/awesome-project
Cloning into 'awesome-project'...
warning: You appear to have cloned an empty repository.
```

jika repositori kosong maka akan muncul warning message bahwa repositori yang di clone adalah kosong.

Setiap repo memilik branch, nama branch tersebut meiliki nama default yaitu `master` namun pada saat ini banyak team menggunakan `main` saebagai nama default dari repo mereka, user bisa mengaturnya saat melakukan instalasi dengan meilih pilihan kedua. bisa dilihat di [installasi git langkah ke 6](01-install-git.md).
#

### **Cara melakukan branching**

```bash
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

#
## Mengelola Repositori

### Mengubah isi, push tanpa merging.

Biasanya jika pengguna linux / BSD akan sudah terinstall default text editor vim untuk melakukan edit file dari repositori.

untuk **vim** dapat menggunakan perintah `vim README.md`.

Apabila untuk pengguna Windows bisa menggunakan **VsCode**, untuk caranya yaitu menggunakan perintah `code README.md`.


```bash
mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (main)
$ code README.md
mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (main)
$ cat README.md

# My Awesome Project
```

* Perintah `cat` diatas adalah untuk melihat isi dari sebuah dokumen tanpa harus membuka editor.


```bash
mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (main)
$ git status
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md

nothing added to commit but untracked files present (use "git add" to track)

mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (main)
$ git add -A
```

* perintah `git status` berguna untuk melihat status dari repo lokal apakah user melakukan perubahan pada repositori tersebut atau tidak, jika terdapat tulisan `Untracked files` berarti user belum memasukkan perubahan dari repo tersebut kedalam antrean.
 Maka akan muncul saran untuk melakukan perintah `git add` untuk menambahkan modifikasi-modifikasi apa saja yang sudah dilakukan ke repo ke dalam index/antrean, dan selanjutnya akan dilakukan _commit_.


```bash
mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (main)
$ git commit -m "Add: README.md"
[main (root-commit) 59eb69a] Add: README.md
 1 file changed, 1 insertion(+)
 create mode 100644 README.md

mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (main)
$ git push origin main
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 242 bytes | 242.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/rofikHa21/awesome-project
 * [new branch]      main -> main
```

* `git commit -m "<pesan commit>"` berfungsi untuk merekam perubahan - perubahan yang sudah terjadi pada repo. `-m` merujuk kepada pesan apa yang akan ditulis

* `git push origin main` adalah perintah yang berguna untuk mengupdate atau mengirim perubahan file setelah di _commit_ di local repositori ke remote repositori, untuk `origin` adalah nama default dari remote, `main` adalah nama branch.

#

### Mengubah Isi Dengan Branching dan Merging

Dengan menggunakan cara ini, setiap kali akan melakukan perubaham, perubahan itu dilakukan di komputer lokal dengan membuat suatu cabang yang nantinya digunakan untuk menampung perubahan-perubahan tersebut. Setelah itu, branch itu yang akan dikirim ke repo GitHub untuk dimintai review kemudian digabungkan `merge` ke main. Secara umum, repo yang dibuat biasanya sudah mempunyai satu branch yang disebut dengan `main`. Cara ini lebih aman, terstruktur, terkendali, dan mempunyai history yang lebih baik. Jika perubahan yang kita buat sudah terlalu kacau dan kita menyesal, maka ada cara untuk "membersihkan" repo lokal kita. Secara umum, langkahnya adalah sebagai berikut:

1. Membuat branch untuk melakukan peribahan - perubahan.
2. Melakukan perubahan - perubahan.
3. Add dan commit ke branch
4. kembali ke repo main.
5. melakukan push ke remote dari branch `edit-readme-1`.
6. membuat pull request di github
7. kemudian di merge pull request di github
8.  Merge branch ke main
9. Selesai


```bash
mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (main)
$ git checkout -b edit-readme-1
Switched to a new branch 'edit-readme-1'

mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (edit-readme-1)
$ code README.md

mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (edit-readme-1)
$ cat README.md
# My Awesome Project

Ini isi proyek
```
* perintah `git checkout -b edit-readme-1` untuk membuat branch baru yang bernama `edit-readme-1` .

```bash
mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (edit-readme-1)
$ git status
On branch edit-readme-1
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")

mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (edit-readme-1)
$ git add -A

mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (edit-readme-1)
$ git commit -m "Add: Isi README.md"
[edit-readme-1 7452706] Add: Isi README.md
 1 file changed, 3 insertions(+), 1 deletion(-)


mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (edit-readme-1)
$ git checkout main
Switched to branch 'main'
Your branch is based on 'origin/master', but the upstream is gone.
  (use "git branch --unset-upstream" to fixup)

mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (main)
$ git branch --unset-upstream
mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (main)
$ git status
On branch main
nothing to commit, working tree clean
```
* `git branch --unset-upstream` befungsi untuk menghilangkan informasi upstream untuk nama branch apabila tidak ada branch yang ditentukan, defaultnya adalah branch saat ini.

```bash
mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (main)
$ git push origin edit-readme-1
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Writing objects: 100% (3/3), 293 bytes | 293.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote:
remote: Create a pull request for 'edit-readme-1' on GitHub by visiting:
remote:      https://github.com/rofikHa21/awesome-project/pull/new/edit-readme-1
remote:
To https://github.com/rofikHa21/awesome-project
 * [new branch]      edit-readme-1 -> edit-readme-1
```
* Apabila push sudah dilakukan pada branch edit-readme-1, maka kita tinggal melakukan **pull request** pada Github.

 1. akan muncul notikasi pada tab **Code**, klik **Compare and pull request**.

 ![01](img/pr/pr-1.jpg)

 2. megisi kolom komentar untuk pull request.
 
 ![02](img/pr/pr-2.jpg)

 3. ketika tidak terdeteksi konflik pada saat pull request, maka klik **Merge pull request**.

 ![03](img/pr/pr-3.jpg)

Setelah itu, `Confirm Merge`, branch yang kita kirimkan tadi sudah dimasukkan ke branch `main`. Setelah itu, merge di komputer lokal:

 ```bash
mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (main)
$ git merge edit-readme-1
Updating 59eb69a..7452706
Fast-forward
 README.md | 4 +++-
 1 file changed, 3 insertions(+), 1 deletion(-)

mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (main)
$ git branch
  edit-readme-1
* main

mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (main)
$ git branch -D edit-readme-1
Deleted branch edit-readme-1 (was 7452706).

mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (main)
$ git branch
* main
 ```

* Perintah `git merge` berfungsi untuk menggabungkan riwayat" perubahan dari dua cabang atau lebih, atau menggabungkan cabang-cabang tersebut.
* `git branch` berfungsi untuk mengecek daftar dari cabang yang ada.

```bash
mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (main)
$ git pull
remote: Enumerating objects: 1, done.
remote: Counting objects: 100% (1/1), done.
remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (1/1), 629 bytes | 209.00 KiB/s, done.
From https://github.com/rofikHa21/awesome-project
   59eb69a..dc8ebe7  main       -> origin/main
There is no tracking information for the current branch.
Please specify which branch you want to merge with.
See git-pull(1) for details.

    git pull <remote> <branch>

If you wish to set tracking information for this branch you can do so with:

    git branch --set-upstream-to=origin/<branch> main

mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (main)
$ git branch --set-upstream-to=origin/main main
Branch 'main' set up to track remote branch 'main' from 'origin'.

mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (main)
$ git pull
Updating 7452706..dc8ebe7
Fast-forward
```

### Sinkronasi

Ketika kita berpindah dari komputer satu ke komputer lain ketika mengelola repositori lokal, kita perlu melakukan sinkronasi agar repositori yang dikelola tidak berantakan, atau masih sama seperti saat di komputer sebelumnya. Perintah sinkronasi :

```bash
$ git pull
```

### Membatalkan Perubahan

* **Langkah - Langkah** : 

1. Membuat cabang / branch terlebih dahulu.
2. Melakukan perubahan - perubahan.

```bash
mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (main)
$ git checkout -b edit-readme-2
Switched to a new branch 'edit-readme-2'

mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (edit-readme-2)
$ code README.md

mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (edit-readme-2)
$ cat README.md
# My Awesome Project

Ini isi proyek. Jadi agak kacau nih
```
3. Kembali lagi ke cabang utama (`main`).

```bash
mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (edit-readme-2)
$ git checkout main
Switched to branch 'main'
M       README.md
Your branch is up to date with 'origin/main'.

mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (main)
$ cat readme.md
# My Awesome Project

Ini isi proyek. Jadi agak kacau nih
```
4. Apabila dokumen dirasa menjadi berantakan setelah mengalami perubahan, maka cabang tersebut bisa dihapus menggunakan `git branch -D <nama cabang>`.
5. Pastikan bahwa cabang tersebut sudah benar - benar terhapus, Untuk melihat cabang `git branch`.
```bash
mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (main)
$ git branch -D edit-readme-2
Deleted branch edit-readme-2 (was dc8ebe7).

mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (main)
$ git branch
* main

mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (main)
$ cat readme.md
# My Awesome Project

Ini isi proyek. Jadi agak kacau nih
```
6. Melakukan perintah `git reset --hard` untuk mengatur ulang index dan working tree. sehingga direktori akan benar-benar bersih dengan menggunakan perintah tersebut.

7. Selesai.
```bash
mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (main)
$ git reset --hard
HEAD is now at dc8ebe7 Merge pull request #1 from rofikHa21/edit-readme-1

mrofi@LUCIENNE-IPS3 MINGW64 ~/awesome-project (main)
$ cat README.md
# My Awesome Project

Ini isi proyek
```
