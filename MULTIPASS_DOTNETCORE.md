# Menjalankan .NET core dan deploy API di Ubuntu Server Multipass

Kali ini saya akan menjalankan .NET core dan deploy contoh API yang dibuat pada multipass ubuntu.

1. Jika pada OS Anda belum menjalankan multipass, Anda dapat download di [sini](https://multipass.run/).

2. Jika belum ada server ubuntu pada multipass, Anda dapat mengikuti tutorial ini mengetahui apa itu multipass lebih lanjut:
https://github.com/zayedelfasa/multipass-ubuntu

Jika dua persyaratan di atas telah dipenuhi, kita akan melanjutkan step yang berikutnya yaitu menjalankan SDK .NET core pada ubuntu multipass.

1. Instal .NET Core di linux. 
Pertama kita perlukan adalah SDK dari .NET Core yang bisa di download dengan menggunakan curl. Kita asumsikan, saat ini kita sudah berada di dalam ubuntu. Untuk download SDK .NET Core, kita bisa download dengan menggunakan perintah curl. 
```
$ curl -o dotnetcore-3.1.tar.gz https://download.visualstudio.microsoft.com/download/pr/fdd9ecec-56b4-40f4-b762-d7efe24fc3cd/ffef51844c92afa6714528e10609a30f/dotnet-sdk-3.1.403-linux-x64.tar.gz
```

2. Setelah selesai download, langkah selanjutnya adalah membuat folder untuk lokasi SDK di ubuntu.
```
$ sudo mkdir /opt/.netcore/ 
```

kemudian extrak
```
$ sudo tar xvf dotnetcore-3.1.tar.gz -C /opt/.netcore
```

### Menjalankan .NET Core

