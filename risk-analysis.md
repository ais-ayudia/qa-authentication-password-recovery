## Risk Analysis – Password Recovery

Fitur Password Recovery merupakan salah satu alur dengan **risiko tertinggi** dalam sistem autentikasi karena menyentuh akses akun tanpa kredensial utama. Kegagalan pada alur ini berdampak langsung pada keamanan akun, kepercayaan user, dan beban operasional.

## Risiko Utama yang Diidentifikasi

1. Account Enumeration
Jika sistem membedakan respons antara email terdaftar dan tidak terdaftar, penyerang dapat mengidentifikasi akun yang valid.

Dampak :

- Penyerang dapat mengumpulkan daftar akun aktif
- Meningkatkan risiko phishing dan brute-force
- Menurunkan kepercayaan user terhadap keamanan platform

Mitigasi yang diverifikasi melalui TC-02 :

Sistem wajib menampilkan pesan generik tanpa mengonfirmasi keberadaan akun

2. Token Reset yang Tidak Aman atau Tidak Kedaluwarsa
Link reset password yang dapat digunakan ulang atau tidak memiliki masa berlaku membuka peluang account takeover.

Dampak :

- Akses ilegal ke akun user
- Potensi penyalahgunaan data pribadi
- Insiden keamanan yang memerlukan investigasi dan komunikasi publik

Mitigasi yang diverifikasi melalui TC-04 :

- Token reset harus memiliki expiry dan ditolak setelah kedaluwarsa
- User diarahkan untuk melakukan request ulang secara eksplisit

3. Password Policy Lemah atau Tidak Ditegakkan
Jika sistem menerima password yang lemah atau mengizinkan reuse password lama, maka reset password tidak meningkatkan keamanan akun.

Dampak :

- Akun tetap rentan meskipun user melakukan reset
- False sense of security bagi user
- Pelanggaran kebijakan keamanan internal

Mitigasi yang diverifikasi melalui TC-05 dan TC-06 :

- Sistem menolak password yang tidak memenuhi policy
- Sistem menolak penggunaan ulang password sebelumnya

4. User Confusion pada Kondisi Gagal
Alur forgot password sering dilakukan dalam kondisi user frustrasi. Pesan error yang tidak jelas atau ambigu meningkatkan churn dan tiket ke customer support.

Dampak :

- User gagal memulihkan akun
- Peningkatan beban customer support
- Pengalaman pengguna yang buruk pada momen kritis

Mitigasi yang diverifikasi melalui TC-03 dan TC-04 :

- Validasi input ditampilkan secara jelas
- Feedback eksplisit pada kondisi link kadaluarsa

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
