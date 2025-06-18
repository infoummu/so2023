---
title: Pertemuan 04 - Penjadwalan Proses 
author: Ikhwan N. Elyas
category: Halaman Materi
published: true
description: Penjadwalan proses adalah mekanisme OS untuk menentukan proses mana yang akan dieksekusi. Tujuannya mengoptimalkan penggunaan CPU dan respon sistem. Algoritma penjadwalan beragam, dari batch (misalnya, shortest job first) hingga interaktif (misalnya, round robin). Faktor seperti prioritas, waktu tunggu, dan jenis proses (I/O-bound atau CPU-bound) mempengaruhi keputusan penjadwalan. 

---

### Penjadwalan Proses 

Penjadwalan proses adalah mekanisme OS untuk menentukan proses mana yang akan dieksekusi. Tujuannya mengoptimalkan penggunaan CPU dan respon sistem. Algoritma penjadwalan beragam, dari batch (misalnya, shortest job first) hingga interaktif (misalnya, round robin). Faktor seperti prioritas, waktu tunggu, dan jenis proses (I/O-bound atau CPU-bound) mempengaruhi keputusan penjadwalan. 

### Materi 

* **Silahkan Baca-baca Materi Berikut ini:** 
    - [Andrew_S.T._OS_02-Process-and-Threads.pdf](/so2023/reff/materi/andrew/Andrew_OS_02-Process-and-Threads.pdf){:target="_blank"}


---# 📘 Sistem Operasi: Proses dan Threads

## 📌 BAB 2: Processes and Threads

---

## 1. Konsep Dasar Proses
- **Proses** adalah *abstraksi program yang sedang berjalan*.
- Memungkinkan *pseudoparalelisme* meski hanya ada satu CPU.
- Setiap proses memiliki:
  - Program counter
  - Register
  - Variabel sendiri
- Memberi ilusi paralelisme melalui **multiprogramming**.

---

## 2. Model Proses
- Semua proses berjalan secara **sekuensial**.
- Konsep: tiap proses seolah-olah punya CPU sendiri.
- **Multiprogramming**: CPU bergantian menjalankan proses.

---

## 3. Pembuatan Proses

### Proses dapat dibuat melalui:
1. Inisialisasi sistem (boot).
2. System call dari proses lain (`fork()` di UNIX).
3. Aksi pengguna (klik ikon/aplikasi).
4. Proses batch (di sistem besar).

### Perbandingan:
- **UNIX**: `fork()` → `execve()`
- **Windows**: `CreateProcess()`

---

## 4. Penghentian Proses

### Proses berhenti karena:
1. Keluar normal (voluntary).
2. Error terdeteksi (voluntary).
3. Fatal error (involuntary).
4. Dibunuh oleh proses lain (involuntary).

---

## 5. Hierarki Proses
- **UNIX**: proses punya induk dan anak → bentuk **tree**.
- **Windows**: tidak ada struktur hierarki, semua proses setara.

---

## 6. State Proses

### Tiga state utama:
- **Running**: menggunakan CPU.
- **Ready**: siap dijalankan.
- **Blocked**: menunggu event eksternal.

### Transisi:
1. Running → Blocked
2. Running → Ready (karena preempted)
3. Ready → Running
4. Blocked → Ready (input tersedia)

---

## 7. Process Table
- Sistem menyimpan **Process Table / PCB**.
- Berisi informasi seperti:
  - Program counter
  - Register
  - Alokasi memori
  - File terbuka
  - Scheduling info

---

## 8. Model Multiprogramming

### Model Probabilistik:
- Misal: proses idle karena I/O sebesar `p`, jumlah proses `n`  
  \[
  \text{CPU Utilization} = 1 - p^n
  \]

### Contoh:
- Jika `p = 0.8` dan `n = 3` → CPU utilization = `1 - 0.8^3 ≈ 49%`

---

## 9. Threads (Benang Eksekusi)

### Definisi:
- Unit eksekusi dalam proses.
- Share:
  - Memori
  - File
  - Variable global
- Memiliki:
  - Stack sendiri
  - Program counter sendiri

---

## 10. Model Thread Klasik

### Per-thread:
- Program counter
- Register
- Stack
- State

### Per-proses:
- Address space
- File terbuka
- Signal
- Child processes

---

## 11. Penggunaan Thread (Contoh)

- **Word Processor**:
  - Thread 1: interaksi pengguna
  - Thread 2: format ulang dokumen
  - Thread 3: auto-save

- **Web Server**:
  - Dispatcher thread menerima request
  - Worker threads melayani request secara paralel

---

## 12. Implementasi Thread

### A. User-Level Threads
- Tidak diketahui oleh kernel
- Cepat dan ringan
- Tidak mendukung blocking system call dengan baik

### B. Kernel-Level Threads
- Dikelola oleh kernel
- Bisa blocking tanpa ganggu thread lain
- Lebih berat dari sisi performa

---

## 13. POSIX Threads (Pthreads)

### Fungsi penting:
- `pthread_create()` – membuat thread baru
- `pthread_exit()` – keluar dari thread
- `pthread_join()` – tunggu thread lain selesai
- `pthread_yield()` – menyerahkan CPU ke thread lain

---

## 14. Masalah dalam Multithreading

- **Race condition**: dua thread akses data bersamaan
- **Deadlock**: saling menunggu
- **Starvation**: thread tidak pernah dapat giliran CPU
- **Sinkronisasi** penting untuk mengelola akses ke data bersama

---



