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

### Keuntungan Reverse Proxy :
> 1. Menyembunyikan IP asli server backend.
> 2. Load balancing (bisa arahkan ke beberapa server).
> 3. SSL termination (SSL hanya dikelola oleh reverse proxy).
> 4. Caching dan kompresi konten.
> 5. Keamanan (bisa menambahkan firewall, rate limit, dll).

# Implementasi Reverse Proxy untuk wayshub (januar.xyz)
> Langkah-langkah (menggunakan NGINX) :
### Install NGINX
```
  sudo apt update
```
![3](https://github.com/user-attachments/assets/2da9e4d3-0775-4ef3-a0c8-fc49b7952d02)
