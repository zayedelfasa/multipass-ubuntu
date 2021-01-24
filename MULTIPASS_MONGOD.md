# Menjalankan MongoDB pada Multipass ubuntu

1. Jika pada OS Anda belum menjalankan multipass, Anda dapat download di [sini](https://multipass.run/).

2. Jika belum ada server ubuntu pada multipass, Anda dapat mengikuti tutorial ini mengetahui apa itu multipass lebih lanjut:
https://github.com/zayedelfasa/multipass-ubuntu

Kali ini saya akan menjelaskan cara instalasi mongodb pada multipass. 

Pada dasarnya, cara instalasi mongod pada multipass sama dengan cara instalasi di linux turunan debian. Hal itu dikarenakan VM Multipass ini berisi Ubuntu yang diturunkan dari Debian.

Untuk lebih jelasnya kita akan install mongodb sekarang. Kita asumsikan bahwa kita sudah memiliki ubuntu yang sudah running. 

1. Seperti biasa, pertama-tama kita perlu masuk ke dalam ubuntunya. Perintahnya sebagai berikut:
```
$ multipass shell [nama_multipass_ubuntu]
```

**Abaikan perintah ini jika Anda sudah melakukan update dan upgrade OS Anda**


2. Setelah berhasil masuk ke dalam VM, langkah selanjutnya adalah update dan upgrade OS pada VM Multipass Anda.
```
$ sudo apt update
```

```
$ sudo apt upgrade
```

3. Jika VM Multipassnya sudah selesai upgrade, langkah selanjutnya adalah public key yg dimiliki oleh Mongo.
```
$ wget -qO - https://www.mongodb.org/static/pgp/server-4.4.asc | sudo apt-key add -
```

setelah kita enter, maka akan memberikan response "OK".

Apabila terjadi indikasi error, ada kemungkinan perlu untuk install `gnupg`. Cara install-nya sebagai berikut: 
```
$ sudo apt install gnupg
```

4. Tambahkan repo source list mongodb dengan perintah di bawah ini: 
```
$ echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/4.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list
```

Contoh output-nya seperti ini : 

```
deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/4.4 multiverse
```

5. setelah itu lakukan update repo.

```
$ sudo apt update
```

6. Setelah di-update, maka source untuk install mongodb telah tersimpan di dalam source repo. Kemudian jalankan perintah di bawah ini untuk melakukan instalasi mongodb.

```
$ sudo apt install -y mongodb-org
```

Ditunggu sampai selesai.

Kemudian kita bisa jalankan service dari mongodb dengan menggunakan perintah di bawah ini: 
```
$ sudo systemctl start mongod
```

Jika ingin melihat status dari apakah servicenya jalan atau tidak kita bisa menggunakan perintah di bawah ini : 
```
$ sudo systemctl status mongod
```

Maka akan menampilkan output seperti di bawah ini :
```
● mongod.service - MongoDB Database Server
     Loaded: loaded (/lib/systemd/system/mongod.service; disabled; vendor preset: enabled)
     Active: active (running) since Sat 2021-01-23 22:17:39 WIB; 11s ago
       Docs: https://docs.mongodb.org/manual
   Main PID: 2399 (mongod)
     Memory: 62.8M
     CGroup: /system.slice/mongod.service
             └─2399 /usr/bin/mongod --config /etc/mongod.conf

Jan 23 22:17:39 mongod systemd[1]: Started MongoDB Database Server.
```

Jika status `Active` bertuliskan `active (running)` maka mongodb telah berjalan dengan baik.