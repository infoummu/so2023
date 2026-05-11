---
title: Praktikum 01 - Pengenalan Linux dan Command Line Dasar
author: Ikhwan N. Elyas
category: Halaman Materi
published: true
description: Mahasiswa mengenal lingkungan Linux, struktur direktori, perintah dasar terminal, navigasi file, manajemen file dan folder, membaca manual, serta memahami hubungan command line dengan sistem operasi sebagai fondasi praktikum berikutnya dalam mata kuliah Sistem Operasi.
---

# Praktikum 1: Pengenalan Linux dan Command Line Dasar

## A. Tujuan Praktikum
Setelah mengikuti praktikum ini, mahasiswa diharapkan mampu:
1. Menjelaskan lingkungan kerja Linux sebagai sistem operasi yang digunakan dalam kegiatan praktikum.
2. Menggunakan terminal untuk menjalankan perintah-perintah dasar sistem operasi.
3. Melakukan navigasi direktori serta pengelolaan file dan folder sederhana.
4. Mengidentifikasi fungsi beberapa direktori penting dalam sistem Linux.
5. Menggunakan dokumentasi bantuan seperti `man` untuk mempelajari perintah Linux.
6. Menjelaskan peran command line sebagai sarana interaksi pengguna dengan sistem operasi.

## B. Dasar Teori
Sistem operasi merupakan perangkat lunak yang berfungsi sebagai penghubung antara pengguna dengan perangkat keras komputer, sekaligus mengelola berbagai sumber daya sistem. Pada praktikum ini, sistem operasi yang digunakan adalah Linux. Linux dipilih karena banyak konsep dasar sistem operasi dapat diamati dan dipraktikkan secara langsung melalui terminal.

Terminal atau *command line interface* (CLI) adalah antarmuka berbasis teks yang memungkinkan pengguna memberikan instruksi langsung kepada sistem operasi. Melalui terminal, pengguna dapat melakukan berbagai aktivitas seperti menavigasi direktori, mengelola file, menjalankan program, serta mengakses utilitas sistem secara efisien.

Beberapa konsep dasar yang perlu dipahami dalam praktikum ini meliputi:
- **Direktori kerja (*working directory*)**: lokasi aktif tempat pengguna sedang bekerja.
- **File dan direktori**: objek yang dikelola oleh sistem operasi.
- **Path**: alamat atau lokasi dari file maupun direktori.
- **Manual page (`man`)**: dokumentasi bantuan bawaan Linux untuk memahami fungsi suatu perintah.
- **Struktur direktori Linux**: misalnya `/home`, `/bin`, `/etc`, `/dev`, dan `/proc`.

Praktikum ini menjadi landasan awal untuk praktikum-praktikum berikutnya, khususnya pada materi shell scripting, manajemen proses, system call, dan file system.

## C. Alat dan Bahan
1. Komputer atau laptop.
2. Sistem operasi Linux, seperti Ubuntu, Linux Mint, WSL, atau Linux pada mesin virtual.
3. Akses ke terminal.
4. Editor teks sederhana, jika diperlukan.

## D. Materi Praktikum
Pada praktikum ini, mahasiswa akan menggunakan beberapa perintah dasar Linux sebagai berikut:
- `pwd` : menampilkan direktori kerja saat ini.
- `ls` : menampilkan isi direktori.
- `cd` : berpindah direktori.
- `mkdir` : membuat direktori.
- `touch` : membuat file kosong.
- `cp` : menyalin file atau folder.
- `mv` : memindahkan atau mengubah nama file/folder.
- `rm` : menghapus file.
- `rmdir` : menghapus direktori kosong.
- `cat` : menampilkan isi file.
- `less` : menampilkan isi file per halaman.
- `man` : membuka dokumentasi bantuan.
- `clear` : membersihkan layar terminal.

## E. Langkah Kerja Praktikum

### Percobaan 1: Mengidentifikasi Direktori Kerja
1. Buka terminal Linux.
2. Jalankan perintah berikut:

```bash
pwd
```

3. Amati direktori kerja yang sedang aktif.
4. Tampilkan isi direktori dengan perintah berikut:

```bash
ls
```

5. Tampilkan isi direktori secara rinci:

```bash
ls -l
```

6. Tampilkan pula file tersembunyi dengan perintah:

```bash
ls -a
```

### Percobaan 2: Navigasi Direktori
1. Pindah ke direktori home dengan perintah:

```bash
cd ~
```

2. Periksa kembali posisi direktori saat ini:

```bash
pwd
```

3. Buat folder baru dengan nama `praktikum_so`:

```bash
mkdir praktikum_so
```

4. Masuk ke folder tersebut:

```bash
cd praktikum_so
```

5. Buat dua folder baru bernama `materi` dan `tugas`:

```bash
mkdir materi tugas
```

6. Tampilkan isi direktori untuk memastikan folder berhasil dibuat:

```bash
ls
```

### Percobaan 3: Membuat dan Mengelola File
1. Masuk ke folder `materi`:

```bash
cd materi
```

2. Buat file kosong dengan nama `pertemuan1.txt`:

```bash
touch pertemuan1.txt
```

3. Tampilkan hasilnya:

```bash
ls -l
```

4. Tampilkan isi file:

```bash
cat pertemuan1.txt
```

5. Salin file tersebut menjadi file baru:

```bash
cp pertemuan1.txt salinan_pertemuan1.txt
```

6. Ubah nama file salinan menjadi `catatan1.txt`:

```bash
mv salinan_pertemuan1.txt catatan1.txt
```

7. Tampilkan kembali isi direktori:

```bash
ls -l
```

### Percobaan 4: Menghapus File dan Menavigasi Direktori
1. Hapus file `catatan1.txt`:

```bash
rm catatan1.txt
```

2. Periksa kembali isi folder:

```bash
ls -l
```

3. Kembali ke folder `praktikum_so`:

```bash
cd ..
```

4. Masuk ke folder `tugas`, tampilkan direktori aktif, kemudian kembali ke folder sebelumnya:

```bash
cd tugas
pwd
cd ..
```

### Percobaan 5: Menggunakan Dokumentasi Bantuan
1. Buka manual perintah `ls`:

```bash
man ls
```

2. Bacalah deskripsi singkat beserta beberapa opsi penting yang tersedia.
3. Keluar dari halaman manual dengan menekan tombol `q`.
4. Lakukan hal yang sama untuk perintah berikut:

```bash
man pwd
man mkdir
```

### Percobaan 6: Mengamati Struktur Direktori Linux
1. Amati fungsi beberapa direktori berikut:
   - `/home` : menyimpan data pengguna.
   - `/bin` : berisi program atau perintah dasar.
   - `/etc` : berisi file konfigurasi sistem.
   - `/dev` : representasi perangkat keras.
   - `/proc` : menyediakan informasi proses dan kernel secara virtual.

2. Lakukan eksplorasi sederhana menggunakan perintah berikut:

```bash
cd /
ls
cd /home
ls
cd /etc
ls
```

3. Catat hasil pengamatan pada laporan praktikum.

**Catatan:** Pada percobaan ini mahasiswa hanya melakukan pengamatan, bukan melakukan perubahan pada direktori sistem.

## F. Tugas Analisis
Jawablah pertanyaan berikut berdasarkan hasil praktikum:
1. Jelaskan fungsi perintah `pwd`, `ls`, dan `cd`.
2. Jelaskan perbedaan antara file dan direktori.
3. Mengapa *command line* penting dalam pembelajaran sistem operasi?
4. Jelaskan fungsi direktori `/home`, `/etc`, dan `/proc`.
5. Apa manfaat perintah `man` dalam penggunaan Linux?

## G. Tugas Praktikum Mandiri
Kerjakan tugas berikut secara mandiri:
1. Buat folder baru bernama `latihan1` di dalam folder `praktikum_so`.
2. Di dalam folder `latihan1`, buat tiga file kosong bernama:
   - `data1.txt`
   - `data2.txt`
   - `data3.txt`
3. Salin `data1.txt` menjadi `backup_data1.txt`.
4. Ubah nama `data2.txt` menjadi `hasil2.txt`.
5. Hapus file `data3.txt`.
6. Dokumentasikan seluruh langkah yang dilakukan beserta hasilnya.

## H. Tugas Akhir Praktikum
Sebagai penguatan pemahaman, kerjakan tugas berikut:
1. Praktikkan kembali seluruh materi pada modul ini di **environment Windows**.
2. Gunakan perangkat yang paling mendekati *command line* Linux, seperti **Command Prompt**, **PowerShell**, atau **WSL** apabila tersedia.
3. Bandingkan secara singkat pengalaman penggunaan *command line* di Linux dan Windows.
4. Susun **laporan praktikum** secara lengkap.
5. Isi laporan harus memuat:
   - identitas praktikan,
   - tujuan praktikum,
   - langkah kerja,
   - **screenshot hasil praktikum**,
   - penjelasan setiap percobaan,
   - jawaban tugas analisis,
   - kesimpulan 3 atau 4 poin.

### Format Laporan
Laporan dikumpulkan secara individu dengan sistematika sebagai berikut:
1. Judul praktikum.
2. Nama dan NIM.
3. Tujuan praktikum.
4. Dasar teori singkat.
5. Langkah kerja.
6. Hasil praktikum disertai screenshot.
7. Pembahasan atau analisis.
8. Jawaban tugas mandiri.
9. Hasil praktik ulang di Windows.
10. Kesimpulan.
11. Berikan nama File Laporannya:  **Laporan_Tugas_Praktikum1_npm.pdf**
12. Upload Laporannya (File PDF)  Sekalian Absen di **[https://so.elyas.site](https://so.elyas.site/){:target="_blank"}**
13. Tugas dikumpul dan batas waktu kumpul hari Rabu: **13/05/2025 Jam 23:59 (Rabu Malam)**


## J. Kesimpulan
Melalui praktikum ini, mahasiswa memperoleh pengenalan awal mengenai penggunaan Linux dan terminal sebagai sarana interaksi dengan sistem operasi. Pemahaman yang diperoleh pada praktikum ini diharapkan menjadi dasar yang kuat untuk mengikuti praktikum-praktikum berikutnya, khususnya yang berkaitan dengan shell scripting, manajemen proses, file system, dan system call.
