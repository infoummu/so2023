---
title: Praktikum 03 - Pipeline, Redirection, dan Manajemen Proses
author: Ikhwan N. Elyas
category: Halaman Materi
published: true
description: Mahasiswa mempelajari konsep pipeline, redirection input/output, serta manajemen proses di Linux, meliputi pengalihan standar input/output/error, penggunaan operator pipe untuk menghubungkan perintah, pengelolaan proses latar depan dan latar belakang, pengiriman sinyal, serta monitoring proses sistem sebagai implementasi konsep manajemen proses pada sistem operasi.
---

# Praktikum 3: Pipeline, Redirection, dan Manajemen Proses

## A. Tujuan Praktikum
Setelah mengikuti praktikum ini, mahasiswa diharapkan mampu:
1. Menjelaskan konsep standar input, output, dan error dalam sistem operasi Linux.
2. Menggunakan operator redirection (`>`, `>>`, `<`, `2>`, `&>`) untuk mengalihkan aliran data.
3. Menggunakan operator pipe (`|`) untuk menghubungkan dua atau lebih perintah.
4. Menjelaskan perbedaan proses latar depan (*foreground*) dan latar belakang (*background*).
5. Menjalankan, menghentikan, dan memantau proses menggunakan perintah sistem.
6. Mengirim sinyal ke proses menggunakan perintah `kill` dan `killall`.
7. Menjelaskan keterkaitan redirection, pipe, dan manajemen proses dalam konteks sistem operasi.

## B. Dasar Teori
Dalam sistem operasi Linux, setiap program yang dijalankan akan memiliki tiga saluran (*stream*) standar yang terhubung ke terminal:

- **stdin (0)** : standar input — secara default menerima masukan dari keyboard.
- **stdout (1)** : standar output — secara default menampilkan keluaran ke layar.
- **stderr (2)** : standar error — secara default menampilkan pesan kesalahan ke layar.

Ketiga saluran ini dapat dialihkan (*redirected*) ke file atau ke saluran lain menggunakan operator redirection. Konsep ini merupakan bagian penting dari filosofi Linux yang memungkinkan penggabungan perintah-perintah sederhana menjadi rangkaian pemrosesan yang kompleks.

Selain itu, sistem operasi mengelola setiap program yang berjalan sebagai sebuah **proses**. Setiap proses memiliki identitas unik berupa **PID** (*Process ID*), status, dan sumber daya yang dialokasikan oleh kernel. Linux menyediakan berbagai perintah untuk memantau dan mengelola proses, seperti:

- `ps` : menampilkan daftar proses aktif.
- `top` / `htop` : menampilkan proses secara real-time.
- `kill` : mengirim sinyal ke proses.
- `jobs`, `bg`, `fg` : mengelola job di shell.

Pemahaman tentang redirection dan manajemen proses sangat penting karena menunjukkan bagaimana sistem operasi menangani aliran data dan alokasi sumber daya antar program.

## C. Alat dan Bahan
1. Komputer atau laptop.
2. Sistem operasi Linux, seperti Ubuntu, Linux Mint, WSL, atau Linux pada mesin virtual.
3. Terminal Linux.
4. Editor teks seperti `nano`, `vim`, `gedit`, atau Visual Studio Code.

## D. Materi Praktikum
Pada praktikum ini, mahasiswa akan mempelajari:

- redirection output (`>`, `>>`),
- redirection input (`<`),
- redirection error (`2>`, `2>>`),
- redirection gabungan (`&>`, `2>&1`),
- operator pipe (`|`),
- perintah `tee` untuk menulis dan menampilkan,
- perintah `grep` untuk menyaring data,
- perintah `wc`, `sort`, `uniq` untuk pemrosesan teks,
- manajemen proses dengan `ps`, `top`, `kill`,
- job control dengan `jobs`, `bg`, `fg`,
- sinyal proses (`SIGTERM`, `SIGKILL`, `SIGSTOP`).

## E. Langkah Kerja Praktikum

### Percobaan 1: Redirection Output ke File
1. Buka terminal Linux.
2. Pindah ke direktori home Anda.
3. Gunakan redirection output untuk menyimpan hasil perintah ke dalam file:

   ```bash
   echo "Halo, ini praktikum Sistem Operasi" > output.txt
   ```

4. Tampilkan isi file untuk memverifikasi:

   ```bash
   cat output.txt
   ```

5. Gunakan redirection `>>` untuk menambahkan data tanpa menghapus isi sebelumnya:

   ```bash
   echo "Baris kedua ditambahkan dengan operator >>" >> output.txt
   ```

6. Tampilkan kembali isi file:

   ```bash
   cat output.txt
   ```

7. Bandingkan perilaku `>` yang menimpa isi file dengan `>>` yang menambahkan data.

### Percobaan 2: Redirection Input dari File
1. Buat file `data.txt` dengan tiga baris teks bebas menggunakan `echo` dengan redirection:

   ```bash
   echo "baris satu" > data.txt
   echo "baris dua" >> data.txt
   echo "baris tiga" >> data.txt
   ```

2. Gunakan redirection input untuk membaca file sebagai masukan perintah `wc`:

   ```bash
   wc -l < data.txt
   ```

3. Bandingkan hasilnya dengan cara biasa:

   ```bash
   wc -l data.txt
   ```

4. Perhatikan bahwa `wc -l < data.txt` hanya menampilkan jumlah baris, sedangkan `wc -l data.txt` juga menampilkan nama file. Jelaskan perbedaannya.

### Percobaan 3: Redirection Standar Error
1. Coba jalankan perintah yang akan menghasilkan error:

   ```bash
   ls /folder_tidak_ada
   ```

   Perhatikan pesan error yang muncul di layar.

2. Alihkan pesan error ke file menggunakan `2>`:

   ```bash
   ls /folder_tidak_ada 2> error.log
   ```

3. Tampilkan isi file `error.log`:

   ```bash
   cat error.log
   ```

4. Sekarang jalankan perintah yang berhasil dan gagal secara bersamaan, lalu alihkan stdout ke satu file dan stderr ke file lain:

   ```bash
   ls /home /folder_tidak_ada > sukses.txt 2> error.log
   ```

5. Periksa isi kedua file:

   ```bash
   cat sukses.txt
   cat error.log
   ```

6. Alihkan stdout dan stderr ke file yang sama menggunakan `&>`:

   ```bash
   ls /home /folder_tidak_ada &> semua.txt
   cat semua.txt
   ```

### Percobaan 4: Menghubungkan Perintah dengan Pipe (`|`)
1. Gunakan pipe untuk menggabungkan dua perintah:

   ```bash
   ls -l / | wc -l
   ```

   Perintah di atas menghitung jumlah baris dari keluaran `ls -l /`.

2. Gunakan pipe dengan `grep` untuk menyaring data:

   ```bash
   ls -l / | grep "bin"
   ```

3. Rangkaian pipe yang lebih panjang:

   ```bash
   ps aux | grep bash | wc -l
   ```

   Perintah di atas menghitung berapa banyak proses `bash` yang sedang berjalan.

4. Gunakan pipe bersama `sort` dan `uniq`:

   ```bash
   cat /etc/passwd | cut -d: -f7 | sort | uniq -c
   ```

   Perintah di atas menampilkan daftar shell yang digunakan oleh pengguna sistem beserta jumlahnya.

5. Gunakan `tee` untuk menulis ke file sekaligus menampilkan ke layar:

   ```bash
   ls -l | tee daftar_file.txt
   ```

6. Verifikasi isi file:

   ```bash
   cat daftar_file.txt
   ```

### Percobaan 5: Melihat Proses dengan `ps` dan `top`
1. Jalankan perintah `ps` untuk melihat proses-proses yang sedang berjalan di terminal Anda:

   ```bash
   ps
   ```

2. Lihat semua proses yang berjalan di sistem:

   ```bash
   ps aux
   ```

3. Gunakan pipe dan `grep` untuk mencari proses tertentu:

   ```bash
   ps aux | grep systemd
   ```

4. Jalankan `top` untuk melihat proses secara real-time (tekan `q` untuk keluar):

   ```bash
   top
   ```

5. Dari tampilan `top`, catat informasi berikut:
   - PID dari proses dengan penggunaan CPU tertinggi.
   - Persentase memori yang digunakan.
   - Waktu aktif sistem (*uptime*).

### Percobaan 6: Menjalankan Proses Latar Belakang (Background)
1. Jalankan perintah `sleep` di latar belakang dengan menambahkan simbol `&`:

   ```bash
   sleep 30 &
   ```

2. Lihat daftar job yang berjalan:

   ```bash
   jobs
   ```

3. Jalankan dua proses latar belakang sekaligus:

   ```bash
   sleep 20 &
   sleep 10 &
   ```

4. Tampilkan kembali daftar job:

   ```bash
   jobs
   ```

5. Jalankan perintah `yes > /dev/null &` di latar belakang (perintah ini akan terus berjalan sampai dihentikan):

   ```bash
   yes > /dev/null &
   ```

6. Catat PID yang muncul, lalu hentikan proses tersebut:

   ```bash
   kill <PID>
   ```

   Ganti `<PID>` dengan nomor PID yang tercatat.

### Percobaan 7: Mengelola Proses dengan `fg`, `bg`, dan `Ctrl+Z`
1. Jalankan perintah `sleep` di latar depan:

   ```bash
   sleep 30
   ```

2. Sebelum 30 detik berlalu, tekan **Ctrl+Z** untuk menghentikan sementara (*suspend*) proses.

3. Proses akan berhenti dan muncul pesan seperti `[1]+  Stopped`. Verifikasi dengan:

   ```bash
   jobs
   ```

4. Lanjutkan proses di latar belakang:

   ```bash
   bg %1
   ```

5. Verifikasi status job:

   ```bash
   jobs
   ```

6. Pindahkan kembali proses ke latar depan:

   ```bash
   fg %1
   ```

7. Biarkan proses selesai atau tekan **Ctrl+C** untuk menghentikannya.

### Percobaan 8: Mengirim Sinyal ke Proses dengan `kill`
1. Jalankan `yes > /dev/null &` sebanyak dua kali di latar belakang:

   ```bash
   yes > /dev/null &
   yes > /dev/null &
   ```

2. Catat PID dari kedua proses tersebut.

3. Kirim sinyal **SIGTERM** (sinyal 15 — permintaan berhenti secara wajar) ke salah satu proses:

   ```bash
   kill -15 <PID>
   ```

   atau cukup dengan:

   ```bash
   kill <PID>
   ```

   (secara default `kill` mengirimkan SIGTERM)

4. Verifikasi bahwa proses telah berhenti:

   ```bash
   ps aux | grep yes
   ```

5. Untuk proses yang tidak mau berhenti dengan SIGTERM, gunakan **SIGKILL** (sinyal 9):

   ```bash
   kill -9 <PID>
   ```

6. Gunakan `killall` untuk menghentikan semua proses dengan nama tertentu:

   ```bash
   killall yes
   ```

7. Verifikasi tidak ada lagi proses `yes` yang berjalan:

   ```bash
   ps aux | grep yes
   ```

### Percobaan 9: Membuat Shell Script untuk Monitoring Proses
1. Buat file script bernama `monitor_proses.sh` dengan isi sebagai berikut:

   ```bash
   #!/bin/bash
   echo "=== MONITOR PROSES SISTEM ==="
   echo "Waktu: $(date)"
   echo ""
   echo "1. 5 Proses dengan CPU Tertinggi:"
   ps aux --sort=-%cpu | head -6
   echo ""
   echo "2. 5 Proses dengan MEMORY Tertinggi:"
   ps aux --sort=-%mem | head -6
   echo ""
   echo "3. Total Proses Berjalan:"
   ps aux | wc -l
   echo ""
   echo "4. Pengguna yang Sedang Login:"
   who
   ```

2. Simpan file, ubah hak akses, lalu jalankan:

   ```bash
   chmod +x monitor_proses.sh
   ./monitor_proses.sh
   ```

3. Amati output yang dihasilkan. Simpan output ke dalam file laporan dengan redirection:

   ```bash
   ./monitor_proses.sh > hasil_monitor.txt
   cat hasil_monitor.txt
   ```

### Percobaan 10: Membuat Pipeline Data Sederhana
1. Buat file script bernama `pipeline_data.sh` yang mendemonstrasikan rangkaian pipe.

2. Isi file dengan kode berikut:

   ```bash
   #!/bin/bash
   echo "=== PIPELINE DATA SEDERHANA ==="
   echo ""
   echo "Menampilkan 5 file/direktori terbesar di home:"
   du -sh /home/* 2>/dev/null | sort -rh | head -5
   echo ""
   echo "Menampilkan jumlah file per ekstensi di direktori aktif:"
   ls -l 2>/dev/null | grep "^-" | awk -F. '{print $NF}' | sort | uniq -c | sort -rn
   echo ""
   echo "Menampilkan proses dengan penggunaan memori di atas 1%:"
   ps aux --sort=-%mem | awk '$4 > 1.0 {print $11, $4"%"}'
   ```

3. Simpan file, ubah hak akses, lalu jalankan:

   ```bash
   chmod +x pipeline_data.sh
   ./pipeline_data.sh
   ```

4. Amati bagaimana setiap pipe mengalirkan data dari satu perintah ke perintah berikutnya.

## F. Tugas Akhir Praktikum
Sebagai penguatan pemahaman, kerjakan tugas berikut:
1. Praktikkan kembali seluruh materi pada modul ini di **environment Windows**.
2. Gunakan perangkat yang paling mendekati shell Linux, seperti **PowerShell**, **Git Bash**, atau **WSL** apabila tersedia.
3. Bandingkan secara singkat cara melakukan redirection dan manajemen proses di Linux dan Windows.
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

### Format Laporan
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
12. Berikan nama File Laporannya: **Laporan_Tugas_Praktikum3_npm.pdf**
13. Upload Laporannya (File PDF) Sekalian Absen di **[https://t.me/MyAsdosElyasBot](https://t.me/MyAsdosElyasBot){:target="_blank"}** Asisten Dosen AI Untuk Mata Kuliah SO dan PAJ
14. Tugas dikumpul dan batas waktu kumpul: **16/06/2026 Jam 23:59 (Kamis Malam)**.


---
By: elyas@fedora.linux 
