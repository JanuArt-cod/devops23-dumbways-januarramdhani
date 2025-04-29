# 📘 SSH Configuration Documentation: Alias, Custom Ports, and Access Restrictions Based on Public Key

> Dokumen ini berisi panduan konfigurasi SSH di sistem operasi Windows (client) dan Ubuntu Server (server), meliputi :
1. Pembuatan **alias SSH** untuk memudahkan login  
2. Pengubahan **port SSH** dari default ke port khusus (6969)  
3. Pembatasan akses SSH hanya untuk satu device menggunakan **Public Key Authentication**
---
## 1. 🧩 Menambahkan Alias `vm-dumbways` untuk Login SSH

> Tujuannya untuk mempermudah login ke server melalui SSH tanpa perlu mengetik alamat IP, user, dan port setiap kali.

### 🔧 Langkah-langkah:

#### 1.1 Membuat File Konfigurasi `config`
- Buka File Explorer  
- Navigasikan ke:
```
  C:\Users<nama_user>.ssh
```
> Gantilah `<nama_user>` dengan username Windows Anda.
- Jika belum ada file bernama `config`, buat file baru dengan nama **`config`** (tanpa ekstensi)

![1](https://github.com/user-attachments/assets/2658a2a0-d861-42a4-8cb8-fe57fb459786)

#### 1.2 Menulis Konfigurasi Alias SSH
> Buka file `config` dengan Notepad dan isi dengan baris berikut :
```
  Host vm-dumbways
    HostName 192.168.1.28
    User januar
    Port 22
    IdentityFile ~/.ssh/gembok
```

Penjelasan :
- `Host` : Nama alias, bebas ditentukan
- `HostName` : Alamat IP server tujuan
- `User` : Username pada server
- `Port` : Port default SSH (22)
- `IdentityFile` : Lokasi private key untuk autentikasi

![2](https://github.com/user-attachments/assets/52787d0e-28ce-40e2-ac43-b7315f22c855)


#### 1.3 Login dengan Alias
> Buka Windows Terminal atau Git Bash, lalu jalankan :

```
  ssh vm-dumbways
```

![3](https://github.com/user-attachments/assets/fb0f9f54-a6ca-4198-949a-428a0ad0b72e)

---

## 2. 🔐 Mengubah Port Default SSH Menjadi 6969
> Port default SSH adalah 22, dan karena port ini umum digunakan, server yang menjalankan layanan SSH di port tersebut menjadi sasaran empuk untuk pemindaian otomatis dan serangan brute force oleh bot atau penyerang. Dengan mengubah port SSH ke nomor port yang tidak umum (dalam hal ini 6969), maka server akan lebih terlindungi dari serangan semacam itu.

### 🔧 Langkah-langkah :

#### 2.1 Buka File Konfigurasi SSH Server

Masuk ke server Ubuntu Anda menggunakan SSH atau langsung di terminal fisik, lalu jalankan perintah berikut :

```
  sudo nano /etc/ssh/sshd_config
```
> Perintah ini akan membuka file konfigurasi utama SSH dengan editor teks nano. File ini menyimpan semua pengaturan layanan SSH pada server.

![4](https://github.com/user-attachments/assets/f0a92deb-fbb2-4b4f-b001-74073150d9cf)


#### 2.2 Modifikasi Nilai Port

Di dalam file sshd_config, cari baris berikut:

```
  #Port 22
```

![5](https://github.com/user-attachments/assets/c66bd0d1-3be3-4df6-a08f-48f139bfed8b)

> Baris ini menunjukkan bahwa port default SSH adalah 22. Tanda `#` berarti konfigurasi tersebut sedang dikomentari, artinya tidak aktif. Untuk mengaktifkan dan mengubahnya, lakukan dua hal :
> 1. Hapus tanda # di awal baris.
> 2. Ubah angka 22 menjadi 6969.

Sehingga menjadi :
```
  Port 6969
```
> Catatan penting: Pastikan tidak ada baris lain yang mendefinisikan `Port`, agar tidak terjadi konflik saat SSH dijalankan.

![6](https://github.com/user-attachments/assets/6c6b0281-8b9e-4e32-9b72-b64a21ad912f)

#### 2.3 Restart Layanan SSH

Agar perubahan pada konfigurasi diterapkan, Anda perlu me-restart layanan SSH menggunakan:

```
  sudo systemctl restart ssh
```
> Setelah perintah ini dijalankan, SSH akan berhenti mendengarkan di port 22 dan hanya menerima koneksi melalui port 6969.

![7](https://github.com/user-attachments/assets/69edb483-c004-4bb3-9465-452135712030)

```
  exit
```

![8](https://github.com/user-attachments/assets/b96db30f-ca8b-43c7-afdb-dcf758229152)

#### 2.4 Update Konfigurasi Client (Windows)

Karena port yang digunakan telah berubah, Anda juga perlu menyesuaikan konfigurasi pada sisi client, yaitu di file :

```
  C:\Users\<nama_user>\.ssh\config
```
![1](https://github.com/user-attachments/assets/b5f5af90-76c3-4100-9cf8-17ce4a75d17e)

Buka file tersebut dan ubah bagian `Port` menjadi 6969 :

```
  Host vm-dumbways
    HostName 192.168.1.28
    User januar
    Port 6969
    IdentityFile ~/.ssh/gembok
```
![9](https://github.com/user-attachments/assets/7faf43d1-ff05-449b-a318-6c3474237dd6)

Setelah disimpan, Anda dapat mengakses server seperti biasa dengan :
```
  ssh vm-dumbways
```
> Jika login berhasil, artinya port sudah berhasil diganti dan dikonfigurasi dengan benar.

![10](https://github.com/user-attachments/assets/84cd7fa7-6f4c-440f-b02f-d3774f1bae23)
