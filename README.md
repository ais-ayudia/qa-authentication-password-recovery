# qa-authentication-password-recovery
Repository ini berisi dokumentasi dan artefak pengujian untuk alur Forgot Password / Password Recovery pada sistem web dengan autentikasi user. Fokus pengujian adalah memastikan pengguna dapat memulihkan akses akun secara reliable, aman, dan tidak membingungkan, terutama dalam kondisi user sudah kehilangan kredensial login.

✔ Scope of Testing 
Pengujian difokuskan pada:
- Alur end-to-end lupa password dari sudut pandang pengguna (UI & flow)
- Validasi input dan pesan error yang ditampilkan
- Konsistensi status akun setelah password berhasil diubah

Pengujian tidak mencakup:
- Implementasi enkripsi password di backend
- Konfigurasi SMTP / email deliverability tingkat server
- Rate limiting dan brute force protection tingkat infrastruktur

✔ Business Risks
Kegagalan pada fitur Forgot Password berpotensi menyebabkan:
- User tidak dapat mengakses akun yang mengakibatkan churn & kehilangan kepercayaan
- Lonjakan tiket customer support
- Kebocoran informasi akun (email enumeration)
- Risiko account takeover jika link reset tidak aman
Oleh karena itu, skenario ini dikategorikan sebagai high-risk, high-impact flow.

✔ Assumptions & Constraints
Asumsi pengujian:
- User sudah memiliki akun terdaftar
- Email user dapat menerima pesan masuk
- Sistem dalam kondisi normal (tidak maintenance)
- Pengujian dilakukan pada browser modern (Chrome/Firefox)

Batasan Masalah:
- Tidak ada akses ke database atau log backend
- Pengujian dilakukan sebagai black-box testing

✔ Test Environment
- Browser: Firefox 147.0.3
- OS: Windows 10
- Testing type: Black-box
- Backend: Simulated (dummy system)
