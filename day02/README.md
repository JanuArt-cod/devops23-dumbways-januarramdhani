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

## Perbedaan Shell dan Bash

### Tabel Komparasi Shell vs Bash

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

