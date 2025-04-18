# Diagram Jaringan Komputer


![Diagram Jaringan drawio (1)](https://github.com/user-attachments/assets/f3ed0a0f-40cb-4bf9-8e29-0d1181b08a89)

## 🌐 Informasi Jaringan
- **IP Kelas C**: `192.168.11.xxx`
- **Blok CIDR**:
  - Subnet 1: `192.168.11.0/30`
  - Subnet 2: `192.168.11.4/30`
- **Subnet Mask**: `255.255.255.252`
- **Jumlah Perangkat**: 4 unit (PC A, PC B, PC C, PC D)
- **DNS**: Cloudflare `1.1.1.1` dan Google `8.8.8.8`

## Diagram
1. Diagram ini menggunakan IP Kelas C dengan subnetting menggunakan CIDR /30, dan terdiri dari 4 perangkat yang dibagi menjadi 2 subnet kecil.
2. Koneksi Internet Router terhubung ke internet
3. Router Sebagai pusat jaringan dan penghubung antar subnet
4. Total perangkat 4 komputer (A, B, C, D)
5. **Subnet 1**
   ```
   PC A        192.168.11.1
   PC B        192.168.11.2
   Network ID  192.168.11.0
   Broadcast   192.168.11.3
   Subnet Mask 255.255.255.252
   ````
6. **Subnet 2**
    ```
   PC C        192.168.11.5
   PC D        192.168.11.6
   Network ID  192.168.11.4
   Broadcast   192.168.11.7
   Subnet Mask 255.255.255.252
   ````
## Alur Koneksi
1. Internet mengarah ke router pusat.
2. Router membagi jaringan menjadi dua subnet kecil.
3. Subnet 1 menghubungkan Komputer A dan B.
4. Subnet 2 menghubungkan Komputer C dan D.
5. Masing-masing subnet memiliki alamat network, broadcast, dan host IP sesuai pembagian CIDR /30.

# Perbedaan SH (Shell) dan BASH (Bourne-Again Shell)


| Aspek             | SH (Shell)                                                                 |BASH (Bourne-Again Shell)                                                                                            |
|-------------------|------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|
| **Definisi**       | Shell adalah antarmuka command-line yang digunakan untuk berinteraksi dengan sistem operasi. | Bash (Bourne Again Shell) adalah shell yang dikembangkan sebagai penerus Bourne Shell (sh) dengan fitur tambahan. |
| **Jenis**          | Umum dan mencakup berbagai jenis seperti sh, csh, ksh, zsh.            | Salah satu jenis shell yang spesifik dan paling umum digunakan di Linux dan macOS.              |
| **Fitur Dasar**    | Umumnya hanya mendukung perintah dasar dan skrip sederhana.           | Mendukung fitur lanjutan seperti command history, auto-completion, dan scripting kompleks.     |
| **Scripting**      | Bisa digunakan untuk scripting dasar.                                 | Mendukung scripting lanjutan: fungsi, array, ekspansi parameter, dan kontrol alur.              |
| **Interaktivitas** | Kurang interaktif, minim fitur tambahan.                              | Lebih interaktif dengan dukungan autocomplete, prompt kustom, dan fitur navigasi riwayat.       |
| **File Konfigurasi**| Menggunakan file konfigurasi berbeda-beda tergantung jenis shell.     | Menggunakan `.bashrc`, `.bash_profile`, atau `.profile` untuk konfigurasi.                      |
| **Kecepatan**      | Umumnya lebih ringan karena minim fitur.                              | Sedikit lebih lambat karena fitur yang lebih banyak.                                            |
| **Ketersediaan**   | Tersedia di hampir semua sistem Unix/Linux.                           | Umumnya sudah menjadi default di banyak distribusi Linux dan tersedia di macOS.                |
| **Contoh Perintah**| `sh`, `csh`, `ksh`, `zsh`.                                             | `bash`, atau langsung digunakan jika menjadi default shell.                                     |
| **Lisensi**        | Bervariasi tergantung jenis shell.                                    | GNU GPL (open source).                                                                          |
| **Pengembang**     | Dikembangkan oleh berbagai pihak, tergantung jenis shell.             | Brian Fox (GNU Project), saat ini dikembangkan oleh komunitas GNU.                              |


# Dokumentasi Dasar Command Linux (dengan Contoh Outputnya)

### 🔹 Navigasi Direktori

| Perintah       | Fungsi                          | Contoh Output                       |
|----------------|----------------------------------|-------------------------------------|
| `pwd`          | Menampilkan direktori aktif     | `/home/user`                        |
| `ls`           | Menampilkan isi direktori       | `file1.txt  folder1  script.sh`     |
| `cd ..`        | Kembali ke direktori induk      | (tidak ada output, hanya berpindah) |
| `cd ~`         | Masuk ke direktori home         | (tidak ada output)                  |

---

### 🔹 Manajemen File & Folder

| Perintah             | Fungsi                            | Contoh Output                       |
|----------------------|------------------------------------|-------------------------------------|
| `touch test.txt`     | Membuat file kosong                | (tidak ada output)                  |
| `mkdir data`         | Membuat folder baru                | (tidak ada output)                  |
| `cp a.txt data/`     | Menyalin file ke folder            | (tidak ada output)                  |
| `mv test.txt old/`   | Memindahkan file                   | (tidak ada output)                  |
| `rm file.txt`        | Menghapus file                     | (tidak ada output)                  |
| `rm -r folder/`      | Menghapus folder dan isinya        | (tidak ada output)                  |

---

### 🔹 Informasi Sistem

| Perintah      | Fungsi                                | Contoh Output (Singkat)                                       |
|---------------|----------------------------------------|---------------------------------------------------------------|
| `uname -a`    | Info kernel dan arsitektur OS         | `Linux ubuntu 5.15.0-84-generic x86_64 GNU/Linux`             |
| `top`         | Monitoring proses                      | Daftar proses secara real-time (berjalan di terminal)         |
| `df -h`       | Penggunaan disk                        | `/dev/sda1   50G  25G  25G  50% /`                            |
| `free -h`     | Penggunaan RAM                         | `Mem: 7.6Gi total, 1.5Gi used, 5.5Gi free`                    |

---

### 🔹 Pengguna & Hak Akses

| Perintah                   | Fungsi                          | Contoh Output                        |
|----------------------------|----------------------------------|--------------------------------------|
| `whoami`                   | Menampilkan user aktif          | `user`                               |
| `chmod +x script.sh`       | Memberi hak eksekusi            | (tidak ada output)                   |
| `ls -l`                    | Menampilkan file + permission   | `-rw-r--r-- 1 user user 1234 Apr 18 file.txt` |

---

### 🔹 Jaringan

| Perintah             | Fungsi                               | Contoh Output                                 |
|----------------------|---------------------------------------|-----------------------------------------------|
| `ping google.com`    | Cek koneksi internet                 | `64 bytes from google.com: icmp_seq=1 ttl=56` |
| `ip a`               | Info alamat IP dan interface        | `inet 192.168.1.10/24`                        |
| `curl example.com`   | Ambil data dari URL                 | `<html> ... </html>`                         |

---

### 🔹 Manajemen Paket

| Perintah                      | Fungsi                          | Contoh Output                              |
|-------------------------------|----------------------------------|--------------------------------------------|
| `sudo apt update`             | Update list paket                | `Hit:1 http://archive.ubuntu.com ...`       |
| `sudo apt install git`        | Install paket                    | `Setting up git (1:2.34.1) ...`             |
| `sudo apt remove nano`        | Hapus paket                      | `Removing nano (5.4-2ubuntu2) ...`          |

---

### 🔹 Perintah Lain yang Berguna

| Perintah              | Fungsi                             | Contoh Output                      |
|-----------------------|-------------------------------------|------------------------------------|
| `history`             | Melihat riwayat command             | `1  ls` `2  cd folder/`            |
| `clear`               | Bersihkan terminal                  | (terminal menjadi bersih)          |
| `alias ll='ls -la'`   | Alias perintah                      | (tidak ada output, langsung aktif) |
"""
