# Test Scenarios – Password Recovery

## TS-01 – Secure & Controlled Password Recovery Flow

### Objective
Memastikan mekanisme password recovery memungkinkan user memulihkan akses akun secara end-to-end dengan kontrol keamanan yang mencegah :

- Account enumeration
- Token replay
- Session persistence setelah reset
- Credential inconsistency
#### Risk Level: Critical – Authentication Boundary

### Skenario ini memverifikasi bahwa :

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

### Engineering Assumptions
- Backend menyimpan reset token secara hashed (bukan plaintext)
- Expiry diverifikasi di server, bukan hanya UI
- Password change dan session invalidation berada dalam satu transaction boundary
- Email lookup dilakukan secara case-insensitive di backend

### Possible Technical Failure Patterns
- Token tidak di-invalidate karena race condition
- Multiple reset request menghasilkan token lama masih valid
- Password update sukses tapi session tidak invalid
- Email comparison case-sensitive di DB
