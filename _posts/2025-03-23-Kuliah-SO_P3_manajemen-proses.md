---
title: Pertemuan 03 - Manajemen Proses 
author: Ikhwan N. Elyas
category: Halaman Materi
published: true
description: Manajemen proses adalah fungsi sistem operasi untuk mengelola eksekusi program (proses) dan thread. Ini meliputi pembuatan, penjadwalan, dan penghentian proses, serta mengatur statusnya (ready, running, blocked). Manajemen proses juga mencakup komunikasi antar proses (IPC) dan penanganan masalah seperti deadlock dan race condition untuk memastikan eksekusi yang efisien dan aman. 

---

### Manajemen Proses

Manajemen proses adalah salah satu fungsi utama sistem operasi yang bertanggung jawab untuk mengelola eksekusi program (proses) dan thread. Berikut penjelasan lengkap tentang **konsep proses dan thread** serta **status proses** beserta poin-poin yang berkaitan.

---

### 1. Konsep Proses dan Thread

#### A. Proses
- **Definisi**:  
  Proses adalah program yang sedang dieksekusi. Setiap proses memiliki ruang memori, sumber daya, dan status eksekusi sendiri.
- **Komponen Proses**:
  1. **Text Section**: Berisi kode program yang dieksekusi.
  2. **Data Section**: Menyimpan variabel global dan statis.
  3. **Heap**: Area memori untuk alokasi dinamis (misal: `malloc` di C).
  4. **Stack**: Digunakan untuk menyimpan data sementara seperti parameter fungsi, return address, dan variabel lokal.
- **Process Control Block (PCB)**:  
  Struktur data yang menyimpan informasi tentang proses, seperti:
  - Process ID (PID).
  - Program Counter (PC).
  - Status register CPU.
  - Status proses (ready, running, blocked).
  - Informasi memori dan I/O.

#### B. Thread
- **Definisi**:  
  Thread adalah unit eksekusi yang lebih kecil dari proses. Sebuah proses dapat memiliki banyak thread yang berbagi ruang memori dan sumber daya.
- **Perbedaan Proses dan Thread**:

    | **Aspek**          | **Proses**                          | **Thread**                        |
    |---------------------|-------------------------------------|-----------------------------------|
    | **Memori**          | Memiliki ruang memori sendiri.      | Berbagi memori dengan proses induk.|
    | **Overhead**        | Lebih berat (butuh lebih banyak sumber daya). | Lebih ringan.                   |
    | **Komunikasi**      | Komunikasi lebih lambat (IPC).      | Komunikasi lebih cepat (shared memory). |
    | **Contoh**          | Membuka browser baru.              | Tab baru dalam browser yang sama. |

- **Jenis Thread**:
  1. **User-level Thread**: Dikelola oleh library pengguna (contoh: POSIX threads).
  2. **Kernel-level Thread**: Dikelola langsung oleh sistem operasi.

---

### 2. Status Proses

Proses memiliki beberapa status selama siklus hidupnya. Berikut penjelasan lengkapnya:

#### A. Status Utama Proses
1. **New**:
   - Proses baru saja dibuat.
   - Sistem operasi mengalokasikan PCB dan sumber daya awal.
2. **Ready**:
   - Proses siap dieksekusi, menunggu alokasi CPU.
   - Proses berada dalam antrian penjadwalan (ready queue).
3. **Running**:
   - Proses sedang dieksekusi oleh CPU.
   - Hanya satu proses yang dapat berstatus running per CPU pada satu waktu.
4. **Waiting/Blocked**:
   - Proses menunggu suatu event, seperti penyelesaian I/O atau sinyal dari proses lain.
   - Proses tidak dapat melanjutkan eksekusi sampai event terjadi.
5. **Terminated**:
   - Proses selesai dieksekusi atau dihentikan secara paksa.
   - Sumber daya proses dibebaskan, dan PCB dihapus.

#### B. Diagram Transisi Status
- **New → Ready**: Proses diinisialisasi dan dimasukkan ke antrian ready.
- **Ready → Running**: Penjadwal CPU memilih proses untuk dieksekusi.
- **Running → Waiting**: Proses meminta operasi I/O atau menunggu event.
- **Waiting → Ready**: Event yang ditunggu selesai, proses siap dieksekusi kembali.
- **Running → Terminated**: Proses selesai atau dihentikan.

---

### 3. Poin-Poin Berkaitan dengan Manajemen Proses

#### A. Penjadwalan Proses
- **Tujuan**: Mengalokasikan CPU secara efisien ke proses yang siap dieksekusi.
- **Algoritma Penjadwalan**:
  1. **First-Come, First-Served (FCFS)**: Proses dilayani berdasarkan urutan kedatangan.
  2. **Shortest Job First (SJF)**: Proses dengan waktu eksekusi terpendek diprioritaskan.
  3. **Round Robin (RR)**: Setiap proses diberi waktu CPU (time quantum) secara bergiliran.
  4. **Priority Scheduling**: Proses dengan prioritas tertinggi dieksekusi terlebih dahulu.

#### B. Operasi pada Proses
- **Pembuatan Proses**:
  - Sistem call: `fork()` (Unix/Linux) atau `CreateProcess()` (Windows).
  - Proses induk (parent) dapat membuat proses anak (child).
- **Penghentian Proses**:
  - Sistem call: `exit()` (Unix/Linux) atau `TerminateProcess()` (Windows).

#### C. Komunikasi Antar Proses (IPC)
- **Shared Memory**: Proses berbagi area memori yang sama.
- **Message Passing**: Proses mengirim pesan melalui sistem operasi (contoh: pipes, sockets).

#### D. Masalah dalam Manajemen Proses
1. **Deadlock**:
   - Situasi di mana dua atau lebih proses saling menunggu sumber daya yang tidak akan pernah dilepaskan.
   - Solusi: Deteksi, pencegahan, atau penghindaran deadlock.
2. **Starvation**:
   - Proses tidak pernah mendapatkan sumber daya yang dibutuhkan karena prioritas rendah.
   - Solusi: Penjadwalan yang adil (fair scheduling).
3. **Race Condition**:
   - Ketika dua proses mengakses data bersama secara bersamaan, menyebabkan hasil yang tidak konsisten.
   - Solusi: Sinkronisasi menggunakan semaphore atau mutex.

---

### Ringkasan
- **Proses** adalah program yang sedang dieksekusi, sedangkan **thread** adalah unit eksekusi yang lebih kecil dalam proses.
- **Status proses** meliputi new, ready, running, waiting, dan terminated.
- Manajemen proses mencakup penjadwalan, operasi pada proses, komunikasi antar proses, dan penanganan masalah seperti deadlock dan race condition.

Dengan memahami manajemen proses, kita dapat mengoptimalkan kinerja sistem operasi dan memastikan eksekusi program yang efisien dan aman.