# Menjalankan Reactjs dalam Server Ubuntu Multipass

Kali ini saya akan menjalankan web reactjs di dalam Server Ubuntu lokal melalui multipass. Pada dasarnya cara install reactjs di server ubuntu melalui multipass sama dengan ketika kita install reactjs di Ubuntu Desktop.

Kebutuhan untuk install reactjs terdiri dari :
- Nodejs  
- NPM 

### Instalasi
* note : nama image saya untuk tutorial kali ini adalah `ubuntu-react`.
Pastikan Server Ubuntu Lokal telah ada di PC Anda. Jika Belum, bisa buat dulu. Caranya ada di [sini](https://github.com/zayedelfasa/multipass-ubuntu/blob/main/README.md).

Semua perintah 

Setelah itu lakukan update repository ubuntu dengan cara berikut : 

```
$ multipass exec ubuntu-react -- sudo apt update
```

Setelah itu lakukan instalasi nodejs dan npm seperti di bawah ini: 

* nodejs
```
$ multipass exec ubuntu-react -- sudo apt install nodejs
```

* npm
```
$ multipass exec ubuntu-react -- sudo apt install npm
```

Setelah semua perintah di atas telah di eksekusi, langkah selanjutnya adalah membuat reactjs dengan menggunakan perintah npx: 
```
$ multipass exec ubuntu-react -- npx create-react-app multipass-react
```

Perintah di atas mendefinisikan bahwa kita telah membuat sebuah project reactjs bernama `multipass-react` yang letaknya berada di `home`. Setelah itu kita perlu masuk ke dalam folder `multipass-react`. Untuk perintah ini (masuk ke dalam folder project `multipass-react`), mari kita masuk langsung ke dalam ubuntu dengan menggunakan perintah di bawah ini :

```
$ multipass shell ubuntu-react 
```

maka kita akan memasuki server ubuntu. kemudian masuk ke dalam folder `multipass-react` yang lokasinya add di home: 

```
$ cd multipass-react
```

setelah itu kita jalankan project react. 

```
$ npm start
```

Untuk mencobanya, kita bisa langsung akses de dalam PC kita dengan cara akses IP dari server ubuntu. Contoh IPnya seperti gambar di bawah ini:

Sekian. Terima kasih.