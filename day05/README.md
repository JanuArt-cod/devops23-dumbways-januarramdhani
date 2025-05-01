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
#### A. Akses ke Server via SSH
> Sebelum kamu bisa melakukan deployment aplikasi, kamu harus terlebih dahulu masuk ke dalam server menggunakan protokol SSH (Secure Shell). Pastikan kamu memiliki :
> ssh username@IP_SERVER

**Contoh :**

```bash
    ssh januar@192.168.1.28
```
> Jika berhasil, kamu akan masuk ke terminal server tempat kamu akan men-deploy aplikasi.

#### B. Memperbarui daftar paket sistem
> Setelah kamu masuk ke server, jalankan perintah ini untuk memperbarui daftar paket sistem kamu :
```
  sudo apt update
```
![1](https://github.com/user-attachments/assets/138e43c6-965a-4081-9b3b-6831d0080f27)

**Penjelasan :**
> - sudo: Menjalankan perintah dengan hak akses superuser (root).
> - apt: Merupakan package manager untuk distribusi berbasis Debian (seperti Ubuntu).
> - update: Perintah yang digunakan untuk memperbarui informasi paket dari repository.

#### C. Pastikan Firewall Aktif (UFW)
> UFW (Uncomplicated Firewall) adalah firewall bawaan Ubuntu yang membantu mengontrol akses masuk dan keluar dari server.

**Aktifkan firewall :**
```
  sudo ufw enable
```
> Setelah diaktifkan, semua koneksi luar akan diblokir secara default, kecuali port yang secara eksplisit dibuka menggunakan perintah `sudo ufw allow`.
![17](https://github.com/user-attachments/assets/bc4a2ba4-60a0-479c-92e0-cda204f6f82c)

## 2. Deploy Aplikasi wayshub-frontend (Node.js di Port 3000)
> Aplikasi Wayshub Frontend adalah aplikasi berbasis React yang dijalankan menggunakan `Node.js`. Aplikasi ini berfungsi sebagai frontend yang berjalan di `port 3000` secara default. Berikut adalah langkah-langkah untuk mendownload, menginstal, dan menjalankan aplikasi ini di server.

### A. Tahap Persiapan Server
> Jika kamu memerlukan versi tertentu dari `Node.js`, seperti `versi 13`, kamu bisa menggunakan NVM agar versi yang digunakan lebih fleksibel. Berikut adalah langkah-langkah yang lebih rinci untuk menginstal `Node.js` `versi 13` menggunakan NVM:

#### 1. **Install Git, Node.js, dan NPM :**
```
    sudo apt install -y git nodejs npm
```
> sudo apt install -y git nodejs npm: Menginstal Git (untuk clone repositori), Node.js (runtime untuk aplikasi JavaScript), dan NPM (pengelola paket Node.js).

![2](https://github.com/user-attachments/assets/c3c3955f-c207-4978-b2a0-711b4c021730)
> **Catatan Penting :**
> Aplikasi `wayshub-frontend` membutuhkan Node.js versi 13. Namun, versi dari repositori bawaan Ubuntu biasanya tidak menyediakan versi tersebut. Oleh karena itu, kita menggunakan **NVM (Node Version Manager)** untuk menginstal dan mengelola Node.js versi tertentu.

#### 2. **Install NVM (Node Version Manager)**
```
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```
![4](https://github.com/user-attachments/assets/662277f4-8810-4623-b32d-8c526eca92e5)

> Kemudian aktifkan NVM :
```
    source ~/.bashrc
```
> **Penjelasan :**
> - Perintah pertama mengunduh dan menjalankan installer NVM.
> - source ~/.bashrc digunakan untuk memuat ulang konfigurasi shell agar perintah nvm dikenali.

#### 3. Install Node.js Versi 13 Menggunakan NVM
```
    nvm install 13
    nvm use 13
```
> **Penjelasan :**
> - nvm install 13: Mengunduh dan menginstal Node.js versi 13.
> - nvm use 13: Mengaktifkan penggunaan Node.js versi 13 di terminal saat ini.

![5](https://github.com/user-attachments/assets/f6ba61dc-348a-4b12-a417-1434ba670f73)
![6](https://github.com/user-attachments/assets/28a1f59a-b064-49fa-b0fe-ccf30baaa1df)

---

### B. Tahap Deploy Aplikasi
#### 1. **Clone Repository Aplikasi**
```
    git clone https://github.com/dumbwaysdev/wayshub-frontend
    cd wayshub-frontend
```
> **Penjelasan :**
> - git clone: Mengambil (clone) seluruh isi repository ke server lokal.
> - cd wayshub-frontend: Masuk ke direktori project.
![7](https://github.com/user-attachments/assets/8ae9416d-4514-4e03-a04e-097c6d8a65c9)

#### 2. Install Dependensi Node.js
```
    npm install
```
> **Penjelasan :**
> Perintah ini membaca file package.json dan menginstal semua library (dependensi) yang dibutuhkan aplikasi.
![8](https://github.com/user-attachments/assets/9ba732a3-cb13-4471-8355-61a15da57369)

#### 3. Jalankan Aplikasi
```
    npm start
```
> **Penjelasan :**
> Menjalankan aplikasi. Secara default, aplikasi akan berjalan di port 3000.

![10](https://github.com/user-attachments/assets/cb900db6-ec0b-4d37-a94f-6b1b1015ed75)
