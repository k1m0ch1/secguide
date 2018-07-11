# General Security Development guide - Indonesia

> Poin poin dibawah ini masih dalam urutan acak

Legend :
:zap: : Level Mudah untuk implementasi 
:ocean: : Level Mudah untuk implementasi 
:pray: : Level Susah untuk implementasi
note, level dilihat dari developer dengan minim pengalaman security dev

## Web Server

- [ ] Enable Header `X-XSS-Protection`, best config : "X-XSS-Protection: 1; mode=block"
- [ ] Enable Header `X-Frame-Options`, best config : "X-Frame-Options "SAMEORIGIN" always"
- [ ] Enable Header `X-Content-Type-Options`, best config : "X-Content-Type-Options "nosniff" always"
- [ ] Enable Header `Content-Security-Policy`
- [ ] Enable Header `Referrer-Policy`
- [ ] Untuk konfigurasi SSL gunakan `TLS v1`, `TLS v1.1` dan `TLS v1.2`
- [ ] Jangan gunakan `TLS v3`
- [ ] Jangan remote SSH Login menggunakan root 
- [ ] Batasi besar file pada saat upload
- [ ] Selalu periksa direktori file upload tidak ada file yang mencurigakan ( bisa pake backdoor scanner https://github.com/RomelSan/website-findbackdoor atau https://github.com/djeraseit/PHP-backdoor-detector simple tapi powerfull )
- [ ] Matikan Directory Listing
- [ ] Disable akses public `robot.txt` (jika dibutuhkan)
- [ ] Disable X-powered-by web server

## Development Application

- [ ] Jangan gunakan GET method untuk mengirimkan data yang sensitif
- [ ] Hapus/ Matikan Experiment plugin
- [ ] Segala resource yang berhubungan dengan data sensitif, seperti data pesanan, jurnal transaksi ataupun reedem voucher, cek terlebih dahulu kevalidan user nya real atau tidak. 
- [ ] Pastikan tidak ada file backup (`.bak`) disetiap file development
- [ ] Tidak membuat file archive berisi backup program yang dapat di akses secara publik
- [ ] Hapus Routes yang ga dipake (menghindari routes scanner oleh hacker)
- [ ] HTML input type autocomplete=off
- [ ] Error handling tidak menampilkan pesan debug pada production

#### Version Control (Repository)

- [ ] Periksa Kelemahan repository (free tools https://snyk.io/)
- [ ] Jangan commit data api key, password, secret key secara hard code, gunakan environment variable

#### Authentication

- [ ] Gagal login lebih prefer menggunakan pesan "Kombinasi User atau password salah", jangan memberikan petunjuk jika password salah atau user tidak terdaftar

#### Input Data

- [ ] Sanitize input data pada saat update profile yang akan ditampilkan lagi datanya pada user
- [ ] Sanitize Input search
- [ ] Sanitize File name setelah file di upload
- [ ] Validasi file dilihat dari ekstensi file dan content file cocok (`EXIF`)
- [ ] Sanitize `EXIF` data pada saat upload file gambar

#### SQL Query

- [ ] DB Queries disarankan menggunakan `prepared statement`

## Password

- [ ] Rubah password default ( bisa cek ke https://lowe.github.io/tryzxcvbn/ untuk cek password strength )
- [ ] Gunakan enkripsi `Bcrypt` untuk password ( kenapa bcrypt ? baca https://goo.gl/vA3FJE )

## Online Generator

- [ ] jangan pernah melakukan generate hash secara online ( karena secara tidak langsung password akan di store dimanfaatkan hacker untuk decrypting hash)
- [ ] jangan pernah melakukan pengecekan password secara online di website yg tidak di percaya ( contoh trusted : https://password.kaspersky.com/ )

## Database

- [ ] Jangan pasang WEB IDE DB (ex: phpmyadmin) di server production ( jika benar benar butuh gunakan basic auth untuk akses ke phpmyadmin )
- [ ] Tidak membuat database backup yang dapat di akses secara publik