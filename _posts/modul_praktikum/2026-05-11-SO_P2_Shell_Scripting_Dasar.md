---
title: Praktikum 02 - Shell Scripting Dasar
author: Ikhwan N. Elyas
category: Halaman Materi
published: true
description: Mahasiswa mempelajari dasar shell scripting di Linux, meliputi struktur skrip, eksekusi file script, penggunaan variabel, input, percabangan, perulangan, dan otomasi tugas sederhana untuk memperkuat pemahaman interaksi pengguna dengan sistem operasi melalui command line.
---

# Praktikum 2: Shell Scripting Dasar

## A. Tujuan Praktikum
Setelah mengikuti praktikum ini, mahasiswa diharapkan mampu:
1. Menjelaskan pengertian shell script dan fungsinya dalam sistem operasi Linux.
2. Membuat dan menjalankan file shell script sederhana.
3. Menggunakan variabel, input pengguna, dan argumen pada shell script.
4. Mengimplementasikan struktur percabangan dan perulangan sederhana.
5. Membuat otomasi tugas sederhana menggunakan shell script.
6. Menjelaskan manfaat shell scripting dalam administrasi dan pengelolaan sistem.

## B. Dasar Teori
Shell merupakan antarmuka yang menerima perintah dari pengguna dan meneruskannya kepada sistem operasi untuk diproses. Pada Linux, salah satu shell yang umum digunakan adalah **Bash** (*Bourne Again Shell*). Selain digunakan untuk menjalankan perintah secara interaktif, shell juga dapat digunakan untuk menyusun serangkaian perintah dalam bentuk skrip.

Shell script adalah file teks yang berisi kumpulan perintah Linux yang dieksekusi secara berurutan. Dengan shell script, pengguna dapat melakukan otomasi tugas-tugas yang berulang sehingga pekerjaan menjadi lebih cepat, konsisten, dan efisien.

Beberapa konsep penting pada shell scripting meliputi:
- **Shebang** (`#!/bin/bash`) untuk menunjukkan interpreter yang digunakan.
- **Variabel** untuk menyimpan data sementara.
- **Input pengguna** menggunakan `read`.
- **Argumen script** seperti `$1`, `$2`, dan seterusnya.
- **Percabangan** menggunakan `if`.
- **Perulangan** menggunakan `for` atau `while`.

Dalam konteks sistem operasi, shell scripting penting karena memperlihatkan bagaimana pengguna dapat menginstruksikan sistem operasi untuk melaksanakan serangkaian tugas secara otomatis.

## C. Alat dan Bahan
1. Komputer atau laptop.
2. Sistem operasi Linux, seperti Ubuntu, Linux Mint, WSL, atau Linux pada mesin virtual.
3. Terminal Linux.
4. Editor teks seperti `nano`, `vim`, `gedit`, atau Visual Studio Code.

## D. Materi Praktikum
Pada praktikum ini, mahasiswa akan mempelajari:
- struktur dasar shell script,
- pembuatan dan eksekusi file script,
- penggunaan variabel,
- penerimaan input dari pengguna,
- penggunaan argumen baris perintah,
- percabangan sederhana,
- perulangan sederhana,
- otomasi tugas sederhana.

## E. Langkah Kerja Praktikum

### Percobaan 1: Membuat Shell Script Sederhana
1. Buka terminal Linux.
2. Pindah ke direktori kerja yang diinginkan.
3. Buat file script bernama `script1.sh` menggunakan editor teks.
4. Isi file dengan kode berikut:

```bash
#!/bin/bash
echo "Halo, selamat datang di praktikum Sistem Operasi"
```

5. Simpan file tersebut.
6. Ubah hak akses file agar dapat dieksekusi:

```bash
chmod +x script1.sh
```

7. Jalankan script:

```bash
./script1.sh
```

8. Amati hasil yang ditampilkan pada layar.

### Percobaan 2: Menggunakan Variabel
1. Buat file script baru bernama `script2.sh`.
2. Isi file dengan kode berikut:

```bash
#!/bin/bash
nama="Mahasiswa"
matkul="Sistem Operasi"
echo "Nama: $nama"
echo "Mata kuliah: $matkul"
```

3. Simpan file, lalu ubah hak aksesnya:

```bash
chmod +x script2.sh
```

4. Jalankan script tersebut:

```bash
./script2.sh
```

5. Amati bagaimana nilai variabel ditampilkan.

### Percobaan 3: Input dari Pengguna
1. Buat file script bernama `script3.sh`.
2. Isi file dengan kode berikut:

```bash
#!/bin/bash
echo "Masukkan nama Anda:"
read nama
echo "Halo, $nama. Selamat belajar shell scripting."
```

3. Simpan file, ubah hak akses, lalu jalankan.
4. Masukkan nama ketika diminta.
5. Amati hasil keluaran script.

### Percobaan 4: Menggunakan Argumen Baris Perintah
1. Buat file script bernama `script4.sh`.
2. Isi file dengan kode berikut:

```bash
#!/bin/bash
echo "Argumen pertama: $1"
echo "Argumen kedua: $2"
```

3. Simpan file dan ubah hak aksesnya.
4. Jalankan script dengan dua argumen, misalnya:

```bash
./script4.sh Sistem Operasi
```

5. Amati hasil keluaran dan identifikasi isi dari `$1` dan `$2`.

### Percobaan 5: Percabangan Sederhana
1. Buat file script bernama `script5.sh`.
2. Isi file dengan kode berikut:

```bash
#!/bin/bash
echo "Masukkan nilai Anda:"
read nilai

if [ $nilai -ge 60 ]
then
    echo "Anda dinyatakan lulus"
else
    echo "Anda dinyatakan belum lulus"
fi
```

3. Simpan file, ubah hak akses, lalu jalankan.
4. Uji script dengan beberapa nilai yang berbeda.
5. Amati perubahan hasil keluaran.

### Percobaan 6: Perulangan Sederhana
1. Buat file script bernama `script6.sh`.
2. Isi file dengan kode berikut:

```bash
#!/bin/bash
for i in 1 2 3 4 5
do
    echo "Perulangan ke-$i"
done
```

3. Simpan file, ubah hak akses, lalu jalankan.
4. Amati hasil yang ditampilkan.

### Percobaan 7: Otomasi Tugas Sederhana
1. Buat file script bernama `backup_sederhana.sh`.
2. Isi file dengan kode berikut:

```bash
#!/bin/bash
mkdir -p backup_praktikum
cp *.sh backup_praktikum 2>/dev/null
echo "File script berhasil disalin ke folder backup_praktikum"
```

3. Simpan file, ubah hak akses, lalu jalankan.
4. Periksa apakah file-file script berhasil disalin ke folder `backup_praktikum`.
5. Jelaskan manfaat otomasi sederhana tersebut.

## F. Tugas Analisis
Jawablah pertanyaan berikut berdasarkan hasil praktikum:
1. Apa yang dimaksud dengan shell script?
2. Apa fungsi baris `#!/bin/bash` pada awal script?
3. Jelaskan perbedaan antara variabel dan argumen pada shell script.
4. Apa fungsi perintah `chmod +x`?
5. Mengapa shell scripting penting dalam lingkungan sistem operasi Linux?

## G. Tugas Praktikum Mandiri
Kerjakan tugas berikut secara mandiri:
1. Buat sebuah shell script bernama `biodata.sh`.
2. Script harus meminta input berupa nama, NIM, dan kelas.
3. Script kemudian menampilkan kembali biodata tersebut ke layar.
4. Buat shell script kedua bernama `hitung_file.sh`.
5. Script `hitung_file.sh` harus menampilkan jumlah file yang terdapat pada direktori aktif.
6. Dokumentasikan seluruh langkah, kode program, dan hasil eksekusinya.

## H. Tugas Akhir Praktikum
Sebagai penguatan pemahaman, kerjakan tugas berikut:
1. Praktikkan kembali seluruh materi pada modul ini di **environment Windows**.
2. Gunakan perangkat yang paling mendekati shell Linux, seperti **PowerShell**, **Git Bash**, atau **WSL** apabila tersedia.
3. Bandingkan secara singkat pengalaman penggunaan shell scripting di Linux dan Windows.
4. Susun **laporan praktikum** secara lengkap.
5. Isi laporan harus memuat:
   - identitas praktikan,
   - tujuan praktikum,
   - langkah kerja,
   - kode script,
   - **screenshot hasil praktikum**,
   - penjelasan setiap percobaan,
   - jawaban tugas analisis,
   - kesimpulan.

## I. Format Laporan
Laporan dikumpulkan secara individu dengan sistematika sebagai berikut:
1. Judul praktikum.
2. Nama dan NIM.
3. Tujuan praktikum.
4. Dasar teori singkat.
5. Langkah kerja.
6. Kode program atau script.
7. Hasil praktikum disertai screenshot.
8. Pembahasan atau analisis.
9. Jawaban tugas mandiri.
10. Hasil praktik ulang di Windows.
11. Kesimpulan.

## J.Kesimpulan
Melalui praktikum ini, mahasiswa memperoleh pemahaman dasar mengenai shell scripting sebagai sarana otomatisasi perintah dalam sistem operasi Linux. Keterampilan ini menjadi dasar penting untuk praktikum-praktikum berikutnya yang berkaitan dengan pengelolaan proses, file system, dan administrasi sistem.
