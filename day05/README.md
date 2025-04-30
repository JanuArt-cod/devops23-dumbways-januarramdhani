# Application in Server
---

# Dokumentasi cara deploy 3 aplikasi berbeda di server Linux menggunakan SSH dengan firewall (`ufw`) yang aktif.



> 📦 Aplikasi yang Dideploy

| Teknologi | Port | Keterangan |
|----------|------|------------|
| NodeJS   | 3000 | Frontend Wayshub |
| Python (Flask) | 5000 | Menampilkan teks nama pribadi |
| Golang   | 8080 | Menampilkan teks "Golang geming!" |

---
## 1. Persiapan Awal
### A. Akses ke Server via SSH
> Sebelum kamu bisa melakukan deployment aplikasi, kamu harus terlebih dahulu masuk ke dalam server menggunakan protokol SSH (Secure Shell). Pastikan kamu memiliki :
> ssh username@IP_SERVER

**Contoh :**

```bash
    ssh januar@192.168.1.28
```
> Jika berhasil, kamu akan masuk ke terminal server tempat kamu akan men-deploy aplikasi.

### B. Memperbarui daftar paket sistem
> Setelah kamu masuk ke server, jalankan perintah ini untuk memperbarui daftar paket sistem kamu :
```
  sudo apt update
```
![1](https://github.com/user-attachments/assets/138e43c6-965a-4081-9b3b-6831d0080f27)

**Penjelasan :**
> - sudo: Menjalankan perintah dengan hak akses superuser (root).
> - apt: Merupakan package manager untuk distribusi berbasis Debian (seperti Ubuntu).
> - update: Perintah yang digunakan untuk memperbarui informasi paket dari repository.

### C. Pastikan Firewall Aktif (UFW)
> UFW (Uncomplicated Firewall) adalah firewall bawaan Ubuntu yang membantu mengontrol akses masuk dan keluar dari server.

**Aktifkan firewall :**
```
  sudo ufw enable
```
> Setelah diaktifkan, semua koneksi luar akan diblokir secara default, kecuali port yang secara eksplisit dibuka menggunakan perintah `sudo ufw allow`.
![17](https://github.com/user-attachments/assets/bc4a2ba4-60a0-479c-92e0-cda204f6f82c)

## 2. Deploy Aplikasi NodeJS (Wayshub Frontend)
> Aplikasi Wayshub Frontend adalah aplikasi berbasis React yang dijalankan menggunakan `Node.js`. Aplikasi ini berfungsi sebagai frontend yang berjalan di `port 3000` secara default. Berikut adalah langkah-langkah untuk mendownload, menginstal, dan menjalankan aplikasi ini di server.

### A. Persiapan Node.js dengan NVM
> Jika kamu memerlukan versi tertentu dari `Node.js`, seperti `versi 13`, kamu bisa menggunakan NVM agar versi yang digunakan lebih fleksibel. Berikut adalah langkah-langkah yang lebih rinci untuk menginstal `Node.js` `versi 13` menggunakan NVM:

> - Instal Node.js dan npm dengan perintah berikut :
```
  sudo apt install -y git nodejs npm
```
![2](https://github.com/user-attachments/assets/c3c3955f-c207-4978-b2a0-711b4c021730)
![3](https://github.com/user-attachments/assets/ce29ebc3-d26e-4af8-bfc9-331c95f05e5a)


