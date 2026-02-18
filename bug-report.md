# 🐞 Bug Report

## Bug ID
BR-PR-014

## Title
Token reset sebelumnya tetap valid setelah permintaan reset password kedua

## Related Test Case
TC-14 – Permintaan reset berulang hanya boleh mengaktifkan token terakhir

## Severity
### Critical

## Priority
High

## Environment
- Browser: Firefox 147.0.3
- OS: Windows 10
- Tipe Pengujian: Black-box
- Backend: Simulasi / Dummy system

## Description

Sistem mengizinkan lebih dari satu token reset password tetap aktif secara bersamaan ketika user melakukan beberapa kali permintaan forgot password dalam waktu berdekatan.

Token pertama tetap dapat digunakan meskipun token kedua sudah diterbitkan dan digunakan untuk mengganti password.

Perilaku ini menunjukkan tidak adanya mekanisme invalidasi token sebelumnya saat token baru dibuat atau setelah password berhasil diperbarui.

## Steps to Reproduce
1. Akses halaman Forgot Password.
2. Masukkan email terdaftar dan submit.
3. Terima email pertama berisi link reset (jangan gunakan terlebih dahulu).
4. Lakukan permintaan forgot password kedua dengan email yang sama.
5. Gunakan link reset kedua untuk mengganti password.
6. Setelah berhasil, coba gunakan kembali link reset pertama.

## Actual Result
Link reset pertama tetap dapat digunakan untuk mengubah password kembali.

## Expected Result
- Hanya token reset terbaru yang valid.
- Semua token sebelumnya harus otomatis dinonaktifkan saat token baru dibuat.
- Setelah password berhasil diubah, seluruh token reset yang masih aktif harus menjadi tidak valid.

## Impact
- Memperluas attack window apabila salah satu link reset bocor.
- Meningkatkan risiko token replay.
- Berpotensi menyebabkan account takeover dalam kondisi tertentu.
- Melanggar prinsip secure token lifecycle management.
