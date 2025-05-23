# Day 1 - Introduction to DevOps

## 1. Istilah DevOps

DevOps adalah implementasi berkolaborasi antara tim development dan operations untuk mempercepat proses pengembangan dan pengiriman aplikasi. DevOps adalah :

- **Integration (CI)** : _proses otomatis penggabungan perubahan kode dari beberapa kontributor ke dalam repositori utama._
- **Delivery (CD)** : _proses otomatis untuk menguji dan menyebarkan aplikasi ke produksi secara berkelanjutan._
- **Deployment** : _setiap perubahan yang lolos tahap pengujian akan diterapkan secara otomatis._

## 2. Virtual Machine

Disini saya menggunakan `VirtualBox.`

![VirtualBox.](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRbmKsWKCY_H0bNgedHjXJMoop2-fajr7ZYiw&s)

dan Operating system saya `Ubuntu Server.`

![Ubuntu Server.](https://www.osboxes.org/wp-content/uploads/2018/04/ubuntu-server-desktop-post.png)

## 3. Buat 1 Virtual Machine

Kamu bebas pilih tools seperti:

1. VirtualBox
2. VMware
3. Multipass
4. etc

Contoh cara buat VM dengan VirtualBox :

- Buka `VirtualBox`
- Klik `"New"`
- Pilih OS: `Ubuntu/Linux`
- Atur RAM `(minimal 1GB)` & `disk (10GB)`
- Klik `"Create"`
- Jalankan `VM` dan install `Ubuntu/Linux`

## 4. Install Nginx WebServer di VM

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




![Screenshot of a comment on a GitHub issue showing an image, added in the Markdown, of an Octocat smiling and raising a tentacle.](https://myoctocat.com/assets/images/base-octocat.svg)
