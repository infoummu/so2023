---
title: Praktikum 04 - File Permission, User Management, dan Filesystem
author: Ikhwan N. Elyas
category: Halaman Materi
published: true
description: Mahasiswa mempelajari sistem izin file (permission) di Linux, manajemen pengguna dan grup, pengelolaan kepemilikan file, serta pemahaman dasar filesystem, partisi, dan penggunaan ruang disk sebagai implementasi konsep manajemen file dan proteksi pada sistem operasi.
---

# Praktikum 4: File Permission, User Management, dan Filesystem

## A. Tujuan Praktikum
Setelah mengikuti praktikum ini, mahasiswa diharapkan mampu:
1. Menjelaskan konsep izin file (*file permission*) di Linux dan makna setiap bit izin.
2. Mengubah izin file dan direktori menggunakan perintah `chmod` (mode numerik dan simbolik).
3. Mengubah kepemilikan file menggunakan perintah `chown` dan `chgrp`.
4. Menjelaskan konsep pengguna (*user*) dan grup (*group*) dalam sistem operasi Linux.
5. Membuat dan mengelola pengguna serta grup menggunakan perintah sistem.
6. Memahami struktur filesystem Linux serta memantau penggunaan ruang disk.
7. Mengintegrasikan pipeline, redirection, dan shell script untuk analisis filesystem.

## B. Dasar Teori

### File Permission (Izin File)
Setiap file dan direktori di Linux memiliki tiga kategori izin yang diterapkan pada tiga entitas:

| Kategori | Entitas | Penjelasan |
|-----------|---------|-------------|
| **u** (*user*) | Pemilik file | Pengguna yang memiliki file tersebut |
| **g** (*group*) | Grup | Anggota grup yang terasosiasi dengan file |
| **o** (*others*) | Lainnya | Semua pengguna lain di sistem |

Setiap kategori memiliki tiga jenis izin:

| Izin | Simbol | Numerik | Penjelasan |
|------|--------|---------|------------|
| **r** (*read*) | `r` | 4 | Membaca isi file / membaca isi direktori |
| **w** (*write*) | `w` | 2 | Menulis/mengubah file / membuat/menghapus file di direktori |
| **x** (*execute*) | `x` | 1 | Mengeksekusi file / masuk ke direktori |

Izin direpresentasikan sebagai 10 karakter, misalnya `-rwxr-xr--`:
- Karakter ke-1: tipe file (`-` file biasa, `d` direktori, `l` symlink)
- Karakter ke-2-4: izin untuk pemilik (user)
- Karakter ke-5-7: izin untuk grup
- Karakter ke-8-10: izin untuk lainnya (others)

Nilai numerik merupakan penjumlahan dari nilai setiap izin. Contoh: `rwx` = 4+2+1 = 7, `r-x` = 4+0+1 = 5, `r--` = 4+0+0 = 4.

### User dan Group
Linux adalah sistem *multi-user*, di mana banyak pengguna dapat menggunakan sistem secara bersamaan. Setiap pengguna memiliki:
- **Username** : nama login pengguna.
- **UID** (*User ID*) : identitas numerik unik.
- **GID** (*Group ID*) : identitas grup utama.
- **Home directory** : direktori pribadi pengguna.
- **Shell default** : program shell yang digunakan saat login.

Grup digunakan untuk mengelompokkan pengguna dengan keperluan akses yang sama. Informasi pengguna disimpan di `/etc/passwd`, hash password di `/etc/shadow`, dan informasi grup di `/etc/group`.

### Filesystem Linux
Filesystem Linux mengatur bagaimana data disimpan dan diorganisir di media penyimpanan. Struktur direktori dimulai dari root (`/`) yang merupakan akar dari seluruh hirarki. Beberapa konsep penting:

- **Mount** : proses menghubungkan partisi atau perangkat penyimpanan ke dalam satu hirarki direktori.
- **Partisi** : pembagian fisik atau logis dari media penyimpanan.
- **Inode** : struktur data yang menyimpan metadata file (kecuali nama file).
- **Superblock** : menyimpan informasi metadata filesystem secara keseluruhan.

Untuk memantau penggunaan disk, Linux menyediakan perintah `df` (*disk free*) dan `du` (*disk usage*).

## C. Alat dan Bahan
1. Komputer atau laptop.
2. Sistem operasi Linux, seperti Ubuntu, Linux Mint, WSL, atau Linux pada mesin virtual.
3. Terminal Linux.
4. Editor teks seperti `nano`, `vim`, `gedit`, atau Visual Studio Code.
5. Hak akses *superuser* (`sudo`) untuk percobaan manajemen pengguna.

## D. Materi Praktikum
Pada praktikum ini, mahasiswa akan mempelajari:

- struktur dan representasi izin file (`rwx`),
- mode numerik dan simbolik `chmod`,
- perubahan kepemilikan dengan `chown` dan `chgrp`,
- sticky bit, setuid, setgid,
- manajemen pengguna dengan `useradd`, `usermod`, `userdel`, `passwd`,
- manajemen grup dengan `groupadd`, `groupmod`, `groupdel`,
- informasi akun di `/etc/passwd`, `/etc/shadow`, `/etc/group`,
- perintah `id`, `who`, `whoami`, `su`,
- filesystem: `df`, `du`, `mount`, `lsblk`,
- integrasi dengan pipeline, grep, awk, dan shell script.

## E. Langkah Kerja Praktikum

### Percobaan 1: Melihat dan Memahami Izin File

1. Buka terminal Linux dan pindah ke direktori home.

2. Buat sebuah file kosong dan sebuah direktori untuk percobaan:

   ```bash
   touch percobaan.txt
   mkdir percobaan_dir
   ```

3. Lihat detail izin kedua objek tersebut:

   ```bash
   ls -l
   ```

   Perhatikan keluaran seperti `-rw-rw-r--` atau `-rw-r--r--`. Amati perbedaan izin antara file dan direktori (diawali dengan `-` untuk file, `d` untuk direktori).

4. Lihat izin secara lebih detail pada satu file:

   ```bash
   stat percobaan.txt
   ```

   Perhatikan informasi *Access*, *Change*, dan *Modify* timestamps serta mode izin dalam bentuk oktal.

5. Amati izin dari beberapa file sistem:

   ```bash
   ls -l /bin /etc/passwd /etc/shadow
   ```

6. Gunakan pipeline untuk menyaring file berdasarkan izin tertentu. Misalnya, cari file yang dapat dieksekusi di direktori `/bin`:

   ```bash
   ls -l /bin | head -20
   ```

7. Gunakan `ls -la` untuk melihat file tersembunyi beserta izinnya:

   ```bash
   ls -la ~
   ```

   Catat perbedaan izin pada file konfigurasi tersembunyi (diawali titik).

### Percobaan 2: Mengubah Izin File dengan `chmod` — Mode Numerik

Mode numerik menggunakan angka oktal 3 digit: digit pertama untuk *user*, kedua untuk *group*, ketiga untuk *others*.

1. Buat file baru untuk percobaan:

   ```bash
   echo "File untuk percobaan chmod numerik" > izin_file.txt
   ls -l izin_file.txt
   ```

2. Setel izin menjadi `rwxr-xr--` (754):

   ```bash
   chmod 754 izin_file.txt
   ls -l izin_file.txt
   ```

   Arti 754: user=7 (rwx), group=5 (r-x), others=4 (r--).

3. Setel izin menjadi hanya *read* untuk semua (`r--r--r--` = 444):

   ```bash
   chmod 444 izin_file.txt
   ls -l izin_file.txt
   ```

4. Coba baca file (seharusnya berhasil):

   ```bash
   cat izin_file.txt
   ```

5. Coba tulis ke file (seharusnya gagal karena izin tulis tidak ada):

   ```bash
   echo "tulisan baru" >> izin_file.txt
   ```

   Amati pesan error yang muncul.

6. Kembalikan izin agar dapat ditulis:

   ```bash
   chmod 644 izin_file.txt
   ls -l izin_file.txt
   ```

7. Setel izin *full access* hanya untuk pemilik (700):

   ```bash
   chmod 700 izin_file.txt
   ls -l izin_file.txt
   ```

8. Buat direktori dengan izin tertentu:

   ```bash
   mkdir izin_dir
   chmod 755 izin_dir
   ls -ld izin_dir
   ```

### Percobaan 3: Mengubah Izin File dengan `chmod` — Mode Simbolik

Mode simbolik menggunakan notasi `u` (user), `g` (group), `o` (others), `a` (all), operator `+` (tambah), `-` (kurang), `=` (setel).

1. Buat file baru:

   ```bash
   echo "Mode simbolik chmod" > simbolik.txt
   chmod 644 simbolik.txt
   ls -l simbolik.txt
   ```

2. Tambahkan izin *execute* untuk pemilik:

   ```bash
   chmod u+x simbolik.txt
   ls -l simbolik.txt
   ```

3. Hapus izin *read* untuk grup dan lainnya:

   ```bash
   chmod go-r simbolik.txt
   ls -l simbolik.txt
   ```

4. Berikan izin *read* dan *execute* untuk grup:

   ```bash
   chmod g+rx simbolik.txt
   ls -l simbolik.txt
   ```

5. Setel izin *read* dan *write* untuk semua pengguna:

   ```bash
   chmod a=rw simbolik.txt
   ls -l simbolik.txt
   ```

6. Kombinasikan beberapa perubahan dalam satu perintah:

   ```bash
   chmod u=rwx,g=rx,o=r simbolik.txt
   ls -l simbolik.txt
   ```

7. Gunakan redirection untuk menyimpan perbandingan izin sebelum dan sesudah:

   ```bash
   echo "Sebelum:" > perbandingan_izin.txt
   ls -l simbolik.txt >> perbandingan_izin.txt
   chmod a=r simbolik.txt
   echo "Sesudah:" >> perbandingan_izin.txt
   ls -l simbolik.txt >> perbandingan_izin.txt
   cat perbandingan_izin.txt
   ```

### Percobaan 4: Izin Khusus — Sticky Bit, SetUID, SetGID

1. **Sticky Bit** — mencegah pengguna lain menghapus file milik orang lain di direktori bersama. Direktori `/tmp` adalah contoh direktori dengan sticky bit:

   ```bash
   ls -ld /tmp
   ```

   Perhatikan huruf `t` pada akhir izin (`drwxrwxrwt`).

2. Setel sticky bit pada direktori percobaan:

   ```bash
   mkdir direktori_bersama
   chmod 1777 direktori_bersama
   ls -ld direktori_bersama
   ```

   Nilai 1 di awal (1777) menunjukkan sticky bit.

3. Gunakan mode simbolik untuk sticky bit:

   ```bash
   mkdir direktori_bersama2
   chmod a=rwx direktori_bersama2
   chmod +t direktori_bersama2
   ls -ld direktori_bersama2
   ```

4. Amati efek sticky bit dengan membuat dua file di dalamnya (sebagai pengguna yang sama):

   ```bash
   touch direktori_bersama/file_a.txt
   touch direktori_bersama/file_b.txt
   ls -l direktori_bersama
   ```

   (Efek sticky bit akan jelas terlihat jika ada lebih dari satu pengguna.)

5. **SetUID (SUID)** — program berjalan dengan hak pemilik file, bukan pengguna yang menjalankannya. Contoh:

   ```bash
   ls -l /usr/bin/passwd
   ```

   Perhatikan huruf `s` pada posisi izin *execute* user (`-rwsr-xr-x`).

6. Amati program lain yang memiliki SUID:

   ```bash
   find /usr/bin -perm -4000 2>/dev/null | head -10
   ```

7. Gunakan pipeline untuk menghitung jumlah file SUID di sistem:

   ```bash
   find / -perm -4000 2>/dev/null | wc -l
   ```

8. **SetGID (SGID)** — pada file: berjalan dengan hak grup pemilik. Pada direktori: file baru mewarisi grup direktori:

   ```bash
   ls -l /usr/bin/wall
   ```

   Perhatikan huruf `s` pada posisi izin *execute* grup.

### Percobaan 5: Mengubah Kepemilikan File dengan `chown` dan `chgrp`

1. Lihat kepemilikan file yang sudah dibuat sebelumnya:

   ```bash
   ls -l percobaan.txt izin_file.txt
   ```

   Perhatikan kolom *owner* (nama pengguna) dan *group*.

2. Buat grup baru untuk percobaan (mungkin perlu `sudo`):

   ```bash
   sudo groupadd praktikan
   ```

   Jika diminta password, masukkan password *superuser*.

3. Ubah grup kepemilikan file dengan `chgrp`:

   ```bash
   sudo chgrp praktikan percobaan.txt
   ls -l percobaan.txt
   ```

4. Kembalikan grup ke grup default pengguna:

   ```bash
   sudo chgrp $(id -gn) percobaan.txt
   ls -l percobaan.txt
   ```

5. Ubah pemilik dan grup sekaligus dengan `chown`:

   ```bash
   sudo chown root:root percobaan.txt
   ls -l percobaan.txt
   ```

6. Kembalikan kepemilikan ke pengguna Anda:

   ```bash
   sudo chown $(whoami):$(id -gn) percobaan.txt
   ls -l percobaan.txt
   ```

7. `chown` juga dapat digunakan hanya untuk mengubah pemilik:

   ```bash
   sudo chown root izin_file.txt
   ls -l izin_file.txt
   sudo chown $(whoami) izin_file.txt
   ls -l izin_file.txt
   ```

8. Gunakan opsi `-R` (rekursif) untuk mengubah kepemilikan seluruh direktori:

   ```bash
   chmod 755 percobaan_dir
   sudo chown -R root:root percobaan_dir
   ls -l percobaan_dir
   sudo chown -R $(whoami):$(id -gn) percobaan_dir
   ls -l percobaan_dir
   ```

### Percobaan 6: Informasi Pengguna dan Grup

1. Lihat identitas pengguna Anda saat ini:

   ```bash
   id
   ```

   Perhatikan UID, GID, dan grup-grup tempat Anda berada.

2. Lihat nama pengguna:

   ```bash
   whoami
   ```

3. Lihat siapa saja yang sedang login:

   ```bash
   who
   ```

   atau dengan informasi lebih detail:

   ```bash
   w
   ```

4. Amati file konfigurasi pengguna:

   ```bash
   cat /etc/passwd | head -10
   ```

   Format setiap baris: `username:password:UID:GID:deskripsi:home:shell`.

5. Gunakan `cut` dan `sort` untuk melihat shell apa saja yang digunakan:

   ```bash
   cat /etc/passwd | cut -d: -f7 | sort | uniq -c | sort -rn
   ```

   (Ini adalah pipeline yang sama seperti di modul P3.)

6. Lihat informasi grup:

   ```bash
   cat /etc/group | head -10
   ```

   Format: `nama_grup:password:GID:anggota`.

7. Hitung jumlah pengguna di sistem:

   ```bash
   cat /etc/passwd | wc -l
   ```

8. Hitung jumlah grup:

   ```bash
   cat /etc/group | wc -l
   ```

9. Lihat informasi login terakhir:

   ```bash
   last | head -10
   ```

### Percobaan 7: Manajemen Pengguna dan Grup

**Catatan:** Percobaan ini memerlukan hak akses `sudo`. Jika tidak memiliki akses, cukup amati dan catat perintah-perintahnya.

1. Buat pengguna baru:

   ```bash
   sudo useradd -m -s /bin/bash mahasiswa1
   ```

   Opsi `-m` membuat home directory, `-s /bin/bash` menetapkan shell default.

2. Buat pengguna kedua:

   ```bash
   sudo useradd -m -s /bin/bash mahasiswa2
   ```

3. Verifikasi bahwa pengguna berhasil dibuat:

   ```bash
   tail -5 /etc/passwd
   ```

4. Lihat home directory kedua pengguna:

   ```bash
   ls -l /home
   ```

   Perhatikan bahwa setiap home directory hanya dapat diakses oleh pemiliknya.

5. Setel password untuk pengguna baru:

   ```bash
   sudo passwd mahasiswa1
   ```

   Masukkan password ketika diminta. Gunakan password sederhana untuk percobaan (misalnya: `123`).

6. Lakukan hal yang sama untuk `mahasiswa2`.

7. Buat grup baru:

   ```bash
   sudo groupadd kelas_so
   ```

8. Tambahkan kedua pengguna ke grup `kelas_so`:

   ```bash
   sudo usermod -aG kelas_so mahasiswa1
   sudo usermod -aG kelas_so mahasiswa2
   ```

   Opsi `-aG` berarti *append* ke grup tambahan.

9. Verifikasi keanggotaan grup:

   ```bash
   cat /etc/group | grep kelas_so
   ```

   atau gunakan:

   ```bash
   groups mahasiswa1
   groups mahasiswa2
   ```

10. Informasi detail akun dengan `id`:

    ```bash
    id mahasiswa1
    id mahasiswa2
    ```

11. Coba login sebagai `mahasiswa1` (gunakan password yang telah diset):

    ```bash
    su - mahasiswa1
    ```

12. Di dalam sesi `mahasiswa1`, buat file dan lihat izinnya:

    ```bash
    touch file_mahasiswa1.txt
    ls -l file_mahasiswa1.txt
    exit
    ```

    Perhatikan bahwa pemilik file adalah `mahasiswa1`.

13. Hapus pengguna percobaan setelah selesai:

    ```bash
    sudo userdel -r mahasiswa1
    sudo userdel -r mahasiswa2
    sudo groupdel kelas_so
    ```

    Opsi `-r` menghapus home directory dan mail spool.

### Percobaan 8: Memantau Penggunaan Disk dengan `df` dan `du`

1. Lihat informasi filesystem dan penggunaan disk seluruh sistem:

   ```bash
   df -h
   ```

   Opsi `-h` (*human-readable*) menampilkan ukuran dalam format yang mudah dibaca (GB, MB).

2. Lihat filesystem dengan tipe tertentu:

   ```bash
   df -hT
   ```

   Opsi `-T` menampilkan tipe filesystem (ext4, xfs, tmpfs, dll).

3. Lihat penggunaan disk hanya untuk filesystem fisik (bukan *tmpfs* atau *ramfs*):

   ```bash
   df -h --type=ext4
   ```

   atau:

   ```bash
   df -h | grep -v tmpfs
   ```

4. Gunakan pipeline untuk menampilkan filesystem yang penggunaan disknya di atas 50%:

   ```bash
   df -h | awk '{print $5, $6}' | grep -v Use | sort -rn | head -10
   ```

5. Lihat ukuran direktori home:

   ```bash
   du -sh /home
   ```

   Opsi `-s` (summary) dan `-h` (human-readable).

6. Lihat 5 direktori atau file terbesar di dalam direktori saat ini:

   ```bash
   du -sh * 2>/dev/null | sort -rh | head -5
   ```

   (Pipeline ini mirip dengan yang ada di modul P3.)

7. Lihat ukuran setiap direktori di `/home` secara detail:

   ```bash
   sudo du -sh /home/* | sort -rh
   ```

8. Gunakan `lsblk` untuk melihat perangkat blok dan partisi:

   ```bash
   lsblk
   ```

9. Lihat informasi lebih detail tentang perangkat dan partisi:

   ```bash
   lsblk -f
   ```

   Opsi `-f` menampilkan filesystem, label, dan UUID.

10. Simpan ringkasan informasi filesystem ke file laporan:

    ```bash
    {
      echo "=== INFORMASI FILESYSTEM ==="
      echo "Waktu: $(date)"
      echo ""
      echo "-- Penggunaan Disk --"
      df -h
      echo ""
      echo "-- Perangkat Blok --"
      lsblk
      echo ""
      echo "-- 5 Direktori Terbesar di Home --"
      du -sh /home/* 2>/dev/null | sort -rh | head -5
    } > info_filesystem.txt

    cat info_filesystem.txt
    ```

### Percobaan 9: Mount dan Unmount Sederhana

**Catatan:** Percobaan ini memerlukan hak akses `sudo` dan sebaiknya dilakukan dengan pengawasan asisten jika di laboratorium.

1. Lihat daftar perangkat yang terpasang (*mounted*):

   ```bash
   mount
   ```

   Perhatikan output yang panjang. Setiap baris menunjukkan perangkat, titik mount, tipe filesystem, dan opsi mount.

2. Persempit output dengan grep untuk melihat hanya filesystem ext4:

   ```bash
   mount | grep ext4
   ```

3. Buat direktori untuk mount point:

   ```bash
   mkdir /tmp/percobaan_mount
   ```

4. Buat file kosong untuk disimulasikan sebagai image filesystem (jika diizinkan):

   ```bash
   dd if=/dev/zero of=/tmp/disk_image.img bs=1M count=50
   ```

   Perintah `dd` membuat file image kosong sebesar 50 MB.

5. Format file image sebagai filesystem ext4:

   ```bash
   mkfs.ext4 /tmp/disk_image.img
   ```

6. Mount file image:

   ```bash
   sudo mount /tmp/disk_image.img /tmp/percobaan_mount
   ```

7. Verifikasi bahwa filesystem berhasil di-mount:

   ```bash
   df -h | grep percobaan_mount
   ```

8. Buat file di dalam filesystem yang baru di-mount:

   ```bash
   sudo touch /tmp/percobaan_mount/file_disk.txt
   ls -l /tmp/percobaan_mount
   ```

9. Unmount filesystem:

   ```bash
   sudo umount /tmp/percobaan_mount
   ```

10. Verifikasi bahwa direktori sudah kosong (setelah di-unmount, filesystem tidak lagi terpasang):

    ```bash
    df -h | grep percobaan_mount
    ls -l /tmp/percobaan_mount
    ```

    Direktori `/tmp/percobaan_mount` masih ada tetapi isinya tidak terlihat karena filesystem sudah dilepas.

11. Bersihkan file percobaan:

    ```bash
    rmdir /tmp/percobaan_mount
    rm /tmp/disk_image.img
    ```

### Percobaan 10: Shell Script untuk Analisis File dan Filesystem

1. Buat file script bernama `analisis_filesystem.sh` dengan isi sebagai berikut:

   ```bash
   #!/bin/bash

   echo "=================================="
   echo " ANALISIS FILE DAN FILESYSTEM"
   echo "=================================="
   echo ""

   # 1. Informasi Pengguna
   echo "1. INFORMASI PENGGUNA"
   echo "   Pengguna aktif : $(whoami)"
   echo "   UID/GID        : $(id -u)/$(id -g)"
   echo "   Home           : $HOME"
   echo ""

   # 2. Ringkasan File di Direktori Aktif
   echo "2. RINGKASAN FILE DI DIREKTORI AKTIF"
   echo "   Direktori      : $(pwd)"
   echo "   Total file     : $(ls -l | grep '^-' | wc -l)"
   echo "   Total direktori: $(ls -l | grep '^d' | wc -l)"
   echo "   File tersembunyi: $(ls -la | grep '^-' | wc -l)"
   echo ""

   # 3. Distribusi Izin File
   echo "3. DISTRIBUSI IZIN FILE"
   echo "   File yang dapat dieksekusi   : $(find . -maxdepth 1 -type f -executable 2>/dev/null | wc -l)"
   echo "   File dengan izin 777         : $(find . -maxdepth 1 -type f -perm 777 2>/dev/null | wc -l)"
   echo ""

   # 4. Informasi Filesystem
   echo "4. INFORMASI FILESYSTEM"
   echo "   Total ruang disk : $(df -h / | awk 'NR==2 {print $2}')"
   echo "   Terpakai         : $(df -h / | awk 'NR==2 {print $3}')"
   echo "   Tersedia         : $(df -h / | awk 'NR==2 {print $4}')"
   echo "   Persentase       : $(df -h / | awk 'NR==2 {print $5}')"
   echo ""

   # 5. 5 File/Direktori Terbesar di Direktori Aktif
   echo "5. 5 FILE/DIREKTORI TERBESAR (DI SINI)"
   du -sh * 2>/dev/null | sort -rh | head -5
   echo ""

   # 6. Pengguna yang Login
   echo "6. PENGGUNA YANG SEDANG LOGIN"
   who | awk '{print "   " $1 " sejak " $3 " " $4}'
   echo ""

   echo "=================================="
   echo " ANALISIS SELESAI"
   echo "=================================="
   ```

2. Simpan file, ubah hak akses, lalu jalankan:

   ```bash
   chmod +x analisis_filesystem.sh
   ./analisis_filesystem.sh
   ```

3. Amati setiap bagian output yang dihasilkan.

4. Simpan output script ke dalam file:

   ```bash
   ./analisis_filesystem.sh > hasil_analisis.txt
   cat hasil_analisis.txt
   ```

5. Buat script kedua bernama `cek_permission.sh` untuk memeriksa izin file secara detail:

   ```bash
   #!/bin/bash

   if [ $# -eq 0 ]; then
       echo "Penggunaan: $0 <file_atau_direktori>"
       exit 1
   fi

   TARGET="$1"

   if [ ! -e "$TARGET" ]; then
       echo "Error: '$TARGET' tidak ditemukan."
       exit 1
   fi

   echo "=== ANALISIS IZIN: $TARGET ==="
   echo ""

   # Tipe file
   if [ -f "$TARGET" ]; then
       echo "Tipe: File biasa"
   elif [ -d "$TARGET" ]; then
       echo "Tipe: Direktori"
   elif [ -L "$TARGET" ]; then
       echo "Tipe: Symbolic link"
   else
       echo "Tipe: Lainnya"
   fi

   # Cek izin
   echo ""
   echo "Izin file (stat):"
   stat -c "%A (%a)" "$TARGET"
   echo ""

   # Cek akses
   echo "Cek akses pengguna saat ini:"
   [ -r "$TARGET" ] && echo "  Dapat dibaca  (read)" || echo "  Tidak dapat dibaca"
   [ -w "$TARGET" ] && echo "  Dapat ditulis (write)" || echo "  Tidak dapat ditulis"
   [ -x "$TARGET" ] && echo "  Dapat dieksekusi (execute)" || echo "  Tidak dapat dieksekusi"
   echo ""

   # Kepemilikan
   echo "Kepemilikan:"
   echo "  Pemilik: $(stat -c '%U' "$TARGET")"
   echo "  Grup  : $(stat -c '%G' "$TARGET")"
   echo "  Size  : $(stat -c '%s' "$TARGET") bytes"
   ```

6. Simpan file, ubah hak akses, lalu jalankan dengan argumen file atau direktori:

   ```bash
   chmod +x cek_permission.sh
   ./cek_permission.sh analisis_filesystem.sh
   ./cek_permission.sh /etc/passwd
   ./cek_permission.sh /tmp
   ```

7. Amati perbedaan output untuk berbagai jenis target.

### Percobaan 11: Pipeline Analisis Izin di Seluruh Sistem

Pada percobaan ini, Anda akan menggunakan pipeline untuk menganalisis izin file di berbagai bagian sistem — mengintegrasikan keterampilan dari P3 (pipe, grep, sort, wc) dengan konsep izin dari P4.

1. Hitung jumlah total file di sistem yang memiliki izin *world-writable* (dapat ditulis oleh semua orang):

   ```bash
   find / -type f -perm -o+w 2>/dev/null | wc -l
   ```

2. Cari 10 file *world-writable* teratas:

   ```bash
   find / -type f -perm -o+w 2>/dev/null | head -10
   ```

3. Cari direktori dengan sticky bit (biasanya direktori bersama):

   ```bash
   find / -type d -perm -1000 2>/dev/null | head -10
   ```

4. Analisis shell apa yang paling banyak digunakan di sistem:

   ```bash
   cut -d: -f7 /etc/passwd | sort | uniq -c | sort -rn
   ```

5. Cari 10 file terbesar di sistem (perlu `sudo`):

   ```bash
   sudo find / -type f -size +100M 2>/dev/null | head -10
   ```

6. Hitung total file per tipe filesystem:

   ```bash
   df -hT | grep -v tmpfs | grep -v Filesystem | awk '{print $2}' | sort | uniq -c
   ```

7. Buat laporan akhir menggunakan redirection ke satu file:

   ```bash
   {
     echo "LAPORAN ANALISIS IZIN DAN FILESYSTEM"
     echo "==================================="
     echo "Waktu: $(date)"
     echo ""
     echo "File world-writable: $(find / -type f -perm -o+w 2>/dev/null | wc -l)"
     echo "Direktori sticky: $(find / -type d -perm -1000 2>/dev/null | wc -l)"
     echo "Total pengguna: $(cat /etc/passwd | wc -l)"
     echo "Total grup: $(cat /etc/group | wc -l)"
     echo ""
     echo "-- Ringkasan Filesystem --"
     df -h /
     echo ""
     echo "-- Shell yang digunakan --"
     cut -d: -f7 /etc/passwd | sort | uniq -c | sort -rn
   } > laporan_izin_sistem.txt

   cat laporan_izin_sistem.txt
   ```

## F. Tugas Akhir Praktikum
Pelajari dan praktikkan, nanti akan di Presentasikan Praktikumnya online atau offline (menyesuaikan)

---
By: elyas@fedora.linux
