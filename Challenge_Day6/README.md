# Implementasi Load Balancing untuk Aplikasi Wayshub dengan 2 Server
> Berikut adalah panduan untuk mengimplementasikan load balancing pada aplikasi Wayshub menggunakan 2 server:
## Persiapan Infrastruktur
> Pertama, siapkan 2 server untuk menjalankan aplikasi Wayshub:

| Nama Server     | Hostname         | Alamat IP         |
|------------------|-------------------|--------------------|
| Server1         | januar-januar   | 192.168.1.28      |
| Server_1(anggap saja server2)         | server1-server1   | 192.168.1.10      |
| load balancing    | lb-lb        | 192.168.1.11      |

## 1. Load Balancer (Nginx) - lb-lb (192.168.1.11)
> **Fungsi:** Seperti "polisi lalu lintas" yang mengarahkan request ke 2 server Wayshub.
```
  # Install Nginx
  sudo apt update && sudo apt install nginx -y
```

![1-lb](https://github.com/user-attachments/assets/8820d009-59b1-42d0-85f6-6b6d47970846)

![2](https://github.com/user-attachments/assets/25b24f66-6190-413d-8325-bf38bf186cab)

```
  # Edit config
  sudo nano /etc/nginx/sites-available/wayshub
```

![3](https://github.com/user-attachments/assets/b40e25b2-5579-4b77-a7fe-34f1dd326f25)

### Simpan & Restart:
```
  sudo ln -s /etc/nginx/sites-available/wayshub /etc/nginx/sites-enabled/
  sudo systemctl restart nginx
```
![4](https://github.com/user-attachments/assets/e14d6768-9858-4cd1-8664-750f5f8939aa)

![5](https://github.com/user-attachments/assets/00ce8071-6dcb-420b-bfe8-3b427e5a643f)

---
## 2. App Server 1 - januar-januar (192.168.1.28)
> Fungsi: Menjalankan aplikasi Wayshub di port 3000.

**Install Node.js**
```
  sudo apt install nodejs npm -y
```
> Menginstal nodejs dan npm jika belum terinstall

**Clone repo Wayshub**
```
  https://github.com/dumbwaysdev/wayshub-frontend.git
```
> bagi yang belum clone repo

**Masuk ke direktori & npm install**
```
  cd wayshub
  npm install
```
**Jalankan**
```
  npm start  
```
> Pastikan jalan di port 3000

![6](https://github.com/user-attachments/assets/1aef69d2-f1ff-4a34-b72f-c5a55d9105a0)
![7](https://github.com/user-attachments/assets/f4b592b3-0cee-4d3d-a029-db8885085760)

---
## 2. App Server 2 - server1-server1 (192.168.1.10)
> Fungsi: Sama seperti Server 1 (clone aplikasi Wayshub).
> Langkah:
> - Lakukan persis seperti Server 1 (install Node.js, clone repo, dll).
> - Pastikan aplikasi jalan di port 3000.

**Install Node.js**
```
  sudo apt install nodejs npm -y
```
> Menginstal nodejs dan npm jika belum terinstall

**Clone repo Wayshub**
```
  https://github.com/dumbwaysdev/wayshub-frontend.git
```
> bagi yang belum clone repo

**Masuk ke direktori & npm install**
```
  cd wayshub
  npm install
```
**Jalankan**
```
  npm start  
```
> Pastikan jalan di port 3000

![8](https://github.com/user-attachments/assets/b1185075-4f7f-4aa0-b8bb-fa98adc02e0f)

## Cara Testing
### Akses Load Balancer
> Buka browser atau curl :
```
  curl http://192.168.1.28 -> akses server 1 
```

![10](https://github.com/user-attachments/assets/2657d666-a4cf-462b-9ca8-2a96a350d8b3)

```
  curl http://192.168.1.10  -> akses server 2
```

![9](https://github.com/user-attachments/assets/b67b323e-eeb1-4b86-8d4e-989b97ee2469)

```
  curl -I http://192.168.1.28 -> akses server 1
  curl -I http://192.168.1.10  -> akses server 2
```
![11](https://github.com/user-attachments/assets/665b1832-131b-424b-8535-b2cbaa0a2cdf)


