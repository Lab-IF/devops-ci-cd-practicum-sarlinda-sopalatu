# Laporan Praktikum Pertemuan 01: DevOps Culture & Principles

**Nama:** Sarlinda Sopalatu  
**NIM:** 105841101423  

---

## 1. Penjelasan Mendetail tentang DevOps

Secara harfiah, **DevOps** adalah lakuran (gabungan) dari *Development* (Pengembangan Perangkat Lunak) dan *Operations* (Operasi Teknologi Informasi). Namun, secara konsep, DevOps bukanlah sekadar sebuah alat (*tool*) atau perangkat lunak, melainkan sebuah **budaya kerja, filosofi, dan serangkaian praktik** yang bertujuan untuk menyatukan kedua tim tersebut.

Dalam pendekatan tradisional, tim *Development* dan tim *Operations* sering kali terisolasi (*siloed*). Tim Dev berfokus pada seberapa cepat mereka bisa merilis fitur baru, sementara tim Ops berfokus pada menjaga stabilitas *server* agar tidak *down* atau *error*. Perbedaan fokus ini sering memunculkan "tembok pembatas" di mana pembaruan aplikasi memakan waktu lama dan rentan terhadap kegagalan. 

DevOps hadir untuk meruntuhkan tembok tersebut dengan menekankan integrasi yang erat, kolaborasi berkelanjutan, dan pembagian tanggung jawab yang sama sejak tahap perencanaan aplikasi hingga aplikasi tersebut digunakan oleh pengguna (klien).

## 2. Mengapa DevOps Sangat Penting?

Penerapan DevOps telah menjadi standar industri saat ini karena memberikan dampak yang sangat signifikan, antara lain:

1. **Kecepatan dan *Time-to-Market* yang Singkat:** Dengan DevOps, pembaruan aplikasi tidak lagi dilakukan secara manual yang memakan waktu berminggu-minggu. Otomatisasi pada proses *build* dan *deploy* memungkinkan tim untuk merilis fitur baru, perbaikan *bug*, atau pembaruan keamanan kepada pengguna dengan sangat cepat (bahkan bisa berkali-kali dalam sehari).

2. **Otomatisasi dan Pengurangan *Human Error*:**
   DevOps sangat bergantung pada otomatisasi tugas-tugas repetitif. Dengan menggunakan praktik *Continuous Integration* dan *Continuous Deployment* (CI/CD), proses pengujian dan pemindahan kode ke *server* dilakukan oleh sistem, sehingga meminimalisir kesalahan yang sering diakibatkan oleh kelalaian manusia (*human error*).

3. **Kolaborasi dan Transparansi yang Kuat:**
   DevOps mengubah budaya saling menyalahkan menjadi budaya saling mendukung. Pengembang dan administrator sistem saling berbagi informasi, berbagi alat ukur (KPI), dan memecahkan masalah bersama. Hal ini secara drastis mengurangi gesekan komunikasi.

4. **Kualitas, Stabilitas, dan Keandalan:**
   Melalui praktik pengujian otomatis yang konstan dan pemantauan sistem (*monitoring*) secara *real-time*, tim dapat mengidentifikasi *bug* atau penurunan performa lebih awal. Selain itu, penggunaan *container* seperti Docker memastikan bahwa aplikasi berjalan dengan konsisten di lingkungan mana pun, baik di laptop pengembang maupun di *server* utama.

5. **Efisiensi (Prinsip Lean):**
   DevOps mengadopsi prinsip *Lean*, yaitu mengeliminasi pemborosan (*waste*). Ini termasuk mengurangi waktu tunggu (*waiting time*) antar tim dan menghindari pekerjaan yang tidak memberikan nilai tambah, sehingga tim bisa lebih fokus pada inovasi.

## 3. DevOps Lifecycle (Siklus Hidup DevOps)

Penerapan DevOps di atas diwujudkan dalam sebuah siklus berkelanjutan (*infinity loop*) yang terdiri dari:
* **Plan & Code:** Merencanakan fitur dan menulis kode (menggunakan Git).
* **Build & Test:** Mengemas kode dan melakukan pengujian otomatis secara ketat.
* **Release & Deploy:** Merilis dan menerapkan aplikasi ke *server* produksi secara otomatis.
* **Operate & Monitor:** Mengelola aplikasi yang berjalan dan memantau performanya untuk dijadikan bahan evaluasi pada fase *Plan* berikutnya.

---

## 4. Screenshot Environment

1. **Bukti instalasi Git (Version Control):** `git-version.png`
2. **Bukti instalasi Docker (Containerization):** `docker-version.png`
3. **Bukti ekstensi VS Code (IDE & Extensions):** `vscode-setup.png`