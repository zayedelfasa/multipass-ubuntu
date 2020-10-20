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

.NET Core dapat dijalankan dengan perintah `dotnet` dengan syarat binary-nya sudah dikenali oleh environment shell dari ubuntu. Cara untuk dikenalinya dapat menjalankan perintah sebagai berikut: 
```
$ export PATH=/opt/.netcore:$PATH
```

Setelah itu silahkan untuk coba menjalankan perintah `dotnet`.
```
$ dotnet
```

Jika berhasil maka akan keluar info seperti di bawah ini: 
```
Usage: dotnet [options]
Usage: dotnet [path-to-application]

Options:
  -h|--help         Display help.
  --info            Display .NET Core information.
  --list-sdks       Display the installed SDKs.
  --list-runtimes   Display the installed runtimes.

path-to-application:
  The path to an application .dll file to execute.
```

### Menjalankan contoh API yang dibuat menggunakan .NET Core.
