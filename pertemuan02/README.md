# LAPORAN PRAKTIKUM DEVOPS – PERTEMUAN 02 
**Materi:** Praktikum Docker Dasar, Dockerfile, dan Docker Compose

**Nama:** Sarlinda Sopalatu  
**NIM:** 105841101423  

---

## TASK 1 – Eksplorasi Docker Dasar

### Tujuan
Memahami *lifecycle* (siklus hidup) dasar dari sebuah container Docker, mulai dari proses mengunduh image (pull), menjalankan, memantau *logs*, berinteraksi di dalam terminal container, hingga menghentikan dan menghapusnya.

### Langkah-Langkah

**1. Pull Image**
`docker pull nginx:alpine`
> **Penjelasan:** Perintah ini mengunduh *image* resmi Nginx dari Docker Hub. Varian `alpine` dipilih karena menggunakan OS Linux Alpine yang ukurannya sangat kecil dan ringan, sehingga menghemat ruang penyimpanan dan mempercepat proses *pull*.

**2. Menjalankan Container**
`docker run -d --name web-praktikum -p 8080:80 nginx:alpine`
> **Penjelasan Perintah:**
> - `-d` (detached): Menjalankan container di latar belakang agar terminal tetap bisa digunakan.
> - `--name web-praktikum`: Memberikan nama spesifik pada container.
> - `-p 8080:80`: Menghubungkan port 8080 di laptop ke port 80 di dalam container Nginx.

**Cek container berjalan:**
`docker ps`
> **Hasil:** Menampilkan daftar container yang sedang aktif beserta detail *Container ID*, *Status*, dan *Ports*.

**3. Mengakses Aplikasi**
Buka browser dan akses URL berikut:
`http://localhost:8080`
> **Hasil:** Halaman default "Welcome to nginx!" berhasil ditampilkan.

**4. Melihat Logs**
`docker logs web-praktikum`
> **Penjelasan:** Digunakan untuk melihat riwayat aktivitas (*request HTTP* atau *error*) yang terjadi di dalam Nginx untuk keperluan *troubleshooting*.

**5. Masuk ke Dalam Container**
`docker exec -it web-praktikum sh`
> **Penjelasan:** Flag `-it` (Interactive TTY) memungkinkan kita membuka dan masuk ke dalam terminal *shell* (`sh`) bawaan container tersebut.

**Eksplorasi di dalam container:**
`ls -la /usr/share/nginx/html` *(Melihat letak file web bawaan Nginx)*
`cat /etc/nginx/nginx.conf` *(Melihat konfigurasi utama server Nginx)*
`exit` *(Keluar dari dalam container)*

**6. Stop dan Hapus Container**
`docker stop web-praktikum`
`docker rm web-praktikum`
> **Penjelasan:** Proses dihentikan secara aman (graceful shutdown) dengan `stop`, lalu dihapus dari sistem dengan `rm` agar tidak membebani memori perangkat.

### Kesimpulan Task 1
Lifecycle container Docker terdiri dari: **create → run → stop → remove**. Container jauh lebih ringan dan cepat dibanding Virtual Machine (VM) karena tidak memerlukan proses *booting* sistem operasi yang berat.

---

## TASK 2 – Membuat Custom Docker Image

### Tujuan
Membuat *image* Docker kustom sendiri menggunakan `Dockerfile` agar aplikasi dan lingkungannya dapat dibungkus secara utuh.

### Struktur Project
```text
praktikum-docker/
├── Dockerfile
└── app/
    └── index.html

### Isi Dockerfile
dockerfile
FROM nginx:alpine
COPY app/index.html /usr/share/nginx/html/index.html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
### Penjelasan
- FROM → menggunakan base image nginx alpine
- COPY → menyalin file HTML ke direktori nginx
- EXPOSE → mendeklarasikan port 80
- CMD → menjalankan nginx di foreground

## Build Image
bash
docker build -t praktikum-docker:v1 .
Cek image:
bash
docker images
## Menjalankan Container
bash
docker run -d -p 8080:80 --name praktikum-web praktikum-docker:v1
Akses:
http://localhost:8080
Hasil: Website custom dengan nama dan NIM berhasil ditampilkan.
## Kesimpulan Task 2
Saya berhasil:
- Membuat Dockerfile
- Build image
- Menjalankan container dari image custom
Dockerfile memungkinkan pembuatan environment aplikasi yang konsisten dan portable.

# TASK 3 – Docker Compose Multi-Container
## Tujuan
Menjalankan beberapa container sekaligus dalam satu konfigurasi menggunakan Docker Compose.
## Services yang Digunakan
- Web → nginx
- API → httpd
- Database → postgres
## 🔹 Menjalankan Docker Compose
bash
docker compose up -d
Cek status:
bash
docker compose ps
Melihat logs:
bash
docker compose logs -f
## Pengujian
Web:
http://localhost:8080
API:
http://localhost:8081
Kedua service berhasil berjalan dengan baik.
## Cleanup
bash
docker compose down -v

# Perbedaan Container vs Virtual Machine
| Container | Virtual Machine |
|------------|----------------|
| Ringan | Lebih berat |
| Startup cepat | Startup lebih lama |
| Share kernel OS | Memiliki OS sendiri |
| Cocok untuk microservices | Cocok untuk isolasi penuh |

# Screenshot
Screenshot yang dilampirkan dalam folder `screenshots/`:
1. Output docker ps  
2. Tampilan nginx di browser  
3. Output docker build  
4. Image berhasil dibuat  
5. Docker compose ps  
6. Tampilan web & api service  

# Kesimpulan Akhir
Pada praktikum ini saya telah:
✅ Memahami lifecycle container Docker  
✅ Menjalankan dan mengelola container  
✅ Membuat custom Docker image menggunakan Dockerfile  
✅ Menjalankan multi-container menggunakan Docker Compose  
Docker membantu proses deployment aplikasi menjadi lebih cepat, ringan, dan konsisten.