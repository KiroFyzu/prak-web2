# Laporan 5 Praktikum Pemrograman Web 2

## Judul

API RESTful dan Standar Response

## Tujuan Praktikum

Tujuan dari praktikum ini adalah:

1. Memahami konsep dasar API RESTful pada aplikasi Laravel.
2. Membuat endpoint API dengan method HTTP yang sesuai.
3. Mengimplementasikan standar response JSON pada API.
4. Menguji endpoint API menggunakan tool seperti Postman, Thunder Client, atau cURL.
5. Menangani response sukses dan error secara konsisten.

## Dasar Teori

### API

API atau Application Programming Interface adalah mekanisme yang memungkinkan sebuah aplikasi berkomunikasi dengan aplikasi lain. Dalam pengembangan web, API sering digunakan untuk mengirim dan menerima data antara frontend, backend, aplikasi mobile, atau layanan pihak ketiga.

### RESTful API

RESTful API adalah arsitektur API yang mengikuti prinsip REST atau Representational State Transfer. API RESTful biasanya menggunakan method HTTP untuk menentukan operasi terhadap resource.

| Method | Fungsi |
| --- | --- |
| GET | Mengambil data |
| POST | Menambahkan data baru |
| PUT/PATCH | Mengubah data yang sudah ada |
| DELETE | Menghapus data |

### Standar Response

Standar response digunakan agar format balasan API konsisten dan mudah dipahami oleh client. Response API umumnya menggunakan format JSON.

Contoh response sukses:

```json
{
    "success": true,
    "message": "Data berhasil diambil",
    "data": []
}
```

Contoh response error:

```json
{
    "success": false,
    "message": "Data tidak ditemukan",
    "data": null
}
```

## Persiapan Project

Langkah awal menjalankan project Laravel:

```bash
composer install
cp .env.example .env
php artisan key:generate
php artisan migrate
php artisan serve
```

Jika menggunakan database, sesuaikan konfigurasi pada file `.env`.

## 1. Git Branching & Setup Environment

Pada tahap awal pengerjaan modul ini, project dipindahkan dari branch `main` ke branch baru bernama `feature/api-design`. Branch baru ini digunakan agar pengerjaan modul API RESTful dan standar response terpisah dari branch utama.

Perintah yang digunakan:

```bash
git checkout -b feature/api-design
```

Hasil setelah branch dibuat:

```bash
Switched to a new branch 'feature/api-design'
```

Untuk memastikan branch aktif, digunakan perintah:

```bash
git branch
```

Output:

```bash
* feature/api-design
  main
```

Screenshot:

Tambahkan screenshot terminal yang menampilkan daftar branch dengan tanda aktif `*` pada branch `feature/api-design`.

## Implementasi

### 1. Membuat Route API

Route API dibuat pada file `routes/api.php`.

```php
Route::get('/nama-resource', [NamaController::class, 'index']);
Route::post('/nama-resource', [NamaController::class, 'store']);
Route::get('/nama-resource/{id}', [NamaController::class, 'show']);
Route::put('/nama-resource/{id}', [NamaController::class, 'update']);
Route::delete('/nama-resource/{id}', [NamaController::class, 'destroy']);
```

### 2. Membuat Controller

Controller digunakan untuk mengatur proses request dan response API.

```bash
php artisan make:controller Api/NamaController
```

### 3. Membuat Standar Response JSON

Setiap endpoint API mengembalikan response dengan format yang konsisten.

```php
return response()->json([
    'success' => true,
    'message' => 'Data berhasil diproses',
    'data' => $data
], 200);
```

### 4. Menangani Error

Response error diberikan ketika proses gagal, misalnya data tidak ditemukan atau validasi gagal.

```php
return response()->json([
    'success' => false,
    'message' => 'Data tidak ditemukan',
    'data' => null
], 404);
```

## Daftar Endpoint

| Method | Endpoint | Keterangan | Status Code |
| --- | --- | --- | --- |
| GET | `/api/nama-resource` | Menampilkan semua data | 200 |
| POST | `/api/nama-resource` | Menambahkan data baru | 201 |
| GET | `/api/nama-resource/{id}` | Menampilkan detail data | 200 |
| PUT/PATCH | `/api/nama-resource/{id}` | Mengubah data | 200 |
| DELETE | `/api/nama-resource/{id}` | Menghapus data | 200 |

## Hasil Pengujian

### Pengujian GET

Tambahkan screenshot atau hasil response dari endpoint GET.

```json
{
    "success": true,
    "message": "Data berhasil diambil",
    "data": []
}
```

### Pengujian POST

Tambahkan screenshot atau hasil response dari endpoint POST.

```json
{
    "success": true,
    "message": "Data berhasil ditambahkan",
    "data": {}
}
```

### Pengujian PUT/PATCH

Tambahkan screenshot atau hasil response dari endpoint PUT/PATCH.

```json
{
    "success": true,
    "message": "Data berhasil diperbarui",
    "data": {}
}
```

### Pengujian DELETE

Tambahkan screenshot atau hasil response dari endpoint DELETE.

```json
{
    "success": true,
    "message": "Data berhasil dihapus",
    "data": null
}
```

## Pembahasan

Pada praktikum ini, API RESTful dibuat dengan memanfaatkan route, controller, dan response JSON pada Laravel. Setiap endpoint menggunakan method HTTP sesuai fungsinya. Format response dibuat konsisten agar client dapat membaca status, pesan, dan data dengan mudah.

Tuliskan pembahasan tambahan sesuai implementasi yang dibuat pada project.

## Kendala

Tuliskan kendala yang ditemukan selama praktikum, misalnya:

1. Kesalahan konfigurasi database pada file `.env`.
2. Route API tidak terbaca.
3. Validasi request belum sesuai.
4. Response JSON belum konsisten.

## Kesimpulan

Berdasarkan praktikum yang telah dilakukan, dapat disimpulkan bahwa API RESTful pada Laravel dapat dibuat menggunakan route API dan controller. Standar response JSON membantu membuat API lebih rapi, konsisten, dan mudah digunakan oleh client.

## Lampiran

Tambahkan screenshot hasil pengujian API, kode program penting, atau dokumentasi endpoint yang digunakan dalam praktikum.
