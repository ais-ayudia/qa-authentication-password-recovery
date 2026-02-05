# Test Scenarios – Password Recovery

## TS-01: User dapat memulihkan akses akun melalui fitur Forgot Password secara aman dan dapat digunakan

Scenario ini memvalidasi bahwa pengguna yang kehilangan kredensial login
dapat memulihkan akses akun tanpa kebingungan, tanpa kebocoran informasi,
dan tanpa membuka celah keamanan.

Scenario ini penting karena:
- User berada dalam kondisi frustrasi (lost access)
- Kegagalan berdampak langsung pada churn dan beban customer support
- Alur ini berpotensi dieksploitasi untuk account takeover jika tidak aman

Fokus utama scenario:
- Keberhasilan end-to-end password reset
- Perlindungan terhadap penyalahgunaan dan informasi sensitif
- Kejelasan feedback kepada user di setiap kondisi gagal
