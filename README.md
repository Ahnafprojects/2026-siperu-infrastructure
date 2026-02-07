# Siperu Infrastructure

![CI](https://github.com/Ahnafprojects/2026-siperu-infrastructure/actions/workflows/ci.yml/badge.svg)

## Deskripsi
Repositori ini mengatur orkestrasi layanan Siperu (backend ASP.NET dan frontend React + Vite) menggunakan Docker Compose. Fokusnya adalah setup lokal yang cepat, konsisten, dan mudah dijalankan oleh semua anggota tim.

## Fitur
- Menjalankan backend dan frontend dengan satu perintah
- Port lokal sudah terkonfigurasi untuk pengembangan
- Persistensi database backend melalui volume
- Dokumentasi operasional singkat dan jelas

## Teknologi
- Docker
- Docker Compose
- ASP.NET (repo backend terpisah)
- React + Vite (repo frontend terpisah)

## Struktur Folder
Repositori ini mengasumsikan dua repo sibling di level yang sama:
```text
../2026-siperu-backend
../2026-siperu-frontend
./2026-siperu-infrastructure (repo ini)
```

## Instalasi
1. Instal Docker Desktop (atau Docker Engine + Compose).
2. Pastikan repo `2026-siperu-backend` dan `2026-siperu-frontend` sudah berada di folder sibling.
3. Salin `.env.example` menjadi `.env`, lalu sesuaikan jika perlu.

## Cara Menjalankan
1. Build dan jalankan semua service.
```bash
docker compose up --build
```
2. Akses aplikasi.
Backend API tersedia di `http://localhost:5250`.
Frontend tersedia di `http://localhost:5173`.

3. Hentikan layanan.
```bash
docker compose down
```

4. Lihat log realtime.
```bash
docker compose logs -f
```

5. Menjalankan satu service saja.
```bash
docker compose up backend
```
```bash
docker compose up frontend
```

## Environment Variables
Buat file `.env` di root repo ini (jangan commit). Variabel yang dipakai:
- `ASPNETCORE_ENVIRONMENT` (default: `Development`)
- `VITE_API_URL` (default: `http://localhost:5250/api`)

## Troubleshooting
- Frontend tidak bisa akses API.
Pastikan `VITE_API_URL` mengarah ke `http://localhost:5250/api` dan backend sudah berjalan.

- Port bentrok.
Ubah mapping port di `docker-compose.yml`.

- Database tidak persisten.
Pastikan path volume backend valid dan punya permission.

## FAQ
- Apakah harus menjalankan backend dan frontend dari repo ini?
Iya. Repo ini hanya untuk orkestrasi. Kode aplikasi ada di repo backend dan frontend.

- Apakah bisa menjalankan hanya salah satu service?
Bisa. Gunakan `docker compose up backend` atau `docker compose up frontend`.

## Deployment (Sederhana)
1. Siapkan server dengan Docker dan Docker Compose.
2. Clone repo ini dan pastikan repo backend dan frontend berada di folder sibling.
3. Set `.env` sesuai environment server.
4. Jalankan `docker compose up -d --build`.

## Kontribusi
Buat pull request dengan deskripsi yang jelas. Usahakan perubahan tetap fokus ke infrastruktur dan workflow.

## Lisensi
MIT

## Kredit
Tim Siperu Infrastructure.
