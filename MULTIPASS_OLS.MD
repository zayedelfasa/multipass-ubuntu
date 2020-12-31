# Mencoba OPEN LITE SPEED di Multipass Ubuntu

Kali ini kita akan mencoba untuk membangun sebuah web server bernama "Open Lite Speed" di dalam sebuah server Multipass Ubuntu. 

Website resmi dari Open Lite Speed, bisa dilihat di [sini](https://openlitespeed.org).

Ada beberapa cara untuk melakukan instalasi Open Lite Speed, untuk tutorial kali ini kita akan melakukan instalasi dengan cara menambahkan repository Open Lite Speed ke dalam dafar repo ubuntu kita.

Sebelum melakukan instalasai, kita masuk dulu ke dalam server menggunakan perintah di bawah ini: 

```
$ multipass shell [nama_multipass_ubuntu]
```

## Langkah - Langkah Instalasi

1. Pertama kali dilakukan adalah menambahkan repository Open Lite Speed dengan cara di bawah ini :
```
$ wget -O - http://rpms.litespeedtech.com/debian/enable_lst_debian_repo.sh | sudo bash
```

2. Setelah itu lakukan update repository dengan cara di bawah ini : 
```
$ sudo apt update
```

3. Setelah langkah-langkah di atas selesai, maka kita bisa install Web Server-nya. 
```
$ sudo apt install openlitespeed
```

4. Setelah selesai instalasi, masih ada langkah-langkah yang perlu dilakukan untuk mencoba Web Server ini yaitu menjalankan service Open Lite Speed. Caranya seperti di bawah ini: 
```
$ sudo /usr/local/lsws/bin/lswsctrl start
```

setelah perintah di atas dijalankan, anda dapat melihat tampilannya admin di browser PC client dengan alamat : 

http://[your-ip-ubuntu-multipass]:7088


secara default, port web admin berada pada port 7088 dan port dari contoh web ada di 8088: 

http://[your-ip-ubuntu-multipass]:8088



## Setting Username dan Password Admin

Agar kita dapat masuk ke dalam web admin, kita perlu set username dan password-nya terlebih dahulu. Untuk set userame dan password, dapat menjalankan perintah di bawah ini :
```
$ sudo /usr/local/lsws/admin/misc/admpass.sh
```

Contohnya seperti di bawah ini :

Setelah username dan pssword telah diisi, kita kembali ke halaman web admin kemudian masukkan username dan password yang telah kita set tadi. Contoh gambar seperti di bawah ini :

Untuk mencoba project simple di-deploy pada Open Lite Speed, akan ditulis di bagian ke dua.