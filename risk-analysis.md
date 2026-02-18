# Risk Analysis – Password Recovery

Fitur Password Recovery merupakan salah satu alur dengan **risiko tertinggi** dalam sistem autentikasi karena menyentuh akses akun tanpa kredensial utama. Kegagalan pada alur ini berdampak langsung pada keamanan akun, kepercayaan user, dan beban operasional.

## Risiko Utama yang Diidentifikasi

### 1. Account Enumeration & Information Disclosure Risk

Dampak :
- Enumerasi akun valid
- Peningkatan risiko phishing dan brute-force
- Information leakage tentang arsitektur sistem
- Penurunan kepercayaan user terhadap keamanan platform

Mitigasi yang diverifikasi melalui TC-01, TC-02, TC-03, TC-11, TC-16 :
- Pesan selalu generik
- Tidak mengonfirmasi keberadaan akun
- Tidak mengekspos detail teknis
- Logging detail hanya di server
- Penerbitan token baru harus langsung membatalkan token-token sebelumnya secara bersamaan (atomik)

### 2. Token Security & Lifecycle Management Risk

Dampak :
- Token replay
- Account takeover
- Penyalahgunaan link reset yang bocor
- Insiden keamanan tingkat tinggi

Mitigasi yang diverifikasi melalui TC-04, TC-10, TC-14, TC-15 :
- Token memiliki expiry
- Token single-use
- Token invalid setelah digunakan
- User diarahkan request ulang jika expired

### 3. Session Management & Post-Reset Security Risk

Dampak:
- Session lama tetap aktif
- Reset tidak menghentikan compromise
- Unauthorized persistent access

Mitigasi yang diverifikasi melalui TC-12:

- Semua session aktif diinvalidasi
- User login ulang
- Token autentikasi lama tidak berlaku

### 4. Password Policy & Credential Integrity Risk

Dampak :
- Password lemah tetap digunakan
- Reuse password lama
- User terkunci
- Inconsistent credential state
- Audit finding

Mitigasi yang diverifikasi melalui TC-05, TC-06, TC-07, TC-09, TC-13 :

- Policy enforced di backend
- Reuse ditolak
- Valid password tidak ditolak
- Update dilakukan secara atomic
- Login setelah reset berjalan normal

### 5. Input Handling & Identity Consistency Risk

Dampak :
- Duplikasi akun
- Fragmentasi identitas
- Gagal autentikasi

Mitigasi yang diverifikasi melalui TC-08:
- Email dinormalisasi
- Validasi konsisten lintas modul
- Data identitas tidak ambigu

- 
## Risiko yang Sengaja Tidak Dicakup

Beberapa risiko tidak diuji dalam scope portofolio ini karena keterbatasan akses dan lingkungan :

- Rate limiting pada request forgot password
- Abuse detection terhadap spam reset email
- Keamanan implementasi token di sisi backend
- Delivery dan latency email service

Risiko ini diasumsikan ditangani oleh sistem backend dan infrastruktur, namun perlu diuji secara terpisah pada environment yang memiliki akses log dan konfigurasi server.

## Dampak Bisnis Jika Risiko Lolos ke Produksi

Jika salah satu risiko di atas tidak terdeteksi :

- Potensi pengambilalihan akun meningkat
- Komplain user dan eskalasi ke tim keamanan
- Kerusakan reputasi dan hilangnya kepercayaan
- Biaya operasional meningkat akibat support dan investigasi

Oleh karena itu, Password Recovery diperlakukan sebagai critical flow dan menjadi prioritas utama dalam pengujian fungsional dan keamanan dasar.
