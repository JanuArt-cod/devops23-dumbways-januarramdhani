# Struktur Web Server dengan Reverse Proxy

![Screenshot 2025-05-05 123423](https://github.com/user-attachments/assets/534f0acc-4a45-4046-b84e-75e5ae0df496)

# 🔁 Apa Itu Reverse Proxy?
> Reverse Proxy adalah sebuah server yang berdiri di antara klien (browser) dan server utama (aplikasi). Ia menerima permintaan dari klien, lalu meneruskannya ke server belakang (backend) dan mengembalikan hasilnya ke klien.

# Cara Kerja Reverse Proxy
> - User mengakses domain seperti alvin.xyz dari browser.
> - Permintaan masuk ke reverse proxy (misal: NGINX) terlebih dahulu.
> - Reverse proxy meneruskan request ke backend server (tempat aplikasi wayshub berjalan).
> - Aplikasi memproses permintaan, lalu mengirim respons kembali ke reverse proxy.
> - Reverse proxy meneruskan respon ke user.

# Keuntungan Reverse Proxy :
> 1. Menyembunyikan IP asli server backend.
> 2. Load balancing (bisa arahkan ke beberapa server).
> 3. SSL termination (SSL hanya dikelola oleh reverse proxy).
> 4. Caching dan kompresi konten.
> 5. Keamanan (bisa menambahkan firewall, rate limit, dll).

# Konfigurasi Domain pada File Hosts di Host OS (Windows)
> Untuk memastikan domain yang gunakan dapat dikenali oleh sistem lokal saat mengakses server Ubuntu melalui reverse proxy, lakukan konfigurasi pada file `hosts` di sistem operasi Windows. Berikut langkah-langkahnya:

### 1. Buka Windows Explorer dan arahkan ke direktori:
```
  C:\Windows\System32\drivers\etc
```
### 2. Temukan file bernama hosts. File ini tidak memiliki ekstensi.
![1](https://github.com/user-attachments/assets/ae235823-e9f9-4104-84cb-ff18da17b3d3)

### 3. Klik kanan pada file hosts, lalu pilih "Open with" atau "Open menggunakan" dan pilih aplikasi Notepad atau Notepad++ yang dijalankan sebagai Administrator.
> *Catatan: Anda harus membuka editor teks dengan hak administrator agar bisa menyimpan perubahan.*
### 4. Tambahkan baris berikut di bagian bawah file untuk mengaitkan domain lokal dengan alamat IP server Ubuntu :
```
  192.168.1.28   januar.xyz
```
> *Gantilah 192.168.1.28 dengan alamat IP server Ubuntu, dan januar.xyz dengan nama domain lokal yang ingin gunakan.*
---

# Akses Server Ubuntu melalui SSH dan Instalasi Nginx
> Setelah berhasil masuk ke server, jalankan perintah berikut untuk memperbarui daftar paket dan memperbarui sistem :
### Perbarui Repositori dan Paket Sistem Ubuntu
```
  sudo apt update
```
![3](https://github.com/user-attachments/assets/2da9e4d3-0775-4ef3-a0c8-fc49b7952d02)

### Instalasi Nginx (Jika Belum Terpasang)

```
  sudo apt install nginx -y
```
### Verifikasi Status Nginx
> Setelah instalasi selesai, pastikan Nginx sudah berjalan dengan baik.
```
  sudo systemctl status nginx
```
---
# Menguji Akses Reverse Proxy Melalui Browser di Host OS
> Setelah mengatur file hosts di Windows dan menginstal serta menjalankan Nginx di server Ubuntu, langkah selanjutnya adalah menguji apakah domain lokal seperti januar.xyz sudah bisa diakses melalui browser di Host OS (Windows).
### Ketik Alamat Domain Lokal yang telah di tambahkan
```
  http://januar.xyz
```
### Cek Tampilan yang Muncul
> - Jika berhasil, akan melihat halaman default Nginx yang menandakan server Nginx berjalan dengan baik.
> - Jika belum berhasil, pastikan
> - File hosts di Windows sudah disimpan dan berisi :
```
  192.168.1.28    januar.xyz
```
---
# Mengizinkan Akses Port 80 dan 443 di UFW
> Jika saat membuka http://januar.xyz di browser mengalami loading tanpa henti (unlimited loading), salah satu penyebab umumnya adalah port yang digunakan untuk HTTP (port 80) dan HTTPS (port 443) belum diizinkan oleh firewall (UFW) di server Ubuntu.

### Jalankan perintah berikut di server Ubuntu untuk memastikan UFW sedang aktif:
```
  sudo ufw status
```
> Jika hasilnya menunjukkan inactive, maka UFW tidak sedang membatasi akses. Jika aktif, lanjut ke langkah berikut.
### Izinkan Port 80 (HTTP) dan Port 443 (HTTPS)
> Gunakan perintah berikut untuk mengizinkan kedua port tersebut:
```
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
```
![18](https://github.com/user-attachments/assets/8c3fd1f5-c55e-4679-9f6a-3842863d729d)

---
# Konfigurasi Reverse Proxy Domain januar.xyz di Nginx
### Pindah ke Direktori Konfigurasi Nginx
> Masuk ke direktori tempat konfigurasi virtual host aktif berada:
```
cd /etc/nginx/sites-enabled
```
> Direktori ini berisi symlink dari file konfigurasi yang sebenarnya ada di `/etc/nginx/sites-available`.

![Screenshot 2025-05-06 021059](https://github.com/user-attachments/assets/cea0cd0e-24c2-4320-8fb9-31e5a2f0421c)

### Buat atau Edit Konfigurasi untuk januar.xyz
> Jika belum memiliki file konfigurasi, buat file baru di  `/etc/nginx/sites-available/` terlebih dahulu:
```
  sudo nano /etc/nginx/sites-available/januar.conf
```
**Kemudian isi dengan konfigurasi berikut:**
```
server {
    listen 80;
    server_name januar.xyz;

    location / {
        proxy_pass http://192.168.1.28:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```
> Konfigurasi di atas akan meneruskan semua permintaan ke `januar.xyz` ke server frontend Anda di `http://192.168.1.28:3000`.
> Jika sudah di aktifkan Konfigurasi dengan Membuat Symlink :
```
  sudo ln -s /etc/nginx/sites-available/januar.conf /etc/nginx/sites-enabled/
```
![5](https://github.com/user-attachments/assets/2233d07f-8e29-4733-9739-a08fbbf42f0f)

![6](https://github.com/user-attachments/assets/a68c0ec9-0f13-438c-af46-9acc2ed38c55)

---
# Konfigurasi Nginx
> Sebelum me-reload Nginx, pastikan tidak ada kesalahan sintaks:
```
  sudo nginx -t
```
![7](https://github.com/user-attachments/assets/e468bb55-bf71-469c-9e32-00af0ecbf768)

```
  sudo systemctl reload nginx
```

```
sudo systemctl status nginx
```
![4](https://github.com/user-attachments/assets/0d915979-7931-4d17-8551-59adc58f8d84)

# Menguji di browser seperti Chrome, Firefox, atau Edge.
> Setelah menyelesaikan konfigurasi Nginx dan mengarahkan domain januar.xyz ke aplikasi wayshub-frontend yang berjalan di http://192.168.1.28:3000, saatnya mengujinya di browser pada Host OS (misalnya Windows).

![8](https://github.com/user-attachments/assets/445121e6-3525-4851-985c-a51a7aa81e50)
