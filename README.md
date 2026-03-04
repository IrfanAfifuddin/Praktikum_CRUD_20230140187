# Praktikum 1 - User Management REST API

Aplikasi REST API sederhana untuk manajemen data pengguna menggunakan **Spring Boot**, **Spring Data JPA**, **MySQL**, **Lombok**, **MapStruct**, dan **Validation**.

---

## Tampilan Website

![Daftar Pengguna](<img width="1919" height="997" alt="image" src="https://github.com/user-attachments/assets/8a409692-9018-473a-a05e-decd0d3f0339" />)

---

## Base URL

```
http://localhost:8080
```

---

## Ringkasan Endpoint

| Method | Endpoint | Deskripsi |
|--------|----------|-----------|
| POST | /api/users | Tambah user baru |
| GET | /api/users | Ambil semua user |
| GET | /api/users/{id} | Ambil user by ID |
| PUT | /api/users/{id} | Update user by ID |
| DELETE | /api/users/{id} | Hapus user by ID |

---

## Detail Endpoint

### 1. Create User — Tambah User

**Endpoint:**
```
POST /api/users
```

**Request Header:**
```
Content-Type: application/json
```

**Request Body:**
```json
{
  "name": "Irfan Afifuddin",
  "age": 20
}
```

**Response — 201 Created (Berhasil):**
```json
{
  "status": "success",
  "data": {
    "id": "86661826-9ab4-428e-810d-6562b01da57b",
    "name": "Irfan Afifuddin",
    "age": 20
  }
}
```

**Response — 400 Bad Request (Field kosong):**
```json
{
  "status": "error",
  "message": "name: must not be blank, age: must be greater than 0"
}
```

**Response — 400 Bad Request (Tipe data salah):**
```json
{
  "status": "error",
  "message": "age: must be a number"
}
```

---

### 2. Get All Users — Ambil Semua User

**Endpoint:**
```
GET /api/users
```

**Response — 200 OK (Berhasil):**
```json
{
  "status": "success",
  "data": [
    {
      "id": "86661826-9ab4-428e-810d-6562b01da57b",
      "name": "Irfan Afifuddin",
      "age": 20
    }
  ]
}
```

**Response — 200 OK (Data kosong):**
```json
{
  "status": "success",
  "data": []
}
```

---

### 3. Get User By ID — Ambil User Berdasarkan ID

**Endpoint:**
```
GET /api/users/{id}
```

**Contoh:**
```
GET /api/users/86661826-9ab4-428e-810d-6562b01da57b
```

**Response — 200 OK (Berhasil):**
```json
{
  "status": "success",
  "data": {
    "id": "86661826-9ab4-428e-810d-6562b01da57b",
    "name": "Irfan Afifuddin",
    "age": 20
  }
}
```

**Response — 404 Not Found (ID tidak ditemukan):**
```json
{
  "status": "error",
  "message": "user not found"
}
```

**Response — 400 Bad Request (ID tidak valid):**
```json
{
  "status": "error",
  "message": "invalid id format"
}
```

---

### 4. Update User — Perbarui Data User

**Endpoint:**
```
PUT /api/users/{id}
```

**Contoh:**
```
PUT /api/users/86661826-9ab4-428e-810d-6562b01da57b
```

**Request Header:**
```
Content-Type: application/json
```

**Request Body:**
```json
{
  "name": "Irfan Afifuddin Updated",
  "age": 21
}
```

**Response — 200 OK (Berhasil):**
```json
{
  "status": "success",
  "data": {
    "id": "86661826-9ab4-428e-810d-6562b01da57b",
    "name": "Irfan Afifuddin Updated",
    "age": 21
  }
}
```

**Response — 404 Not Found (ID tidak ditemukan):**
```json
{
  "status": "error",
  "message": "user not found"
}
```

**Response — 400 Bad Request (Field kosong):**
```json
{
  "status": "error",
  "message": "name: must not be blank, age: must be greater than 0"
}
```

**Response — 400 Bad Request (Tipe data salah):**
```json
{
  "status": "error",
  "message": "age: must be a number"
}
```

---

### 5. Delete User — Hapus User

**Endpoint:**
```
DELETE /api/users/{id}
```

**Contoh:**
```
DELETE /api/users/86661826-9ab4-428e-810d-6562b01da57b
```

**Response — 200 OK (Berhasil):**
```json
{
  "status": "success delete user with id 86661826-9ab4-428e-810d-6562b01da57b"
}
```

**Response — 404 Not Found (ID tidak ditemukan):**
```json
{
  "status": "error",
  "message": "user not found"
}
```

**Response — 400 Bad Request (ID tidak valid):**
```json
{
  "status": "error",
  "message": "invalid id format"
}
```

---

## Teknologi yang Digunakan

- **Spring Boot** — Framework utama
- **Spring Data JPA** — ORM untuk database
- **MySQL** — Database relasional
- **Lombok** — Mengurangi boilerplate code
- **MapStruct** — Mapping antar object (DTO ↔ Entity)
- **Validation** — Validasi request body
