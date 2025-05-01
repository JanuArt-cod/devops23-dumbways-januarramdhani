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

---

# ✅ Deploy Aplikasi wayshub-frontend (Node.js di Port 3000)
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

---

# 🚀 Deploy Aplikasi Python Flask (Port 5000)
> Dokumentasi ini menjelaskan cara men-deploy aplikasi Python sederhana yang menampilkan teks “Nama saya Januar” di browser, berjalan di port 5000, dan dapat diakses dari luar server meskipun firewall UFW aktif.
### A. Persiapan Awal
```
    install Python + pip
```
> **Penjelasan :**
> `python3`, `pip3`: Python versi 3 dan package manager-nya.
![13](https://github.com/user-attachments/assets/70f8da36-ff34-416b-8bba-80165a07a6ab)

### B. Install Flask
> Kita akan menggunakan Flask, framework Python ringan untuk web.
```
    pip3 install flask
```
> Jika kamu ingin isolasi proyek agar lebih rapi, gunakan `python3 -m venv venv` dan `source venv/bin/activate`.
![14](https://github.com/user-attachments/assets/f73977cd-4b22-4e8b-81a8-e452960316f9)

### C. Membuat Aplikasi Python
> Buat file baru bernama `app.py`
```
    nano app.py
```
![11](https://github.com/user-attachments/assets/6e8e9215-26af-4648-9cd6-8fb8a05f55f2)

Masukkan kode berikut :
```
from flask import Flask

app = Flask(__name__)

@app.route("/")
def home():
    return "Nama saya Januar" 

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
```

![12](https://github.com/user-attachments/assets/c76a2947-3593-4a81-87d6-a02bab3688e5)

> **Penjelasan kode :**
> - `host="0.0.0.0"`: Agar bisa diakses dari IP luar (bukan hanya localhost).
> - `port=5000`: Jalankan server di port 5000.
> - `Route` / akan menampilkan teks sederhana.
> - Simpan dengan `CTRL+O`, lalu keluar dengan `CTRL+X`.

### D. Jalankan Aplikasi
```
    python3 app.py
```

Jika berhasil, akan muncul :
```
    * Running on all addresses (0.0.0.0)
    * Running on http://192.168.1.28:5000 (Press CTRL+C to quit)
    * Running on http://127.0.0.1:5000 (Press CTRL+C to quit)
```
![15](https://github.com/user-attachments/assets/ef9b181f-0042-496e-9e5b-52d6faa6e216)

### E. Buka Port 5000 di Firewall (UFW)
```
    sudo ufw allow 5000
    sudo ufw reload
    sudo ufw enable   -> Jika belum aktif
```

Cek status firewall:
```
    sudo ufw status
```
![18](https://github.com/user-attachments/assets/32843b39-83ed-404e-876a-2180dc09cd58)

### F. Akses Aplikasi di Browser
> Buka browser dan kunjungi:
```
    http://192.168.1.28:5000
atau
    http://127.0.0.1:5000
```
![16](https://github.com/user-attachments/assets/5315eba3-9930-45d1-8ba0-f546a2178848)

---

# ✅ Deploy Aplikasi Golang (Port 8080)
> Dokumentasi ini menjelaskan cara membuat dan menjalankan aplikasi Golang sederhana yang menampilkan teks "Golang geming!" di browser, berjalan di port 8080, dan dapat diakses dari luar meski UFW aktif.
### A. Install Golang
```
    sudo apt install golang -y
```
> Atau, untuk versi terbaru Golang, bisa ambil dari situs resmi: `https://go.dev/dl/` (opsional kalau butuh versi lebih tinggi dari repo Ubuntu).

![19](https://github.com/user-attachments/assets/a8e6d73c-65f9-461a-a9e8-789dbbd4ff82)

### B. Buat Aplikasi Golang
> 🔹 Buat file app.go :
```
    nano app.go
```
![20](https://github.com/user-attachments/assets/dd2d3660-cd2e-44b3-909f-02519c979f5d)

**ISI :**
```
package main

import (
    "fmt"
    "net/http"
)

func handler(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintf(w, "Golang geming!")
}

func main() {
    http.HandleFunc("/", handler)
    fmt.Println("Server running on port 8080...")
    http.ListenAndServe(":8080", nil)
}
```
> Simpan dengan `CTRL+O`, keluar dengan `CTRL+X`.



> 🔹 **Inisialisasi modul (Go Modules) :**
```
    go mod init golang-app
```
![22](https://github.com/user-attachments/assets/89f099a9-4d88-4bef-9af0-228f388b5761)

> 🔹 Build file binary :

```
    go build -o golang-app
```
![23](https://github.com/user-attachments/assets/618d13d9-147e-43c7-a147-6deafb4d95c5)

> Maka akan muncul file golang-app (executable).

### C. Build jadi file binary
```
    ./golang-app
```

**Output terminal :**
```
    Server running on port 8080...
```

### D. Buka Port di Firewall (UFW)
> Agar port 8080 dapat diakses dari luar server :

```
    sudo ufw allow 8080
    sudo ufw reload
```
**Cek status :**
```
    sudo ufw status
```

### E. Akses Aplikasi dari Browser
> Buka browser dan ketik :
```
    http://<IP-SERVER>:8080 -> http://192.168.1.28:8080
```
**Jika berhasil, akan muncul teks :**


![25](https://github.com/user-attachments/assets/70998a72-0bf2-4acc-b094-54d2dac51e3c)

