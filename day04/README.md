# 📙 Version Control System (VCS) dengan Git dan GitHub

---

## 🛠️ Pengenalan Git

**Git** adalah perangkat lunak Version Control System (VCS) yang digunakan untuk mencatat, mengelola, dan mengontrol setiap perubahan yang terjadi pada file proyek secara sistematis. Git memungkinkan kolaborasi antara banyak developer tanpa takut konflik perubahan.

Git diciptakan oleh Linus Torvalds pada tahun 2005 untuk membantu pengembangan kernel Linux. Git dirancang agar cepat, efisien, aman, dan mampu mendukung proyek berskala besar.

### 🔹 Fungsi Utama Git
- **Tracking perubahan**: Melacak riwayat perubahan kode secara lengkap.
- **Kolaborasi**: Banyak orang bisa mengerjakan proyek yang sama tanpa mengganggu hasil kerja satu sama lain.
- **Branching dan Merging**: Membuat percabangan pengembangan fitur atau eksperimen tanpa mengganggu branch utama.
- **Rollback**: Kembali ke kondisi sebelumnya jika ada kesalahan.

### 🔹 Kelebihan Git dibanding VCS lain
- **Terdistribusi penuh**: Setiap developer memiliki salinan penuh dari repositori.
- **Cepat**: Operasi lokal (commit, branch, merge) sangat cepat karena tidak memerlukan koneksi server.
- **Aman**: Data commit dienkripsi dan diverifikasi.
- **Fleksibel**: Cocok untuk proyek kecil hingga sangat besar.

> **Kesimpulan:** Git adalah pilar utama dalam pengembangan perangkat lunak modern.

---

# ✨ Langkah Membuat Repository GitHub dan Push Proyek Lokal

Langkah-langkah lengkap mulai dari konfigurasi hingga push:

### 1. Konfigurasi Username dan Email Git

```bash
git config --global user.name "nama"
git config --global user.email "email"
git config --list
```
- Ini mengatur identitas yang akan tertulis dalam setiap commit.

![1](https://github.com/user-attachments/assets/b47a6dfb-71e0-404b-86f9-ede5eb320c03)


### 2. Membuat SSH Key dan Hubungkan ke GitHub

- Cek apakah sudah ada SSH key:
```bash
cd ~/.ssh
ls
```
- Jika belum, buat SSH key:
```bash
ssh-keygen
```

![0](https://github.com/user-attachments/assets/5eead083-61e3-4445-af8a-1457335c044d)

- Salin public key:
```bash
cat id_rsa.pub
```

![3](https://github.com/user-attachments/assets/bc10ed84-8b11-4409-9a25-5f6e821f40e4)


- Tambahkan ke GitHub via Settings ➔ SSH and GPG Keys ➔ New SSH Key.

![4](https://github.com/user-attachments/assets/5eba2c95-7d35-45fc-937e-e43c58701e4a)

![5](https://github.com/user-attachments/assets/ac41f842-cd1f-4d16-ba59-6041a3186a18)

- Tes koneksi:
```bash
ssh git@github.com -T
```

![7](https://github.com/user-attachments/assets/8f1653d8-7e01-4963-a8fa-f4eaa5588e23)


> **Mengapa SSH?** Agar lebih aman dan tidak perlu login setiap push.

### 3. Membuat Proyek Lokal

- Buat folder dan file:
```bash
mkdir dumbways-batch-23
ls
```
![8](https://github.com/user-attachments/assets/dbcc6fb0-6811-4e85-95e1-d30e124a77ea)

```
cd dumbways-batch-23
```
![9](https://github.com/user-attachments/assets/4527a746-83bb-413c-8813-ff2cebb0e6b5)

```bash
cat > file1
cat > file2
cat file1 file2 > file3
```
![10](https://github.com/user-attachments/assets/b0419e18-bbb2-44e4-84fd-0ae8a0c3221c)

- Inisialisasi Git:
```bash
git init dumbways-devops-23
```
![11](https://github.com/user-attachments/assets/2156f472-91c2-4732-a127-4470c05de64a)

- Salin file:
```bash
cp file1 dumbways-devops-23/file1
cp file2 dumbways-devops-23/file2
cp file3 dumbways-devops-23/file3
```

![13](https://github.com/user-attachments/assets/7ce966ac-9523-4393-9372-8c4b4e648c88)

- Melihat seluruh file:
```bash
ls -la
```

![14](https://github.com/user-attachments/assets/43485cc0-9835-4700-8309-232eb81e0081)


### 4. Mengatur `.gitignore`

- Buat file:
```bash
nano .gitignore
```
Isi `.gitignore`:
```
filemaster
```

![16](https://github.com/user-attachments/assets/b0e10c39-3371-4813-9899-0a25de953db8)

![15](https://github.com/user-attachments/assets/a32cdd05-22f8-452d-ab2b-2a5641331092)


- Cek status:
```bash
git status
```

![18](https://github.com/user-attachments/assets/b8f11ff4-7488-4bb5-9648-c0524f50dab5)


### 5. Menambahkan File dan Commit

- Tambahkan file:
```bash
git add .
```

![19](https://github.com/user-attachments/assets/5fc8490e-34c4-488c-8f87-92a31cee81d9)

- Buat commit:
```bash
git commit -m "First commit"
```

![20](https://github.com/user-attachments/assets/e3dfa01c-ca33-413b-a497-e39b4ed76cc5)

### 6. Hubungkan dan Push ke GitHub

![23](https://github.com/user-attachments/assets/002c366c-db89-4073-84dc-62afe93ac00e)

![25](https://github.com/user-attachments/assets/2f5fda73-4750-4cd1-bda5-3e196ae65077)

- Tambahkan remote origin:
```bash
git remote add origin git@github.com:JanuArt-cod/devops23-dumbways-januarramdhani.git
```
![24](https://github.com/user-attachments/assets/3f521ef9-dc44-462b-a382-9d3b14844e22)

- Ganti branch jika perlu:
```bash
git branch -M main
```

![26](https://github.com/user-attachments/assets/cb04d062-cca0-42f7-b9dc-7200f60ccbd9)

- Push perubahan:
```bash
git push -u origin main
```

![28](https://github.com/user-attachments/assets/f3ebc554-c2dc-4fa4-a88d-676b04a5d421)

![29](https://github.com/user-attachments/assets/bf2cd4ac-15ec-41e6-9dfb-6487b4bb16a0)

---

# 📙 Mengelola Tugas Harian dengan Git

Setelah repository berjalan, berikut cara rutin mengelola perubahan:

1. Cek perubahan:
```bash
git status
```

![31](https://github.com/user-attachments/assets/d9e0a85d-8896-4398-8129-5a214783c38e)

2. Tambahkan perubahan:
```bash
mkdir day04
touch day04/README.md
ls
git status
```

![32](https://github.com/user-attachments/assets/b901268d-3035-4269-a765-43bb4c661fdf)

2. Tambahkan perubahan:
```bash
git add .
git status
```

![33](https://github.com/user-attachments/assets/b01c523b-b69b-4643-a109-86eba6e3d34b)

3. Commit perubahan:
```bash
git commit -m "Menambahkan folder day4 untuk task dumbways"
```

![34](https://github.com/user-attachments/assets/410ed720-d675-42f9-90f7-bb50036046f3)


4. Push ke GitHub:
```bash
git push -u origin main
```

![36](https://github.com/user-attachments/assets/69071731-850c-4f5c-a13e-995b685e14bc)

---

![38](https://github.com/user-attachments/assets/c8c1fade-7765-4e91-ba0b-ad30870fb16f)

# 💚 Kesimpulan

Git dan GitHub adalah pondasi penting dalam pengembangan perangkat lunak modern. Dengan menguasai:
- Perintah dasar,
- Manajemen branch,
- Hubungan dengan remote repository,
- Workflow commit dan push,

kita dapat membangun proyek yang terstruktur, kolaboratif, dan profesional.
