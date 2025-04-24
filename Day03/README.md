# Mengakses Server via Terminal Wndows
## 1. Instalasi dan Pengecekan SSH
> Pertama-tama kita perlu memastikan server Ubuntu bisa diakses dari luar melalui protokol SSH. Caranya adalah dengan menginstal OpenSSH. Tapi kalau sebelumnya kamu sudah pernah instal, bagian ini bisa kamu lewati.

**A. Instal OpenSSH dan Pengecekan SSH**
```bash
  sudo apt install openssh-server
```
![1](https://github.com/user-attachments/assets/9c9dc890-fc03-4191-ba83-caa23adab1e8)

> Setelah proses instalasi selesai, kita cek dulu apakah service SSH-nya sudah berjalan. Kalau statusnya “active (running)”, berarti server sudah siap diakses.

```bash
  sudo systemctl status ssh
```

![3](https://github.com/user-attachments/assets/f8161ede-9264-4408-bd4a-6cd331853ef0)

> Lalu kita perlu tahu alamat IP dari server yang akan kita akses. Ini berguna saat kita akan menghubungkannya dari perangkat lain ( Terminal Windows).

**B. Menentukan IP Address Server**
```bash
  ip a
```
![2](https://github.com/user-attachments/assets/bcfb9323-cc30-4ec9-84a6-639db1510164)

Gunakan IP yang muncul pada baris `inet enp0s3`.
> Setelah semua siap, sekarang buka terminal di komputer lain (Windows), lalu sambungkan ke server menggunakan perintah berikut.

**C. Koneksi ke server dari terminal (Windows)**
> Di komputer client (Windows), buka terminal. Bisa menggunakan CMD, PowerShell, atau Git Bash jika kamu menginstall Git. Pastikan komputer ini satu jaringan dengan servernya.
```bash
  ssh januar@192.168.1.28
```
![4](https://github.com/user-attachments/assets/8c4d157d-ff28-4c45-92f9-3d84fab47944)

> Kalau ini adalah koneksi pertama ke server, biasanya muncul notifikasi tentang keaslian host (fingerprint). Cukup ketik yes untuk melanjutkan.
Setelah itu, sistem akan meminta kamu memasukkan password user server. Ketik password-nya (meskipun tidak terlihat di layar) lalu tekan Enter.
Jika berhasil, sekarang kamu sudah berada di dalam terminal server dan bisa menjalankan perintah layaknya sedang duduk langsung di depan mesin tersebut.

## 2. Konfigurasi SSH Menggunakan Public Key (Tanpa Password)
> Supaya lebih aman, kita bisa mengatur agar server hanya bisa diakses menggunakan public key, dan tidak bisa login pakai password. Jadi siapa pun yang tidak punya private key tidak akan bisa masuk.

**A. Generate SSH Key dari Komputer Client**
> Di komputer client (Windows), jalankan perintah berikut untuk membuat pasangan public-private key. Kamu bisa beri nama file-nya sesuai keinginan, di sini contohnya pakai nama gembok.
```bash
  ssh-keygen
```
Langkah pertama untuk mengamankan akses server adalah membuat pasangan kunci SSH: public key dan private key.
Jalankan perintah ssh-keygen di terminal komputer client (Windows). Saat diminta nama file untuk menyimpan kunci, kamu bisa tekan Enter untuk menggunakan nama default, atau ketik nama khusus seperti gembok. Setelah proses selesai, dua file akan dibuat:
- kunci → ini adalah private key **(jangan dibagikan!)**
- kunci.pub → ini adalah public key yang akan ditempel ke server

![7](https://github.com/user-attachments/assets/771bf386-d38a-4d29-be1c-5b004cf7aab7)

**B. Copy public key**
> Buka file gembok.pub lalu salin semua isi teks di dalamnya. Ini adalah public key yang nanti akan ditempel di server.

![8](https://github.com/user-attachments/assets/37c5fcfb-6de0-40f7-8b8a-82e5dd50dc28)

> Kamu bisa buka file gembok.pub dengan Notepad atau text editor, lalu salin seluruh isi public key tersebut. Jangan ada karakter yang terpotong!

**C. Tempelkan Public Key ke Server**
> Setelah menyalin public key dari komputer client, sekarang kita masuk ke server melalui SSH (masih pakai password dulu), lalu masuk ke direktori .ssh.
```bash
  cd .ssh
  nano authorized_keys
```
![10](https://github.com/user-attachments/assets/2ded3381-9f0c-462c-a647-983d21689fe8)

> Tempel public key yang tadi disalin ke dalam file `authorized_keys`, lalu simpan.

![12](https://github.com/user-attachments/assets/7027ac90-b323-440b-a4d7-7fd721d22697)


**D. Coba akses server tanpa password**
> Sekarang, kita coba sambungkan kembali ke server—tapi kali ini menggunakan private key.Tambahkan opsi -i diikuti dengan path ke file private key (gembok) saat menjalankan ssh.
```bash
  ssh -i .ssh/gembok januar@192.168.1.28
```
![13](https://github.com/user-attachments/assets/cf8d3a90-a973-4d5e-96bc-deec636fdea3)

> Kalau semuanya benar, kamu akan langsung masuk ke server tanpa perlu memasukkan password. Ini artinya server hanya bisa diakses oleh perangkat yang punya private key yang cocok—meningkatkan keamanan secara signifikan.

## 3. Perintah `cat`

**A. Menampilkan isi file**
```bash
  cat file1
```
![14](https://github.com/user-attachments/assets/1b86bbd6-7dcb-40c9-bd46-140c538787d3)

> Perintah ini digunakan untuk menampilkan isi dari file yang bernama file1. Cocok dipakai kalau kamu ingin sekadar membaca atau mengecek isi dari sebuah file langsung di terminal, tanpa harus membuka editor seperti `nano` atau `vim`.

**B. Menulis ulang isi file**
```bash
  cat > file1
  Hello Guys
```
> Perintah ini berfungsi untuk menimpa isi file1 dengan teks baru. Setelah mengetik perintah, kamu bisa langsung menulis isinya (misalnya: Hello Guys), lalu tekan CTRL + D untuk menyimpan dan keluar. **Hati-hati, karena ini akan menghapus isi file sebelumnya!**

**C. Membuka isi file1 dan file2**
```bash
  cat file1 file2
```

**D. Menggabungkan isi dari beberapa file**
```bash
  cat file1 file2 > file3
  cat file3
```

> Dengan perintah ini, isi dari dua file ( file1 dan file2 akan digabungkan jadi satu, dan hasilnya disimpan di file baru bernama file3. Ini sangat berguna kalau kamu punya beberapa file teks terpisah dan ingin menjadikannya satu file gabungan.

![15](https://github.com/user-attachments/assets/3eb841bf-e13f-45e5-a6cf-9be4e389caac)
