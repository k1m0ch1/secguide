## General Security Developer guide - Indonesia

> Poin poin dibawah ini masih dalam urutan acak

- [ ] Jangan gunakan GET method untuk mengirimkan data yang sensitif
- [ ] Enable Header `X-XSS-Protection`, best config : "X-XSS-Protection: 1; mode=block"
- [ ] Enable Header `X-Frame-Options`, best config : "X-Frame-Options "SAMEORIGIN" always"
- [ ] Enable Header `X-Content-Type-Options`, best config : "X-Content-Type-Options "nosniff" always"
- [ ] Enable Header `Content-Security-Policy`
- [ ] Enable Header `Referrer-Policy`
- [ ] Untuk konfigurasi SSL gunakan `TLS v1`, `TLS v1.1` dan `TLS v1.2`
- [ ] Jangan gunakan `TLS v3`
- [ ] Jangan SSH Login menggunakan root 
- [ ] Rubah password default
- [ ] Jangan simpan api key, password, secret key secara hard code, gunakan environment variable
- [ ] Gunakan enkripsi `Bcrypt` untuk password
- [ ] Jangan pasang phpmyadmin di server production ( jika perlu gunakan basic auth untuk akses ke phpmyadmin )
- [ ] Gagal login menggunakan pesan "Kombinasi User atau password salah", jangan memberikan petunjuk jika password salah atau user tidak terdaftar
- [ ] Batasi besar file pada saat upload
- [ ] Selalu periksa direktori file upload tidak ada file yang mencurigakan
- [ ] Periksa Kelemahan di dependencies
- [ ] Hapus/ Matikan Experiment plugin
- [ ] Matikan Directory Listing
- [ ] Segala resource yang berhubungan dengan data sensitif, seperti data pesanan, jurnal transaksi, reedem voucher cek terlebih dahulu jika user yang sedang melakukan hal tersebut 
- [ ] Sanitize File name setelah file di upload
- [ ] Validasi file dilihat dari ekstensi file dan content file cocok
- [ ] Disable akses public `robot.txt` 
- [ ] Sanitize `EXIF` data pada saat upload file gambar
- [ ] Sanitize input data pada saat update profile yang akan ditampilkan lagi datanya pada user
- [ ] Sanitize Input search
- [ ] Pastikan tidak ada file backup (`.bak`) disetiap file 
- [ ] Tidak membuat file archive berisi backup program yang dapat di akses secara publik
- [ ] Tidak membuat database backup yang dapat di akses secara publik
- [ ] Disable X-powered-by
- [ ] Hapus Routes yang ga dipake
- [ ] HTML input type autocomplete=off
- [ ] Error handling tidak menampilkan pesan debug
- [ ] DB Queries disarankan menggunakan `prepared statement`