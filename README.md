<div align="center">
<img src="https://assets.ubuntu.com/v1/c87ec87a-Multipass-header-option_crop.png" width="30%" height="30%" alt="bar"/>
</div>
<div align="center">
<h1>Easy Multipass<h1>
</div>
  
# VMs Multipass Ubuntu untuk membuat server lokal secara instant

Multipass adalah salah satu solusi mesin virtual server ubuntu dalam bentuk service yang dapat berjalan di atas sistem operasi. 

Buat saya sendiri, dengan adanya service multipass ini, saya dapat membuat server sederhana di PC saya dengan tujuan riset. Jadi, apabila riset gagal dilakukan, maka Ubuntu server yang sudah saya buat tadi, dapat dihapus dengan mudah dan dapat dibuat kembali.

Untuk Penjelasan tentang multipass ada di [sini](https://multipass.run/)

### Contoh deploy dan penggunaan multipass:
1. [Install .NET Core](https://github.com/zayedelfasa/multipass-ubuntu/blob/main/MULTIPASS_DOTNETCORE.md).
2. [Install ReactJs](https://github.com/zayedelfasa/multipass-ubuntu/blob/main/MULTIPASS_REACT.md).
3. [Install Open Lite Speed](https://github.com/zayedelfasa/multipass-ubuntu/blob/main/MULTIPASS_OLS.MD)

### Download multipass: 
- Windows https://multipass.run/download/windows
- Mac https://multipass.run/download/macos
- Ubuntu https://snapcraft.io/multipass

### Cara penggunaan
Ketika sudah selesai di-download, kita perlu tambahkan Sistem Operasi Ubuntu. Caranya seperti di bawah ini:

```
$ multipass launch --name ubuntu-riset
```

<div>
<img src="https://github.com/zayedelfasa/multipass-ubuntu/blob/main/main_readme/main-1.png" width="50%" height="50%" alt="bar"/>
</div>
Perintah tersebut akan menambahkan satu image ubuntu yang bernama "ubuntu-riset". Perlu waktu ketika menjalankan perintah ini karena image di-download.

Setelah selesai download, Ubuntu server tersebut secara otomatis dibuat dan sudah siap digunakan. Cara untuk melihat image Ubuntu tersebut, kita dapat menjalankan perintah di bawah ini : 

```
$ multipass list
```

<div>
<img src="https://github.com/zayedelfasa/multipass-ubuntu/blob/main/main_readme/main-2.png" width="50%" height="50%" alt="bar"/>
</div>

Perintah tersebut akan menampilkan list image yang sudah kita buat. 

Setelah itu, apabila kita ingin mencoba untuk menjalankan perintah pada server tersebut, kita dapat menjalankan perintah seperti di bawah ini : 


```
$ multipass exec ubuntu-riset -- ls -la
```

<div>
<img src="https://github.com/zayedelfasa/multipass-ubuntu/blob/main/main_readme/main-3.png" width="50%" height="50%" alt="bar"/>
</div>

Perintah tersebut akan memberikan perintah pada server ubuntu buatan kita untuk menampilkan semua file dan folder yang ada pada lokasi home. Anda bisa mengganti perintah linux ubuntu yg lainnya setelah tanda "--" di atas.

Agar kita bisa masuk ke dalam server ubuntu yang telah kita buat, kita dapat menggunakan perintah ini :

```
$ multipass shell ubuntu-riset 
```

<div>
<img src="https://github.com/zayedelfasa/multipass-ubuntu/blob/main/main_readme/main-4.png" width="50%" height="50%" alt="bar"/>
</div>

Setelah kita menjalankan perintah tersebut, maka kita telah masuk ke dalam sistem ubuntu. Di sinilah Anda bisa melakukan otak-atik server. 

Setelah mencoba server kemudian server ingin dihapus, kita dapat menjalankan perintah ini: 

```
$ multipass delete ubuntu-riset
```

Kemudian lanjutkan dengan : 


```
$ multipass purge
```

Maka image akan terhapus.

Jika ingin melihat perintah `multipass` yang lainnya, Anda dapat melihatnya di sini: 

```
$ multipass help
```

Sekian. Zayed Elfasa
