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

# Implementasi Perintah Linux

1. Menuliskan perintah untuk update software linux
```bash
sudo apt update
```
![1](https://github.com/user-attachments/assets/4dc1c6af-87c3-4810-a1a5-3100222ed784)

2. Menuliskan perintah untuk membuat direktori dumbways dan perintah list (ls) untuk menampilkan folder yang sudah dibuat
```bash
mkdir dumbways
```
```bash
ls
```
![2](https://github.com/user-attachments/assets/a77801eb-9e18-4c1d-acbb-e2a9d411ed2a)

3. Menuliskan perintah untuk membuat file filesatu dan perintah list (ls) untuk menampilkan file yang sudah dibuat
```bash
touch filesatu
```
![3](https://github.com/user-attachments/assets/02bb9a00-9ac0-4eae-b475-7e5704e4651a)

4. Menuliskan perintah untuk menampilkan list dengan li dan la untuk menampilkan semua file termasuk yang hidden, dimana l adalah long format(detailed metadata) sedangkan a adalah all files
```bash
ls -la
```
![4](https://github.com/user-attachments/assets/036982b5-03ea-41ce-82c7-ba0d7bba2bac)

5. Menuliskan perintah untuk masuk ke direktori dumbways dan perintah untuk keluar dari direktori dumbways
```bash
cd dumbways
```
```bash
cd ..
```
![5](https://github.com/user-attachments/assets/8f8a5131-9fc5-473c-a4f9-b2728e5416fb)

6. Menuliskan perintah untuk copy file atau duplikat file, dimana filesatu adalah file yang akan di duplikat sedangkan sebelahnya adalah calon file duplikat dengan nama filedua
```bash
cp filesatu filedua
```
![6](https://github.com/user-attachments/assets/550a0117-3c94-4867-83b8-b3519bcc67b2)

7. Menuliskan perintah untuk move file atau memindahkan file, dimana filesatu dipindah ke dalam folder dumbways
```bash
mv filesatu dumbways/filesatu
```
![7](https://github.com/user-attachments/assets/88c178ad-aa44-4af4-8cbf-85ecaaf32634)

8. Menuliskan perintah untuk membuat text hello dumbways
```bash
echo 'hello dumbways'
```
![8](https://github.com/user-attachments/assets/683ffcfe-b092-4e5c-b1b0-b6b637655e5c)

9. Menuliskan perintah untuk membuat text hello dumbways di dalam file.js
```bash
echo 'hello dumbways' > file.js
```
![9](https://github.com/user-attachments/assets/98a4ed04-65ed-45d5-9e7d-5d2daf61063d)

10. Menuliskan perintah untuk menampilkan text atau konten di dalam file.js
```bash
cat file.js
```
![10](https://github.com/user-attachments/assets/88202ad8-dcd4-4e33-99f5-47bf1d763a1a)

11. Menuliskan perintah untuk menampilkan text 2x dengan menambah simbol >>
```bash
echo 'hello dumbways' >> file.js
```
![11](https://github.com/user-attachments/assets/4d3a39b4-6662-4714-98eb-2529c736e9b9)

12. Menuliskan perintah find untuk mencari file atau folder, dengan catatan ini umum maka akan menampilkan semua file dan folder
```bash
find
```
_perintah find dapat dibuat spesifik mencari folder atau file dengan prompt seperti ini_
```bash
find -type f
find -type d
find -type f -name filesatu
```
![12](https://github.com/user-attachments/assets/f913fdb0-8aa1-44ee-884a-514a4025cdb8)

13. Perintah grep untuk mencari text atau input didalam file tertentu
```bash
grep hello file.js
grep -r hello
```
![13](https://github.com/user-attachments/assets/912c5e72-8700-45f2-80d4-7508e066cab1)

14. Perintah untuk membuat text editor di dalam file.js
```bash
nano file.js
```
![14](https://github.com/user-attachments/assets/42a407f7-ff64-40cd-8b0c-86f300fd482f)

15.  Perintah untuk mengubah permission file atau direktori
```bash
chmod 777 file.js
chmod 773 file.js
```
![15](https://github.com/user-attachments/assets/46d5417a-edae-4f84-aa0a-b9a1b85d3429)

16. Perintah untuk mengubah kepemilikan file atau direktori
```bash
sudo chown root:root file.js
```
![16](https://github.com/user-attachments/assets/99193849-f92b-46a7-99b9-7495e34a24c8)

17. Perintah untuk menampilkan riwayat semua perintah linux yang pernah dijalankan
```bash
history
```
![17](https://github.com/user-attachments/assets/642b4c25-cf55-4e2d-9c4b-1b0b14464e42)

18. Perintah untuk memperbaiki masalah jaringan
```bash
sudo netplan apply
```
![18](https://github.com/user-attachments/assets/a7271875-a3ec-4d88-98e5-0715c5b2fa36)

19. Perintah untuk memperbaiki izin file konfigurasi Netplan
```bash
sudo chmod 600 /etc/netplan/01-netcfg.yaml
```

20. Perintah untuk mengecek apakah interface jaringan (seperti enp0s3) sudah dapat IP address.
```bash
ip a
```
![19](https://github.com/user-attachments/assets/03f5ddf7-e04d-4077-aa24-20a5f9edcccf)

21. Perintah untuk cek file konfigurasi netplan.
```bash
ls /etc/netplan/
```
![20](https://github.com/user-attachments/assets/bb4b7e48-0338-4251-a0cb-1a281f15d025)
