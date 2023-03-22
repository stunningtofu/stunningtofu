---
title: "Cara memasang Zsh sebagai default shell"
date: 2023-03-22T14:26:17+07:00
draft: false
---

# Cara memasang Zsh sebagai default shell

Zsh adalah sebuah shell (intepreter perintah) untuk terminal di sistem operasi Linux dan Unix. Zsh dapat digunakan untuk menggantikan shell bawaan sistem operasi seperti bash atau ksh. Zsh memiliki banyak fitur dan dapat dikostumisasi dengan mudah, seperti otomatisasi perintah, penyelesaian otomatis, dan tema yang dapat disesuaikan. Zsh juga memiliki banyak plugin yang tersedia untuk membantu memperpanjang fungsionalitasnya.

Zsh adalah sebuah shell atau intepreter perintah untuk terminal di sistem operasi linux atau unix, zsh untuk sekarang masih belum berfungsi ya di cmd windows, kalau di sistem operasi windows bisa menggunakan [WSL](https://learn.microsoft.com/en-us/windows/wsl/), tapi ujungnya sih linux juga hehe.

Kenapa saya memerlukan ini, karena dengan fitur yang disediakan bisa membantu jika bekerja menggunakan zsh, sebenarnya ada lagi seperti fish cuma ini yang dibahas zsh ya. Contohnya perintah yang sebelumnya sudah pernah dibuat bisa langsung muncul dan digunakan lagi tanpa harus mencari di history atau mengingatnya. Zsh juga memiliki banyak plugin maupun tema, kalau untuk lengkapnya bisa mampir ke web officialnya ya

Langsung saja ke kebutuhannya untuk memasang shell Zsh:

1. [Install cURL dan Zsh](https://www.notion.so/Cara-memasang-Zsh-sebagai-default-shell-4d59cd65cdd24dd89475b6dce6f7aa6e)
2. [Install zsh quick install atau manual](https://www.notion.so/Cara-memasang-Zsh-sebagai-default-shell-4d59cd65cdd24dd89475b6dce6f7aa6e)
3. [Install Antibody](https://www.notion.so/Cara-memasang-Zsh-sebagai-default-shell-4d59cd65cdd24dd89475b6dce6f7aa6e)

# Install cURL dan Zsh

curl digunakan untuk mengunduh file dari halaman tertentu menggunakan terminal, singkatan dari curl sendiri “Client URL”.

Penjelasan Zsh sendiri sudah dijelaskan sebelumnya, untuk sekarang kenapa di install agar konfigurasi yang sudah dibuat bisa dijalankan di sistem operasi.

```bash
$ sudo apt-get install curl
$ sudo apt-get install zsh
$ sudo apt-get update
```

penggunakan update agar package terbaru yang sudah terpasang bisa terbaca.

Setelah zsh terpasang bukan berarti zsh bisa langsung digunakan, bisaaa tetapi jika menutup terminal maka akan kembali ke shell yang sebelumnya. Maka baiknya dicek dulu versinya untuk mengetahui apakah sudah terpasang.

- check curl & zsh version

```bash
$ curl --version
curl 7.81.0 (x86_64-pc-linux-gnu) libcurl/7.81.0 OpenSSL/3.0.2 zlib/1.2.11 brotli/1.0.9 zstd/1.4.8 libidn2/2.3.2 libpsl/0.21.0 (+libidn2/2.3.2) libssh/0.9.6/openssl/zlib nghttp2/1.43.0 librtmp/2.3 OpenLDAP/2.5.13
Release-Date: 2022-01-05
$ zsh --version
zsh 5.8.1 (x86_64-ubuntu-linux-gnu)

<-- untuk masuk ke zsh sementara -->
$ zsh
```

# Install zsh ***************quick install*************** & *manual*

## Install zsh (quick install)

Quick install atau bisa disebut menginstall dengan cepat hehe, dengan perintah seperti dibawah ni tidak perlu untuk mencari file zsh dan mengganti bash shell secara manual.
Jika sebelumnya sudah berhasil menginstall curl dan zsh maka perintah dibawah ini akan langsung jalan, jadi curl akan mengunduh file yang sudah disediakan oleh zsh, lalu sudah ada excute shell di dalam file [install.sh](http://install.sh).

```bash
$ sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## I**nstall zsh manual**

mengetahui dimana letak zsh di pasang.

```bash
$ which zsh
/usr/bin/zsh -> output
```

Perintah `chsh` untuk mengubah shell yang akan digunakan, perintah `-s` digunakan untuk mengatur sebagai default shell, perintah `which zsh` memberitahu tempat shell yang akan dijadikan rujukan dimana tempat shell yang akan digunakan sebagai default.

```bash
$ chsh -s $(which zsh)
```

## Install antibody

Antibody adalah salah satu plugin manager untuk zsh. Dengan menggunakan antibody, pengguna lebih mudah untuk mengelola plugin zsh lainnya tanpa harus melakukan konfigurasi tambahan. Karena jika memasang plugin lainnya tanpa mengunakan antibody prosesnya lebih panjang jadi saya memilih ini untuk mempersingkat proses konfigurasinya.

```bash
$ curl -sfL git.io/antibody | sudo sh -s - -b /usr/local/bin
```

- check antibody version

```bash
$ antibody --version                               
antibody version 6.1.1
```

# Plugins file

Berikut perintah yang saya gunakan didalam file yang akan dijalankan oleh antibody. Plugin yang saya gunakan hanya seperlunya saja, karena jika terlalu banyak plugin zsh sendiri agan menjadi lambat untuk dijalankan. Untuk pluginnya apa saja tidak saya jelaskan ya hehe bisa dicopy persatuan jika ingin mengetahui lebih lanjut kegunaan dari setiap plugin yang saya gunakan.

Buat file `.zsh_plugin.txt` di home dengan menggunakan editor kesukaan kalian saya lebih suka nano atau vim, lalu paste didalam file tersebut jangan lupa disimpan.

```bash
$ vim .zsh_plugin.txt
```

- example ~/.zsh_plugins.txt

```bash
#robbyrussel oh-my-zsh
robbyrussell/oh-my-zsh path:plugins/colored-man-pages
robbyrussell/oh-my-zsh path:plugins/extract
robbyrussell/oh-my-zsh path:plugins/z
robbyrussell/oh-my-zsh path:lib/history.zsh
robbyrussell/oh-my-zsh path:lib/key-bindings.zsh
robbyrussell/oh-my-zsh path:lib/git.zsh
robbyrussell/oh-my-zsh path:themes/jnrowe.zsh-theme

#external plugins
zsh-users/zsh-completions
zsh-users/zsh-history-substring-search
zsh-users/zsh-autosuggestions
zdharma/fast-syntax-highlighting
caarlos0/zsh-mkc
```

- standar penggunaan untuk pengisian didalam file yang akan dijalankan oleh antibody

`robbyrussel/oh-my-zsh` ⇒ *username/repository*

`plugins/color-man-pages` ⇒ *path plugins, names plugins will use*

`zsh-users/zsh-compeltions` ⇒ *username/repository*

Di dalam antibody sendiri terdapat 2 macam untuk konfigurasi plugin yaitu ****************dynamic loading**************** & ***************static loading.*************** Saya lebih memilih static loading karena antibody akan dijalankan dengan updatean terakhir yang sudah terpasang, antibody akan terupdate jika kita memperbarui, jika menggunakan dynamic loading antibody akan memperbarui versi terbaru jadi akan terkesan lebih lama untuk menjalankan terminal pertama kali.

## Insert Antibody in ~/.zshrc

Agar plugin yang sudah dijalankan, perlu dimasukkan perintah antibody didalam file `.zshrc` 

```bash
$ find .zshrc
.zshrc
$ nano .zshrc
<--paste konfigurasi antibody lalu simpan-->
```

- file antibody yang akan di paste di dalam file `.zshrc`

```bash
#user conf
#antibody conf
antibody bundle < ~/.zsh_plugins.txt > ~/.zsh_plugins.sh 
source ~/.zsh_plugins.sh
```

Sudah selesai, ohmyzsh bisa digunakan untuk membantumu menggunakan terminal.

Sebenarnya didalam linux sendiri sudah ada shell defaultnya yaitu bash, menurut saya shell ini kurang lengkap untuk fiturnya, perlu di otak atik lagi saya kurang tertarik. Saya lebih memilih zsh karena saya bisa memilih plugin sesuai kebutuhan saya, lalu untuk pilihan tema lebih banyak membuat terminal lebih berwarna tetapi lagi, sesuaikan dengan kebutuhan jika jarang menggunakan terminal tidak perlu menggunakan shell ini karena jarang terpakai bukan.