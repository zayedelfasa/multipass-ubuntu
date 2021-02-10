# Mencoba Podman pada Multipass Ubuntu

1. Jika pada OS Anda belum menjalankan multipass, Anda dapat download di [sini](https://multipass.run/).

2. Jika belum ada server ubuntu pada multipass, Anda dapat mengikuti tutorial ini mengetahui apa itu multipass lebih lanjut:
https://github.com/zayedelfasa/multipass-ubuntu

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

Berdasarkan `podman.io`, Podman adalah `container` yang dapat melakukan pengolahan (manage), menjalankan OCI Container (Open Container Initiative) pada sistem Linux. Kali ini, podman saya akan jalankan pada Multipass Ubuntu yang merupakan salah satu varian dari Linux tentunya.

