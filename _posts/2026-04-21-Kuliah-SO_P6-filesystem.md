---
title: Pertemuan 06 - File System
author: Ikhwan N. Elyas
category: Halaman Materi
published: true
description: Sistem file adalah komponen OS yang mengelola penyimpanan dan pengambilan data di perangkat. Ini penting untuk kapasitas besar, persistensi data, dan akses bersama. Mengatur file, direktori, dan metadata, serta mendukung operasi dasar seperti membuat, membaca, menulis, dan menghapus, memastikan pengelolaan informasi yang efisien dan terstruktur.
---

## Ringkasan dan Penjelasan Bab File System pada Sistem Operasi

Berikut adalah ringkasan poin-poin penting dan penjelasan dari bab "File System pada Sistem Operasi":

### 1. Definisi dan Peran Utama File System:
*   **Definisi:** Sistem file adalah komponen sistem operasi yang bertanggung jawab untuk mengelola bagaimana data disimpan dan diambil dari perangkat penyimpanan (seperti hard drive, SSD, USB drive).
*   **Peran Utama:** Ini menyediakan cara terstruktur bagi pengguna dan aplikasi untuk menyimpan, mengatur, dan mengakses informasi. Tanpa sistem file, data akan menjadi blok-blok informasi yang tidak terorganisir.

### 2. Mengapa Sistem File Penting?

Sistem file mengatasi beberapa keterbatasan mendasar dari ruang alamat proses (memori utama):

*   **Kapasitas Penyimpanan yang Lebih Besar:**
    *   Ruang alamat proses memiliki batasan ukuran yang relatif kecil.
    *   Sistem file menyediakan kapasitas penyimpanan yang jauh lebih besar (gigabyte, terabyte, petabyte) yang diperlukan untuk aplikasi besar seperti database, sistem perbankan, atau arsip perusahaan.
*   **Persistensi Data:**
    *   Informasi yang disimpan dalam memori utama (ruang alamat proses) bersifat sementara dan akan hilang ketika proses berakhir atau sistem mati.
    *   Sistem file memastikan data tetap ada (persisten) untuk jangka waktu yang lama (berhari-hari, berbulan-bulan, bertahun-tahun) dan tidak hilang bahkan jika terjadi *crash* sistem atau pemadaman listrik.
*   **Akses Bersama (Sharing):**
    *   Seringkali, beberapa proses atau pengguna perlu mengakses informasi yang sama secara bersamaan.
    *   Sistem file memungkinkan informasi menjadi independen dari satu proses tertentu, sehingga dapat diakses dan dibagikan oleh banyak proses atau pengguna secara simultan, dengan mekanisme kontrol akses yang sesuai.

### 3. Konsep Dasar dalam Sistem File:

*   **File:** Unit dasar penyimpanan logis. File adalah kumpulan informasi terkait yang diperlakukan sebagai satu unit oleh sistem operasi.
*   **Direktori (Folder):** Struktur untuk mengorganisir file. Direktori dapat berisi file lain atau sub-direktori, membentuk hierarki.
*   **Metadata:** Informasi tentang file atau direktori, seperti nama, ukuran, tanggal pembuatan/modifikasi, pemilik, izin akses, dan lokasi fisik di disk.
*   **Blok Data:** Unit terkecil dari penyimpanan fisik di disk yang dialokasikan untuk file.
*   **Alokasi Disk:** Metode bagaimana ruang disk dialokasikan untuk file (misalnya, alokasi berurutan, berantai, atau terindeks).
*   **Manajemen Ruang Kosong:** Cara sistem file melacak blok-blok disk yang tersedia untuk digunakan.

### 4. Operasi File System:

Sistem file mendukung berbagai operasi, antara lain:

*   **Membuat File/Direktori:** Membuat entri baru di sistem file.
*   **Menulis ke File:** Menyimpan data ke dalam file.
*   **Membaca dari File:** Mengambil data dari file.
*   **Menghapus File/Direktori:** Menghapus entri dan membebaskan ruang disk.
*   **Memindahkan/Menyalin File:** Mengubah lokasi atau membuat duplikat file.
*   **Mengubah Atribut File:** Memodifikasi metadata seperti izin atau nama.

Secara keseluruhan, sistem file adalah fondasi penting dari setiap sistem operasi modern, memungkinkan pengelolaan data yang efisien, aman, dan persisten bagi pengguna dan aplikasi.
