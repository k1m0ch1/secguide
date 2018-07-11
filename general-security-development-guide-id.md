# General Security Development guide - Indonesia

> Poin poin dibawah ini masih dalam urutan acak

Legend :
- :zap: : Level Mudah untuk implementasi 
- :ocean: : Level Biasa untuk implementasi 
- :pray: : Level Susah untuk implementasi
note, level dilihat dari developer dengan minim pengalaman security dev

## Web Server

- [ ] :zap: Enable Header `X-XSS-Protection`, best config : "X-XSS-Protection: 1; mode=block"
- [ ] :zap: Enable Header `X-Frame-Options`, best config : "X-Frame-Options "SAMEORIGIN" always"
- [ ] :zap: Enable Header `X-Content-Type-Options`, best config : "X-Content-Type-Options "nosniff" always"
- [ ] :zap: Enable Header `Content-Security-Policy`
- [ ] :zap: Enable Header `Referrer-Policy`
- [ ] :zap: Untuk konfigurasi SSL gunakan `TLS v1`, `TLS v1.1` dan `TLS v1.2`
- [ ] :zap: Jangan gunakan `TLS v3`
- [ ] :zap: Jangan remote SSH Login menggunakan root 
- [ ] :zap: Batasi besar file pada saat upload
- [ ] :ocean: Selalu periksa direktori file upload tidak ada file yang mencurigakan ( bisa pake backdoor scanner https://github.com/RomelSan/website-findbackdoor atau https://github.com/djeraseit/PHP-backdoor-detector simple tapi powerfull )
- [ ] :ocean: Matikan Directory Listing
- [ ] :zap: Disable akses public `robot.txt` (jika dibutuhkan)
- [ ] :pray: Disable X-powered-by web server

## Application Development

- [ ] :zap:Jangan gunakan GET method untuk mengirimkan data yang sensitif
- [ ] :zap: Hapus/ Matikan Experiment plugin
- [ ] :ocean: Segala resource yang berhubungan dengan data sensitif, seperti data pesanan, jurnal transaksi ataupun reedem voucher, cek terlebih dahulu kevalidan user nya real atau tidak. 
- [ ] :zap: Pastikan tidak ada file backup (`.bak`) disetiap file development
- [ ] :zap: Tidak membuat file archive berisi backup program yang dapat di akses secara publik
- [ ] :zap: Hapus Routes yang ga dipake (menghindari routes scanner oleh hacker)
- [ ] :zap: HTML input type autocomplete=off
- [ ] :zap: Error handling tidak menampilkan pesan debug pada production

#### Version Control (Repository)

- [ ] :zap: Periksa Kelemahan repository (free tools https://snyk.io/)
- [ ] :zap: Jangan commit data api key, password, secret key secara hard code, gunakan environment variable

#### Authentication

- [ ] :zap: Gagal login lebih prefer menggunakan pesan "Kombinasi User atau password salah", jangan memberikan petunjuk jika password salah atau user tidak terdaftar

#### Input Database

- [ ] :ocean: Sanitize input data pada saat update profile yang akan ditampilkan lagi datanya pada user
- [ ] :ocean: Sanitize Input search
- [ ] :ocean: Sanitize File name setelah file di upload
- [ ] :ocean: Validasi file dilihat dari ekstensi file dan content file cocok (`EXIF`)
- [ ] :pray: Sanitize `EXIF` data pada saat upload file gambar

#### SQL Query

- [ ] :ocean: DB Queries disarankan menggunakan `prepared statement`

#### Wordpress 

- [ ] :zap: Selalu update versi wordpress
- [ ] :zap: Selalu update plugin yang terinstall
- [ ] :zap: Hapus Plugin yang sudah tidak di dukung
- [ ] :zap: Best Security Wordpress Plugin ( https://goo.gl/MbBRZL )
- [ ] :ocean: Wordpress vulnerability scanner (paling mudah untuk cari kelemahan)
- [ ] :zap: Follow hashtag #wpvulndb di twitter untuk update vulnerable (https://twitter.com/hashtag/wpvulndb)
- [ ] :zap: Gunakan email untuk login, jangan pake username
- [ ] :zap: Gunakan 2 Factor Authentication ( Google Authenticator )
- [ ] :zap: Gunakan email untuk login, jangan pake username
- [ ] :ocean: Custom error message ( https://goo.gl/q77QUb )
- [ ] :ocean: Disable WP REST API jika tidak di gunakan (https://wordpress.org/plugins/disable-json-api/)


## Password

- [ ] :zap: Rubah password default ( bisa cek ke https://lowe.github.io/tryzxcvbn/ untuk cek password strength )
- [ ] :zap: Gunakan enkripsi `Bcrypt` untuk password ( kenapa bcrypt ? baca https://goo.gl/vA3FJE )

## Online Generator

- [ ] :zap: jangan pernah melakukan generate hash secara online ( karena secara tidak langsung password akan di store dimanfaatkan hacker untuk decrypting hash)
- [ ] :zap: jangan pernah melakukan pengecekan password secara online di website yg tidak di percaya ( contoh trusted : https://password.kaspersky.com/ )

## Database

- [ ] :ocean: Jangan pasang WEB IDE DB (ex: phpmyadmin) di server production ( jika benar benar butuh gunakan basic auth untuk akses ke phpmyadmin )
- [ ] :zap: Tidak membuat database backup yang dapat di akses secara publik