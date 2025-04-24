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

## 4. Perintah `echo`
**A. Menampilkan teks ke terminal**
```bash
  echo "Alhamdulillah"
```
> Perintah ini digunakan untuk mencetak teks ke layar terminal. Dalam contoh ini, terminal akan menampilkan kata Alhamdulillah. Cocok dipakai untuk debugging, memberi output cepat, atau sekadar menguji sintaks.

![16](https://github.com/user-attachments/assets/62e7af78-d589-4b4d-8300-5114bc7a9472)

**B. Menambahkan teks ke akhir baris file**
```bash
  echo "Luar Biasa" >> file1
```
> Berbeda dari sebelumnya, perintah ini tidak menimpa, tapi menambahkan teks Luar Biasa di akhir file1. Ini aman digunakan kalau kamu ingin menambahkan log atau catatan tambahan tanpa menghapus isi yang sudah ada.

![17](https://github.com/user-attachments/assets/e5da28e7-a561-4426-a219-4c26d3e08e47)

**C. Membuat file baru langsung dengan isi**
```bash
  echo "DevOps" > file4
```

![18](https://github.com/user-attachments/assets/6c8f7b4f-b923-4868-8e7d-c034df3507c8)

> Dengan perintah ini, file baru bernama file4 akan dibuat (jika belum ada) dan langsung diisi dengan teks DevOps. Praktis untuk membuat file konfigurasi, catatan, atau pengujian cepat.

## 5. Perintah `grep`
**A. Mencari teks tertentu dalam file**
```bash
  grep Guys file1
```
> grep digunakan untuk mencari baris yang mengandung kata Guys dalam file1. Ini sangat berguna saat kamu ingin mencari baris yang relevan tanpa membaca semua isi file secara manual.

**B. Case-insensitive search**
```bash
  grep -i "hello" berkastujuh.txt
```
![26](https://github.com/user-attachments/assets/ff18f6b4-5ed4-4e6b-a772-b53cc6ffc955)

> Opsi -i membuat pencarian menjadi tidak sensitif terhadap huruf besar/kecil. Jadi alhamdulillah dan AAlhamDulillAh, akan tetap dianggap cocok.
Cocok untuk mencari data dari input pengguna atau log yang tidak konsisten penulisannya.

**C. Menghitung jumlah baris yang cocok**
```bash
  grep -c Alhamdulillah file1
  grep -c Guys file2
  grep -c Guys file3
```
![21](https://github.com/user-attachments/assets/3575714c-7ea5-4a1b-9246-ad65e470c372)

> Opsi -c akan menghitung berapa kali pola atau kata yang dicari muncul dalam file. Hasilnya adalah angka, bukan isi baris.

**D. Mencari di banyak file sekaligus**
```bash
  grep -c Guys *
```
![22](https://github.com/user-attachments/assets/f79d2c60-ec4c-4936-b48e-50204b7cd7f1)

> Di sini, kita mencari kata Guys di semua file yang ada di direktori saat ini. Hasilnya akan menunjukkan jumlah kecocokan dari masing-masing file.

**E. Menampilkan baris yang cocok dengan nomor baris**
```bash
  grep -n Guys file2
```
![23](https://github.com/user-attachments/assets/75a57650-2c48-41cd-b833-957a41e75417)

> Dengan opsi -n, grep akan menampilkan baris-baris yang mengandung kata Guys
