# Mencoba Podman pada Multipass Ubuntu

1. Jika pada OS Anda belum menjalankan multipass, Anda dapat download di [sini](https://multipass.run/).

2. Jika belum ada server ubuntu pada multipass, Anda dapat mengikuti tutorial ini mengetahui apa itu multipass lebih lanjut:
https://github.com/zayedelfasa/multipass-ubuntu

## Instalasi Podman

Kali ini saya akan mencoba menggunakan Podman di Multipass Ubuntu. 

Asumsinya, mencoba Podman kali ini kita sudah memiliki persiapan image ubuntu. Kali ini nama yang saya gunakan untuk mencoba Podman adalah `podmans`.
```
Name                    State             IPv4             Image
podmans                 Running           192.168.64.14    Ubuntu 20.04 LTS

###########################################################################################
New Multipass 1.5.0 release
Configurable storage and Groovy Gorilla support

Go here for more information: https://github.com/CanonicalLtd/multipass/releases/tag/v1.5.0
###########################################################################################
```

Berdasarkan `podman.io`, Podman adalah `container` yang dapat melakukan pengolahan (manage), menjalankan OCI Container (Open Container Initiative) pada sistem Linux. Kali ini, `Podman` akan coba dijalankan pada Multipass Ubuntu yang merupakan salah satu varian dari Linux tentunya.

1. Pertama kali tentunya kita masuk ke dalam shell Multipass. Kali ini saya menggunakan Multipass Ubuntu yang bernama `podmans`.
   ```
   $ multipass shell podmans
   ```
2. Untuk install pada Ubuntu, diperlukan tambahan repositori agar dapat install podman.
   ```
   $ . /etc/os-release

   $ echo "deb https://download.opensuse.org/repositories/devel:/kubic:/libcontainers:/stable/xUbuntu_${VERSION_ID}/ /" | sudo tee /etc/apt/sources.list.d/devel:kubic:libcontainers:stable.list
   ```
   Pastikan perintah berjalan dengan benar dengan menghasilakn output seperti ini: 
   ```
   el:kubic:libcontainers:stable.list
   deb https://download.opensuse.org/repositories/devel:/kubic:/libcontainers:/stable/xUbuntu_20.04/ /
   ```
   Setelah itu lanjutkan perintah di bawah ini:
   ```
   $ curl -L https://download.opensuse.org/repositories/devel:/kubic:/libcontainers:/stable/xUbuntu_${VERSION_ID}/Release.key | sudo apt-key add -
   ```

3. Setelah itu lakukan update.
   ```
   $ sudo apt update
   ```
   Setelah update, jalankan perintah install podman.
   ```
   $ sudo apt install podman
   ```
Podman sendiri memiliki kemiripan dengan kontainer seperti Docker. 

## Mencoba Menjalankan Podman
Jika sudah selesai install, untuk melihat perintah podman dapat menjalankan perintah di bawah ini: 
```
$ podman --help
```

Kali ini, kita akan mencoba membuat satu kontainer `hello world` dengan menggunakank `podman` ini.

[UNDER CONSTRUCTION]!!!