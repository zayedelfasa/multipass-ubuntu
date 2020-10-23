# Menjalankan .NET core dan deploy API di Ubuntu Server Multipass

Kali ini saya akan menjalankan .NET core dan mencoba compile API pada multipass ubuntu.

1. Jika pada OS Anda belum menjalankan multipass, Anda dapat download di [sini](https://multipass.run/).

2. Jika belum ada server ubuntu pada multipass, Anda dapat mengikuti tutorial ini mengetahui apa itu multipass lebih lanjut:
https://github.com/zayedelfasa/multipass-ubuntu

Jika dua persyaratan di atas telah dipenuhi, kita akan melanjutkan step yang berikutnya yaitu menjalankan SDK .NET core pada ubuntu multipass.
Pada tutorial kali ini, saya akan menggunakan .NET core versi 2.1.

Sebelum melakukan instalasi .NET Core kita perlu register `Microsoft key` menjadi sebuah repository di dalam ubuntu kita, kemudian install dependecies lain yang dibutuhkan. Perintahnya sebagai berikut : 

```
$ wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg

$ sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/

$ wget -q https://packages.microsoft.com/config/ubuntu/18.04/prod.list 

$ sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list

$ sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg

$ sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```
### Install .NET Core 2.1

Setelah melakukan register, langkah selanjutnya adalah instalasi .NET Coew 2.1. Langkahnya sebegai berikut:

```
$ sudo apt-get install apt-transport-https
```

Kemudian update
```
$ sudo apt-get update
```

Setelah itu install .NET Core 2.1
```
$ sudo apt-get install aspnetcore-runtime-2.1
$ sudo apt-get install dotnet-sdk-2.1
```

### Menjalankan .NET Core

.NET Core dapat dijalankan dengan perintah `dotnet` dengan syarat binary-nya sudah dikenali oleh environment shell dari ubuntu. 
Apabila kita sudah melakukan instalasi seperti langkah di atas, maka perintah `dotnet` dapat langsung dikenali.

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

Untuk lebih jelas dari .NET Core yang telah terinstall pada Ubuntu Anda, dapat menggunakan perintah di bawah ini: 
```
$ dotnet --info
```
```
.NET Core SDK (reflecting any global.json):
 Version:   2.1.811
 Commit:    a9da00fd20

Runtime Environment:
 OS Name:     ubuntu
 OS Version:  20.04
 OS Platform: Linux
 RID:         ubuntu.20.04-x64
 Base Path:   /usr/share/dotnet/sdk/2.1.811/

Host (useful for support):
  Version: 2.1.23
  Commit:  b61e1596d6

.NET Core SDKs installed:
  2.1.811 [/usr/share/dotnet/sdk]

.NET Core runtimes installed:
  Microsoft.AspNetCore.All 2.1.23 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
  Microsoft.AspNetCore.App 2.1.23 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
  Microsoft.NETCore.App 2.1.23 [/usr/share/dotnet/shared/Microsoft.NETCore.App]

To install additional .NET Core runtimes or SDKs:
  https://aka.ms/dotnet-download
```

### Menjalankan contoh API yang dibuat menggunakan .NET Core.
Untuk menjalankan contoh API yang telah dibuat pada PC client, kita perlu transfer project API kita ke dalam Ubuntu Multipass. 
Untuk menjalankan perintah transfer project, dapat menggunakan perintah `multipass transfer`. Contohnya seperti berikut: 

Misalkan kita memiliki folder project .NET Core bernama `testwebapi`, maka kita perlu jadikan zip terlebih dahulu karena perintah `multipass transfer` hanya bisa transfer dalam bentuk file.

```
$ multipass transfer testwebapi.zip dotnetbuntu:/home/ubuntu/testwebapi.zip
```

Setelah itu Anda perlu cek project dalam bentuk zip tersebut di dalam ubuntu Anda yang ada di dalam folder `/home/ubuntu/`. 

Setelah itu ekstrak dengan menggunakan perintah `zip`. Jika `zip`  belum Ada, perlu diinstall terlebih dahulu dengan menggunakan perintah berikut: 

```
$ sudo apt install zip
$ sudo apt install unzip
```

Setelah diinstall, langkah selanjutnya adalah ekstrak. 
```
$ mkdir testwebapi

$ cd testwebapi/ && unzip ../testwebapi.zip
```
Sebelum menjalankan API tersebut, kita perlu mengganti ip `localhost` pada project menjadi ip public dari multipass dengan tujuan agar IP dapat diakses oleh PC client.
Cara untuk mengganti ip-nya, kita perlu mengubah konfigurasi dari `launchSettings.json` yang letaknya ada di dalam folder `Properties`.

```
$ cd Properties/
$ vim launchSettings.json
```

Maka akan muncul isi dari file `launchSettings.json`
```
{
  "$schema": "http://json.schemastore.org/launchsettings.json",
  "iisSettings": {
    "windowsAuthentication": false, 
    "anonymousAuthentication": true, 
    "iisExpress": {
      "applicationUrl": "http://localhost:34678",
      "sslPort": 44337
    }
  },
  "profiles": {
    "IIS Express": {
      "commandName": "IISExpress",
      "launchBrowser": true,
      "launchUrl": "api/values",
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development"
      }
    },
    "testwebapi": {
      "commandName": "Project",
      "launchBrowser": true,
      "launchUrl": "api/values",
      "applicationUrl": "https://localhost:5001;http://localhost:5000",
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development"
      }
    }
  }
}
```

Lakukan perubahan pada tulisan `localhost` di bagian key `applicationUrl` menjadi ip ubuntu multipass Anda.
```
{
  "$schema": "http://json.schemastore.org/launchsettings.json",
  "iisSettings": {
    "windowsAuthentication": false, 
    "anonymousAuthentication": true, 
    "iisExpress": {
      "applicationUrl": "http://localhost:34678",
      "sslPort": 44337
    }
  },
  "profiles": {
    "IIS Express": {
      "commandName": "IISExpress",
      "launchBrowser": true,
      "launchUrl": "api/values",
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development"
      }
    },
    "testwebapi": {
      "commandName": "Project",
      "launchBrowser": true,
      "launchUrl": "api/values",
      "applicationUrl": "https://192.168.64.7:5001;http://192.168.64.7:5000",
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development"
      }
    }
  }
}
```

Setelah itu keluar dari editor `vim`.

Setelah diekstrak, kita bisa jalankan project tersebut dengan menggunakan printah `run` pada dotnet.
```
$ dotnet build && dotnet run
```

Setelah itu, Anda bisa mencoba akses API tersebut di PC client Anda sesuai dengan IP dari ubuntu multipass (dotnetbuntu).

Sekian. 

Zayed Elfasa.