# Implementasi Load Balancing untuk Aplikasi Wayshub dengan 2 Server
> Berikut adalah panduan untuk mengimplementasikan load balancing pada aplikasi Wayshub menggunakan 2 server:
## Persiapan Infrastruktur
> Pertama, siapkan 2 server untuk menjalankan aplikasi Wayshub:

| Nama Server     | Hostname         | Alamat IP         |
|------------------|-------------------|--------------------|
| server1    | lb@lb        | 192.168.1.11      |
| Server2         | januar@januar   | 192.168.1.28      |

# server1 lb@lb(192.168.1.11)
> **Fungsi:** Seperti "polisi lalu lintas" yang mengarahkan request ke 2 server Wayshub.
### Install Nginx
```
  sudo apt update && sudo apt install nginx -y
```
![1-lb](https://github.com/user-attachments/assets/a962bc54-b44d-4b99-ad70-01e0fae2debb)

```
  cd /etc/nginx/sites-enabled
```
```
  sudo nano loadbalancer.conf
```
![6-ls](https://github.com/user-attachments/assets/69869d90-a9b6-42cd-ae21-6ef04458cc72)

### Tambahkan konfigurasi berikut:
```
  upstream frontend_cluster {
    server 192.168.1.11:3000; # Server 1
    server 192.168.1.28:3000; # Server 2
}

server {
    listen 80;
    server_name myapp.test;

    location / {
        proxy_pass http://frontend_cluster;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}

```
![5-lb](https://github.com/user-attachments/assets/a2961450-9cc1-4ce1-ad0b-b19809261f9b)

> **Penjelasan:**
> - `upstream frontend_cluster` mendefinisikan dua backend server untuk menerima trafik secara bergantian.
> - `proxy_pass` meneruskan permintaan pengguna ke salah satu server yang tersedia.
> - `proxy_set_header` menyisipkan header tambahan agar informasi pengguna tetap diteruskan ke backend server.

### Uji konfigurasi nginx
```
  sudo nginx -t
```
![3-lb](https://github.com/user-attachments/assets/b8dcd630-29e2-4466-9ca9-2d493b25e9cd)

```
  sudo systemctl restart nginx
```
![4-lb](https://github.com/user-attachments/assets/528628e3-7703-412f-85c3-88db086274db)

---
# Penambahan Identifier pada Project
### Tujuan:
*"Untuk mengetahui dari server mana response web berasal."*

### Langkah :
> Edit file public/index.html pada masing-masing server.
> Tambahkan teks yang membedakan:
> - Misalnya:
> - Di Server 1: Server dari: webbalancer1
> - Di Server 2: Server dari: webserver2

# Menjalankan Project dengan PM2
### Tujuan:
*"Agar aplikasi tetap berjalan walaupun terminal ditutup."*
### Langkah:
Jalankan aplikasi dengan pm2

```
  pm2 start npm --name "server1" -- start
  pm2 start npm --name "server2" -- start
```

![7-lb](https://github.com/user-attachments/assets/8eb44e95-9461-4ae7-acfd-f2dc79d0caa9)

![8-lb](https://github.com/user-attachments/assets/751e4559-0c0a-4864-b72d-e046470fffa4)


# Pengujian Load Balancer
### Akses Load Balancer
> Buka browser atau curl :

### Langkah:
> - Akses http://januar.xyz berkali-kali dari browser.
> - Lihat teks dari masing-masing server (yang sudah ditandai).

![Screenshot 2025-05-06 012636](https://github.com/user-attachments/assets/cf4ca78c-c696-423b-95ba-e01012ed02c6)

![Screenshot 2025-05-06 012715](https://github.com/user-attachments/assets/8fb8f469-5c0e-48f3-8e52-73aca4bb3e52)

