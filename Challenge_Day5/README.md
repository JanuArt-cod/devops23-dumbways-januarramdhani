# Menjalankan Multi-Server (Node.js, Python Flask, dan Golang) Secara Efisien
## Pendahuluan
> Dalam pengembangan aplikasi modern, sering kali kita perlu menjalankan beberapa server sekaligus. Panduan ini akan membahas:

> ✔ Menjalankan server Node.js di background menggunakan PM2.

> ✔ Menjalankan aplikasi Python Flask di background dengan PM2.

> ✔ Membuat server Golang yang dapat diakses via browser.

Dengan panduan ini, dapat mengelola ketiga server secara bersamaan tanpa mengganggu penggunaan terminal.

---
## Prasyarat
>- Node.js & npm ( app wayshub-frontend )
>- Python 3 ( app menampilkan text nama )
>- Golang ( Golang Geming )
>- PM2 (akan diinstal dalam panduan ini)

---
## Masuk ke Direktori Proyek
```
  cd wayshub-frontend
```
> cd ini untuk masuk ke direktori yang akan kita jalan kan sebagai contoh kali ini saya menggunakan app wayshub-frontend. dari repository `https://github.com/dumbwaysdev/wayshub-frontend`

## Menginstal semua dependensi Node.js
### Instalasi depensi Node.js
> Perintah `npm install` digunakan untuk menginstal semua dependensi yang diperlukan dalam proyek `Node.js`. Berikut penjelasan lengkapnya:
**Apa yang dilakukan npm install ?**
> - Membaca file `package.json` di direktori proyek
> - Mengunduh semua dependensi yang tercantum di dalamnya
> - Menyimpannya di folder `node_modules`

```
  npm install
```
![11](https://github.com/user-attachments/assets/70f70f8a-475b-4418-a1b3-3d51ba4f874a)

## Menggunakan PM2 untuk Manajemen Proses
### Instalasi PM2
> PM2 adalah process manager yang memungkinkan aplikasi berjalan di background secara stabil.
```
  npm install -g pm2
```
**📌 Catatan:**
- -g menginstal PM2 secara global.
- PM2 mendukung berbagai bahasa (Node.js, Python, dll).
- Contoh Implementasi dibawah ini :

![1](https://github.com/user-attachments/assets/1d91b355-be5d-4d5f-81b5-48b29c722a33)

#### ✅ Verifikasi Instalasi:
> Berguna untuk mengetahui versi berapa yang kita install karena kita menginstall secara global.
```
  pm2 --version
```
---
## Menjalankan Server Node.js di Background
### Jalankan dengan PM2
```
  pm2 serve build 3000 --name "wayshub-frontend" --spa
```
**🔍 Penjelasan:**
- `serve` - Menggantikan start npm karena kita ingin menjalankan server static files
- `build` - Direktori yang berisi file-file built (hasil dari npm run build)
- `3000` - Port yang digunakan untuk server
- `--name` "wayshub-frontend" - Nama proses di PM2
- `--spa` - Mode Single Page Application (untuk routing client-side)

![15](https://github.com/user-attachments/assets/6d9917b3-8e4a-4e4a-a00f-8ec3c0364ce3)

**Berikut ini adalah video hasil dari pm2**



https://github.com/user-attachments/assets/1d50a800-3a60-4742-a8f6-94bc680d2e08


---
## Menjalankan Server Python Flask di Background
### Jalankan dengan PM2
```
  pm2 start app.py --name "python-app" --interpreter python3
```
**🔍 Penjelasan Setiap Bagian:**
- `pm2` - Process Manager 2 (PM2) - alat untuk mengelola proses aplikasi di background
- `start` - Perintah untuk menjalankan aplikasi baru di bawah PM2
- `app.py` - File utama Python yang ingin dijalankan
- `--name "python-app"` - Memberikan nama/identifier untuk proses ini di PM2 → Berguna untuk manajemen proses (stop/restart/monitor)
- `--interpreter python3` - Menentukan interpreter yang digunakan (python3) → Wajib untuk aplikasi non-Node.js seperti Python

![16](https://github.com/user-attachments/assets/f49c005b-63d6-4ddc-a5d8-ce5da8c22fb4)

**Berikut ini adalah video hasil dari pm2**


https://github.com/user-attachments/assets/57c2c2f5-4442-4baf-a7c3-651b0e9a9b8c

## Membuat Server Golang yang Bisa Diakses via Browser
### Masuk ke Direktori Golang
```
  sudo nano app.go
```
> Perintah ini terdiri dari 3 bagian utama :
> 1. `sudo`
> - Singkatan dari "Super User DO"
> - Menjalankan perintah dengan hak akses administrator (root)
> - Diperlukan ketika : ( Membuat/mengedit file di folder sistem, Mengubah file yang dimiliki oleh user lain, Operasi yang membutuhkan privilege tinggi )
> 2. `nano`
> - Text editor berbasis terminal yang sederhana
> - Mudah digunakan (beginner-friendly)
> 3. `app.go`
> - Nama file yang akan dibuka/dibuat
> - Ekstensi `.go` menandakan file kode Golang
---
**Nano Editor Shortcuts**

| Shortcut    | Fungsi                  |
|-------------|-------------------------|
| `Ctrl + O`  | Save (Write Out)        |
| `Ctrl + X`  | Keluar                  |
| `Ctrl + K`  | Cut line                |
| `Ctrl + U`  | Paste                   |
| `Ctrl + W`  | Cari teks               |
| `Ctrl + \`  | Replace teks            |
| `Ctrl + G`  | Bantuan (help)          |
| `Ctrl + _`  | Go to line              |
| `Alt + U`   | Undo                    |
| `Alt + E`   | Redo                    |
| `Ctrl + C`  | Show cursor position    | 


![17](https://github.com/user-attachments/assets/a5e7ac35-ce0c-4240-885b-58df078a7b5c)


---
## Membuat Server Golang yang Bisa Diakses via Browser
### Menjalankan File Binary (Executable)
```
  pm2 start ./golang-app --name "golang-app"
```

**🔍 Penjelasan Detail:**
