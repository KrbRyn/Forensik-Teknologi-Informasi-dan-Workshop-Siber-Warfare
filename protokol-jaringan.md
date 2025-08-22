# Protokol Jaringan XYZ

Dokumen ini mendeskripsikan protokol jaringan sederhana untuk komunikasi antara client dan server.

## 1. Topologi

- Model: Client-Server
- Transport: TCP/IP

## 2. Format Pesan

Setiap pesan dikirim dalam bentuk JSON dengan struktur:

```json
{
  "type": "string",      // Jenis pesan, misal: "login", "data", "logout"
  "timestamp": "ISO8601",// Waktu pengiriman pesan
  "payload": {...}       // Data tambahan sesuai tipe pesan
}
```

### Contoh Pesan Login

```json
{
  "type": "login",
  "timestamp": "2025-08-22T02:52:48Z",
  "payload": {
    "username": "user123",
    "password": "hashed_password"
  }
}
```

### Contoh Pesan Data

```json
{
  "type": "data",
  "timestamp": "2025-08-22T02:53:10Z",
  "payload": {
    "sensor_id": "A101",
    "value": 23.5,
    "unit": "C"
  }
}
```

## 3. Tipe Pesan

| Tipe      | Deskripsi                       |
|-----------|---------------------------------|
| login     | Autentikasi pengguna            |
| data      | Pengiriman data sensor/informasi|
| logout    | Mengakhiri sesi                 |
| ping      | Cek koneksi                     |
| ack       | Konfirmasi penerimaan           |

## 4. Proses Komunikasi

1. Client mengirim pesan **login** ke server.
2. Jika login sukses, server mengirim **ack**.
3. Client mengirim pesan **data** secara berkala.
4. Server membalas dengan **ack** tiap data diterima.
5. Client mengirim **logout** saat selesai.
6. Server membalas dengan **ack** lalu menutup sesi.

## 5. Error Handling

- Jika pesan tidak valid, server mengirim:
```json
{
  "type": "error",
  "timestamp": "2025-08-22T02:54:00Z",
  "payload": {
    "code": 400,
    "message": "Invalid message format"
  }
}
```

## 6. Security

- Disarankan enkripsi komunikasi menggunakan TLS.
- Password dikirim dalam bentuk hash.

---

**Catatan:** Protokol ini dapat dikembangkan sesuai kebutuhan aplikasi.