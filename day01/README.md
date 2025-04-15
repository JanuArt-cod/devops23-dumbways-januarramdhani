# Day 1 - Introduction to DevOps

## 1.Istilah DevOps

DevOps adalah implementasi berkolaborasi antara tim development dan operations untuk mempercepat proses pengembangan dan pengiriman aplikasi. DevOps adalah :

- **Integration (CI)** : _proses otomatis penggabungan perubahan kode dari beberapa kontributor ke dalam repositori utama._
- **Delivery (CD)** : _proses otomatis untuk menguji dan menyebarkan aplikasi ke produksi secara berkelanjutan._
- **Deployment** : _setiap perubahan yang lolos tahap pengujian akan diterapkan secara otomatis._

## 2. Virtual Machine

Saya menggunakan Ubuntu Server pada VirtualBox.

## 3.Buat 1 Virtual Machine

Kamu bebas pilih tools seperti:
```
- **VirtualBox**
- **VMware**
- **Multipass**
```
Contoh cara buat VM dengan VirtualBox :

**1. Buka `VirtualBox`**
**1. Klik `"New"`**
**2. Pilih OS: `Ubuntu/Linux`**
**3. Atur RAM `(minimal 1GB) & disk (10GB)`**
**4. Klik `"Create"`**
**5. Jalankan `VM` dan install `Ubuntu/Linux`**

## 4.Install Nginx WebServer di VM

Setelah VM jalan dan kamu sudah masuk terminal :
```bash
sudo apt update
sudo apt install nginx -y
```

Cek apakah nginx berhasil :
```bash
systemctl status nginx
```
Cek dari browser: akses IP `192.168.1.10` untuk melihat halaman default nginx.
