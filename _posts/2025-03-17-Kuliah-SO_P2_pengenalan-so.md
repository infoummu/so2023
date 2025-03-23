---
title: Pertemuan 02 - Pengenalan Sistem Operasi 
author: Ikhwan N. Elyas
category: Halaman Materi
published: true
description: Sistem operasi adalah perangkat lunak yang mengelola sumber daya komputer dan menjadi perantara pengguna dengan perangkat keras, seperti Windows dan Linux. Fungsinya meliputi pengelolaan proses, memori, dan antarmuka pengguna, dengan tujuan meningkatkan efisiensi dan kemudahan. Tugas utamanya menjalankan aplikasi dan mengatur data, berbasis konsep multitasking dan virtualisasi, menargetkan kinerja optimal. Sejarahnya berkembang dari batch processing hingga era modern GUI.
---

## РОКОК PEMBAHASAN

1. DEFINISI SISTEM OPERASI  
2. FUNGSI SISTEM OPERASI  
3. TUJUAN SISTEM OPERASI  
4. TUGAS UTAMA SISTEM OPERASI  
5. KONSEP UTAMA SISTEM OPERASI  
6. SASARAN SISTEM OPERASI  
7. ARSITEKUR SISTEM OPERASI 
8. SEJARAH PERKEMBANGAN SISTEM OPERASI  

--------

1. **DEFINISI SISTEM OPERASI**  
   - Pengertian sistem operasi sebagai perangkat lunak pengelola sumber daya komputer.  
   - Peran sebagai perantara antara pengguna dan perangkat keras.  
   - Contoh sistem operasi (Windows, Linux, macOS).  

2. **FUNGSI SISTEM OPERASI**  
   - Mengelola proses (process management).  
   - Mengatur memori (memory management).  
   - Mengendalikan perangkat keras (device management).  
   - Menyediakan antarmuka pengguna (user interface).  

3. **TUJUAN SISTEM OPERASI**  
   - Meningkatkan efisiensi penggunaan sumber daya komputer.  
   - Memberikan kemudahan bagi pengguna.  
   - Memastikan stabilitas dan keamanan sistem.  

4. **TUGAS UTAMA SISTEM OPERASI**  
   - Menjalankan dan mengelola program aplikasi.  
   - Mengatur penyimpanan data (file management).  
   - Menangani input dan output perangkat.  
   - Mendeteksi dan menangani kesalahan (error handling).  

5. **KONSEP UTAMA SISTEM OPERASI**  
   - Multitasking: menjalankan beberapa tugas sekaligus.  
   - Multiprocessing: penggunaan lebih dari satu prosesor.  
   - Virtualisasi: simulasi sumber daya fisik.  
   - Scheduling: pengaturan prioritas tugas.  

6. **SASARAN SISTEM OPERASI**  
   - Optimalisasi kinerja sistem.  
   - Kompatibilitas dengan berbagai perangkat keras dan lunak.  
   - Kemudahan adaptasi untuk kebutuhan pengguna.  

6. **ARSITEKTUR SISTEM OPERASI**
   - Kernel: Inti sistem operasi yang mengendalikan proses, memori, dan perangkat keras.
   - Lapisan (Layers): Struktur berlapis seperti shell, API, dan kernel untuk modularitas.
   - Jenis Arsitektur: Monolitik (satu blok besar), mikrokernel (fungsi minimal di kernel), atau hibrida.
   - Interaksi Komponen: Bagaimana modul seperti file system, driver, dan scheduler bekerja sama.
   - Mode Operasi: Pembagian antara mode pengguna (user mode) dan mode kernel (kernel mode).



7. **SEJARAH PERKEMBANGAN SISTEM OPERASI**  
   - Awal mula: sistem batch processing (1950-an).  
   - Perkembangan: time-sharing dan multitasking (1960-1970-an).  
   - Era modern: GUI dan sistem operasi berbasis mobile (1980-an hingga kini).  
   - Contoh evolusi: dari UNIX ke Android/Windows.

---

1. **Pengertian Sistem Operasi** sebagai Perangkat Lunak Pengelola Sumber Daya Komputer
   Sistem operasi (OS) adalah perangkat lunak yang bertugas mengelola sumber daya komputer seperti prosesor, memori, disk, dan perangkat input/output (I/O). 
   - Sistem operasi memastikan bahwa sumber daya ini digunakan secara efisien dan adil oleh berbagai program yang berjalan di komputer. Misalnya, sistem operasi mengatur bagaimana CPU digunakan oleh berbagai proses, bagaimana memori dialokasikan, dan bagaimana data disimpan dan diakses dari disk. 
   - Sistem operasi juga bertanggung jawab untuk mengelola antarmuka antara perangkat keras dan perangkat lunak aplikasi, sehingga program aplikasi tidak perlu berurusan langsung dengan kompleksitas perangkat keras.

   **Sistem Operasi Memiliki Dua Fungsi Utama:**
   - **Sebagai Mesin yang Diperluas (Extended Machine):** Sistem operasi menyediakan abstraksi yang lebih sederhana dan bersih untuk berinteraksi dengan perangkat keras yang kompleks. Misalnya, alih-alih programmer harus berurusan langsung dengan perintah-perintah tingkat rendah untuk mengakses disk, sistem operasi menyediakan antarmuka file yang lebih mudah digunakan.

   - **Sebagai Manajer Sumber Daya (Resource Manager):** Sistem operasi mengelola sumber daya komputer secara efisien, memastikan bahwa setiap program mendapatkan akses yang adil ke sumber daya yang tersedia, dan mencegah konflik antara program yang berbeda.

2. **Peran sebagai Perantara antara Pengguna dan Perangkat Keras**
   - **Sistem operasi berperan sebagai perantara** antara pengguna (atau program aplikasi) dan perangkat keras komputer. 
   - Tanpa sistem operasi, pengguna atau programmer aplikasi harus berurusan langsung dengan perangkat keras, yang sangat kompleks dan rumit. 
   - Sistem operasi menyediakan lapisan abstraksi yang memungkinkan pengguna dan program aplikasi untuk berinteraksi dengan perangkat keras tanpa perlu memahami detail teknisnya.

   * Sebagai contoh, ketika pengguna ingin menyimpan file ke disk, sistem operasi akan menangani semua detail teknis seperti menulis data ke lokasi tertentu di disk, mengelola struktur file, dan memastikan bahwa data disimpan dengan aman. Pengguna hanya perlu menggunakan perintah sederhana seperti "save" dalam aplikasi, dan sistem operasi akan menangani sisanya.

   * Dalam dokumen tersebut, dijelaskan bahwa sistem operasi menyediakan antarmuka yang bersih dan konsisten untuk berinteraksi dengan perangkat keras, sehingga pengguna dan programmer tidak perlu khawatir tentang detail teknis seperti bagaimana data disimpan di disk atau bagaimana memori dialokasikan.

3. **Contoh Sistem Operasi** (Windows, Linux, macOS)
   Dokumen tersebut menyebutkan beberapa contoh sistem operasi yang populer, di antaranya:

   **Windows:** Sistem operasi yang dikembangkan oleh Microsoft. Windows adalah sistem operasi yang paling banyak digunakan di komputer pribadi (PC). Versi terbaru yang disebutkan dalam dokumen adalah Windows 8. Windows menyediakan antarmuka pengguna grafis (GUI) yang mudah digunakan dan mendukung berbagai aplikasi.

   **Linux:** Sistem operasi open-source yang didasarkan pada kernel Linux. Linux sangat populer di kalangan pengembang dan digunakan di berbagai lingkungan, mulai dari server hingga perangkat embedded. Linux juga mendukung berbagai distribusi (distro) seperti Ubuntu, Fedora, dan Debian.

   **macOS:** Sistem operasi yang dikembangkan oleh Apple untuk komputer Macintosh. macOS adalah sistem operasi berbasis UNIX yang dikenal karena stabilitas dan keamanannya. macOS menyediakan antarmuka pengguna yang elegan dan terintegrasi dengan baik dengan produk-produk Apple lainnya.

   Selain itu, dokumen juga menyebutkan sistem operasi lain seperti **UNIX, FreeBSD,** dan **Android,** yang merupakan sistem operasi populer untuk berbagai jenis perangkat, mulai dari server hingga perangkat mobile.

4. **Kesimpulan**
   Sistem operasi adalah perangkat lunak yang mengelola sumber daya komputer dan bertindak sebagai perantara antara pengguna/perangkat lunak aplikasi dan perangkat keras. Contoh sistem operasi yang populer termasuk Windows, Linux, dan macOS, yang masing-masing memiliki karakteristik dan penggunaan yang berbeda.

---
### **5. Konsep Utama Sistem Operasi**

   Konsep utama yang mendasari sistem operasi meliputi:
   - **Multitasking:** Kemampuan menjalankan beberapa tugas sekaligus, seperti membuka browser dan editor teks bersamaan.

   - **Multiprocessing:** Pemanfaatan lebih dari satu prosesor untuk meningkatkan kinerja, sering digunakan di server.

   - **Virtualisasi:** Simulasi sumber daya fisik, seperti membuat mesin virtual untuk menjalankan sistem operasi lain.

   - **Scheduling:** Pengaturan prioritas tugas, memastikan proses penting mendapatkan akses CPU lebih dulu.

---

### **7. Arsitektur Sistem Opersi** 


#### Kernel  
   - **Penjelasan:** Kernel adalah inti dari sistem operasi yang mengelola sumber daya perangkat keras seperti CPU, memori, dan perangkat I/O. 
   Kernel adalah komponen inti dari sistem operasi yang bertanggung jawab atas pengelolaan sumber daya perangkat keras seperti CPU, memori, dan perangkat I/O. Ia menjalankan fungsi esensial seperti penjadwalan proses, alokasi memori, dan komunikasi dengan perangkat keras melalui driver. Kernel beroperasi pada tingkat privilige tertinggi, memastikan kontrol penuh atas sistem, dan menjadi dasar bagi semua layanan sistem operasi. 

   - **Fungsi:** Menangani penjadwalan proses, alokasi memori, dan komunikasi dengan perangkat keras melalui driver.  

   - **Karakteristik:** Berjalan pada mode privilige tertinggi (kernel mode), memberikan kontrol penuh atas sistem dan menjadi fondasi bagi semua layanan sistem operasi.

#### User Mode  
   - **Penjelasan:** Mode pengguna adalah lingkungan tempat aplikasi pengguna berjalan dengan akses terbatas ke perangkat keras.  

   - **Fungsi:** Melindungi sistem dari kerusakan akibat kesalahan aplikasi, hanya mengizinkan operasi melalui panggilan sistem yang aman.  

   - **Karakteristik:** Tidak memiliki akses langsung ke perangkat keras atau memori sistem; bergantung pada kernel untuk tugas tingkat rendah seperti membaca file atau mencetak.

#### System Call  
   - **Penjelasan:** System call adalah mekanisme yang digunakan aplikasi di user mode untuk meminta layanan dari kernel.  

   - **Fungsi:** Menjembatani user mode dan kernel mode, misalnya untuk membuka file, mengalokasikan memori, atau mengirim data ke jaringan.  

   - **Karakteristik:** Melibatkan perpindahan dari user mode ke kernel mode (context switching), memastikan keamanan dan kontrol dengan memungkinkan kernel memvalidasi setiap permintaan.


#### Lapisan (Layers)
   Arsitektur berlapis membagi sistem operasi menjadi beberapa tingkatan, seperti lapisan kernel (terendah), lapisan layanan sistem (file system, jaringan), dan lapisan antarmuka pengguna (shell atau GUI). Setiap lapisan hanya berkomunikasi dengan lapisan di atas atau di bawahnya, meningkatkan modularitas dan memudahkan pengelolaan, meskipun bisa menambah overhead karena banyaknya panggilan antar lapisan.

#### Jenis Arsitektur
   Ada beberapa jenis arsitektur sistem operasi:  
   - **Monolitik:** Semua fungsi (proses, file, driver) ada dalam satu kernel besar, cepat karena minim komunikasi antar modul, tapi kurang stabil jika ada kegagalan. Contoh: Linux awal.  

   - **Mikrokernel:** Hanya fungsi inti (penjadwalan, komunikasi) di kernel, sisanya di ruang pengguna, lebih stabil tapi lambat karena overhead pesan. Contoh: Minix.  

   - **Hibrida:** Gabungan monolitik dan mikrokernel untuk keseimbangan kinerja dan stabilitas. Contoh: Windows NT, macOS.

####  Interaksi Komponen
   Ini mengacu pada bagaimana modul seperti sistem file (file system), pengelola memori, driver perangkat, dan penjadwal proses (scheduler) saling berinteraksi. Misalnya, saat pengguna menyimpan file, kernel memanggil driver disk, mengalokasikan memori, dan memperbarui sistem file. Interaksi ini bisa langsung (di monolitik) atau melalui pesan (di mikrokernel), memengaruhi efisiensi dan keandalan sistem.

#### Mode Operasi
   Sistem operasi bekerja dalam dua mode:  
   - **Mode Pengguna (User Mode):** Tempat aplikasi berjalan dengan akses terbatas ke perangkat keras untuk mencegah kerusakan sistem. Instruksi dijalankan melalui panggilan sistem (system call) ke kernel.  

   - **Mode Kernel (Kernel Mode):** Kernel beroperasi dengan akses penuh ke perangkat keras, menangani tugas kritis seperti manajemen interrupt dan I/O. Pergantian mode ini (context switching) memastikan keamanan dan stabilitas sistem.



