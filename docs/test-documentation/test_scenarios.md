# Test Scenarios – Password Recovery

## TS-01 – Secure & Controlled Password Recovery Flow

### Objective
Memastikan mekanisme password recovery memungkinkan user memulihkan akses akun secara end-to-end dengan kontrol keamanan yang mencegah :

- Account enumeration
- Token replay
- Session persistence setelah reset
- Credential inconsistency
#### Risk Level: Critical – Authentication Boundary

### Scenario Coverage

1. Sistem tidak membocorkan keberadaan akun melalui response message, status code, atau timing variance.
2. Reset token :
- Bersifat single-use
- Memiliki expiry time yang enforce di server
- Tidak dapat digunakan ulang setelah password berhasil diubah
3. Password update :
- Terjadi secara atomic (tidak partial update)
- Menginvalidasi semua active session
4. Password policy:
- Diverifikasi server-side (bukan hanya client-side)
5. Email diproses secara case-insensitive untuk menjaga konsistensi identitas.
