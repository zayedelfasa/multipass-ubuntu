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

Untuk mencoba `hello-world` pada podman, cukup menuliskan perintah seperti di bawah ini :
```
$ podman run hello-world
```
Kemudian ditunggu sampai selesai.
```
Resolved "hello-world" as an alias (/etc/containers/registries.conf.d/000-shortnames.conf)
Trying to pull docker.io/library/hello-world:latest...
Getting image source signatures
Copying blob 0e03bdcc26d7 done
Copying config bf756fb1ae done
Writing manifest to image destination
Storing signatures
```

Setelah selesai maka akan menampilkan output seperti ini: 
```
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

Untuk mencoba container yang lain dapat menggunakan container docker yang sudah ada. Misalkan kita membutuhkan container mariadb, kita download container mariadb dari docker.

Podman mungkin akan memberikan pilihan untuk melakukan download dari 2 repo yaitu dari docker.io atau dari quay.io. Pilih mariadb yang asal repo-nya dari docker.io.
Contohnya seperti di bawah ini : 
```
$ docker pull mariadb:latest
```
Kemudian akan menampilkan output seperti di bawah ini : 

```
? Please select an image:
  ▸ docker.io/library/127.0.0.0.1:3306
    quay.io/127.0.0.0.1:3306
```

