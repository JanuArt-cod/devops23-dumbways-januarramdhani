# 🔐 Membuat Repositori GitHub `devops-dumbways-januarramdhani` Menjadi Private
> Jika kamu memiliki sebuah repositori di GitHub yang sebelumnya bersifat *public* (dapat diakses siapa pun), dan kamu ingin mengubahnya menjadi *private* (hanya bisa diakses oleh pemilik atau kolaborator yang diizinkan), ikuti langkah-langkah berikut :

## 1. Masuk ke Repositori

> - Buka browser dan akses halaman repositori:  
> `https://github.com/JanuArt-cod/devops-dumbways-januarramdhani`
> - Klik menu **Settings** di bagian atas halaman repositori.

## 2. Ubah Visibilitas Repositori

> - Di halaman Settings, scroll ke bawah hingga kamu menemukan bagian **Danger Zone**.
> - Klik tombol **"Change visibility"**, lalu pilih opsi **"Change to private"**.

![1](https://github.com/user-attachments/assets/8536277f-eff5-4835-a4ca-9790a345eb45)

## 3. Konfirmasi Pengubahan

> - Akan muncul jendela konfirmasi, klik **"I want to make this repository private"**.

![2](https://github.com/user-attachments/assets/fef55456-83c8-4255-a696-05f526fc3216)


> - Centang checkbox **"I have read and understand these effects"** untuk menyatakan bahwa kamu memahami konsekuensi dari perubahan ini.

![3](https://github.com/user-attachments/assets/b3a20858-bf59-43ae-845d-eae877b79295)

  
> - Saat kamu akan mengubah visibilitas repositori GitHub dari public menjadi private, GitHub akan menampilkan jendela konfirmasi akhir sebelum proses dilakukan. Salah satu langkah konfirmasi yang muncul adalah :
> `"To confirm, type the number of stars on this repository in the box below"`
> - Apa Artinya?
> GitHub ingin memastikan bahwa kamu benar-benar menyadari dampak dari tindakan ini, yaitu :
> Bintang (stars) dan pengamat (watchers) dari pengguna yang tidak memiliki akses setelah repositori menjadi private akan dihapus secara permanen. Untuk mengonfirmasi tindakan ini, kamu diminta untuk mengetik jumlah bintang dari repositorimu saat ini di kolom yang disediakan.
> ✅ Jika Tidak Ada Bintang
> Jika repositorimu tidak memiliki bintang (0 star), maka cukup masukkan angka 0 ke dalam kolom konfirmasi tersebut.

```
💡 Contoh :
  Jika repositori kamu memiliki:
  1 star, maka kamu perlu mengetik 1
  0 star, maka kamu perlu mengetik 0
```
> Setelah angka diketik sesuai, tombol `"Make this repository private"` akan aktif dan dapat diklik untuk menyelesaikan proses perubahan visibilitas.

![4](https://github.com/user-attachments/assets/0ed352da-478a-4de8-ac51-63c396f36333)

## 4. Verifikasi Identitas

> - GitHub akan meminta kamu memasukkan **password akun GitHub** untuk verifikasi.

![5](https://github.com/user-attachments/assets/b53d3789-6fec-497a-aa8f-dbfa631d5b01)

> - Setelah berhasil, repositori kamu akan menjadi **private** dan tidak lagi bisa diakses oleh publik.

![6](https://github.com/user-attachments/assets/36aeb1fc-c846-4d7b-b2cf-ef6fd1470547)

---

# 🔄 Demonstrasi Proses Pull Request Sebagai Kontributor
> Bagian ini menjelaskan langkah demi langkah bagaimana seseorang dapat berkontribusi terhadap repositori GitHub melalui proses pull request, seperti yang dilakukan oleh seorang kontributor eksternal terhadap repositori `dumbways-devops-23`. Simulasi ini menggambarkan alur kolaborasi dalam proyek menggunakan Git dan GitHub, mulai dari cloning repositori, membuat branch baru, melakukan perubahan, hingga membuat dan menyelesaikan pull request.

## A. Menyiapkan Lingkungan Lokal
### 1. Clone Repositori Sebagai Kontributor
> Pertama, seorang kontributor harus melakukan clone repositori dari GitHub ke dalam direktori lokal di komputernya. Misalnya dengan nama folder kontributor.
```
  git clone git@github.com:JanuArt-cod/dumbways-devops-23.git kontributor
```

![8](https://github.com/user-attachments/assets/c1be6330-2792-4a4e-9b02-443ca9ee386c)

### 2. Masuk ke Direktori dan Buat Branch Baru
> Setelah berhasil di-clone, masuk ke direktori `kontributor`, lalu buat branch baru untuk memisahkan perubahan dari branch utama (`main`).
```
  cd kontributor
```
![9](https://github.com/user-attachments/assets/f735cd98-fe42-4732-9dd7-265b98b97fe4)

```
  git checkout -b fitur_login
```
![10](https://github.com/user-attachments/assets/2b82caf6-9003-4bb5-990e-d5ce8dec7647)

```
  git status
```
![11](https://github.com/user-attachments/assets/7ffced63-8408-421a-b57f-ca8c9c0a8b2b)

> Branch `fitur_login` ini digunakan khusus untuk mengembangkan fitur tertentu, misalnya halaman login.

## B. Melakukan Perubahan pada File
### 1. Melihat dan Mengedit File
> Cek file yang ada di dalam repositori, lalu pilih file yang akan diedit. Misalnya `file1`.
```
  ls
  cat file1
```
> Edit file tersebut menggunakan editor teks, seperti `nano`.
```
  nano file1
```
![12](https://github.com/user-attachments/assets/6757e881-faa9-4a04-a208-6266f8b5f61f)
> Setelah selesai melakukan perubahan, kamu bisa melihat kembali isinya :
```
  cat file1
```
![13](https://github.com/user-attachments/assets/fe479d54-a6a5-4a55-b395-4e67fd7aad49)
> Cek status file yang diubah :
```
  git status
```
![14](https://github.com/user-attachments/assets/eac3bfab-eb72-4ae5-9d63-0f14bb3547c0)

## C. Menyimpan dan Mengirim Perubahan ke GitHub
### 1. Commit dan Push Perubahan
> Setelah melakukan perubahan, file perlu disimpan dalam Git menggunakan perintah `add`, lalu disimpan ke dalam riwayat perubahan menggunakan `commit`, dan dikirim ke GitHub menggunakan `push`.
```
  git add .
  git commit -m "menambahkan text insyaallah berkah"
```
![15](https://github.com/user-attachments/assets/43f30fef-0cce-421c-aa55-8b63e3c2814f)

```
  git push origin fitur_login
```
![16](https://github.com/user-attachments/assets/305524bb-97ea-46e5-8c62-45db31222a39)
