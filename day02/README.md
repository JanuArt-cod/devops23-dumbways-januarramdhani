# Diagram Jaringan Komputer


![Diagram Jaringan drawio (1)](https://github.com/user-attachments/assets/f3ed0a0f-40cb-4bf9-8e29-0d1181b08a89)

## 🌐 Informasi Jaringan
- **IP Kelas C**: `192.168.11.xxx`
- **Blok CIDR**:
  - Subnet 1: `192.168.11.0/30`
  - Subnet 2: `192.168.11.4/30`
- **Subnet Mask**: `255.255.255.252`
- **Jumlah Perangkat**: 4 unit (PC A, PC B, PC C, PC D)
- **DNS**: Cloudflare `1.1.1.1` dan Google `8.8.8.8`

## Diagram
1. Diagram ini menggunakan IP Kelas C dengan subnetting menggunakan CIDR /30, dan terdiri dari 4 perangkat yang dibagi menjadi 2 subnet kecil.
2. Koneksi Internet Router terhubung ke internet
3. Router Sebagai pusat jaringan dan penghubung antar subnet
4. Total perangkat 4 komputer (A, B, C, D)
5. **Subnet 1**
   ```
   PC A        192.168.11.1
   PC B        192.168.11.2
   Network ID  192.168.11.0
   Broadcast   192.168.11.3
   Subnet Mask 255.255.255.252
   ````
6. **Subnet 2**
    ```
   PC C        192.168.11.5
   PC D        192.168.11.6
   Network ID  192.168.11.4
   Broadcast   192.168.11.7
   Subnet Mask 255.255.255.252
   ````
## Alur Koneksi
1. Internet mengarah ke router pusat.
2. Router membagi jaringan menjadi dua subnet kecil.
3. Subnet 1 menghubungkan Komputer A dan B.
4. Subnet 2 menghubungkan Komputer C dan D.
5. Masing-masing subnet memiliki alamat network, broadcast, dan host IP sesuai pembagian CIDR /30.

## Perbedaan Shell dan Bash

|---------------|------------------------------------------------|---------------------------------------------|
| Aspek         | SH (Shell)                                     | BASH (Bourne-Again Shell)                   |
|---------------|------------------------------------------------|---------------------------------------------|
| Definisi      | Antarmuka baris perintah umum buat komunikasi  | Bourne Again Shell, pengembangan dari Bourne
                                                                   Shell (sh) dengan fitur lebih kaya.
                  dengan sistem operasi.
