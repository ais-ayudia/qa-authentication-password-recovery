# qa-authentication-password-recovery
Repository ini berisi dokumentasi dan artefak pengujian untuk alur Forgot Password / Password Recovery pada sistem web dengan autentikasi user. Fokus pengujian adalah memastikan pengguna dapat memulihkan akses akun secara reliable, aman, dan tidak membingungkan, terutama dalam kondisi user sudah kehilangan kredensial login.

✔ Scope of Testing 
Pengujian difokuskan pada:
- Alur end-to-end lupa password recovery
- Validasi input dan pesan error yang ditampilkan
- Konsistensi status akun setelah password berhasil diubah
- Validasi token reset
- Pengujian keamanan dasar pada boundary autentikasi

✔ Testing Approach
- Black-box testing
- Functional & negative testing
- Security-aware scenario validation
- Dokumentasi API dan UI flow

✔ Business Risks
Kegagalan pada fitur Forgot Password berpotensi menyebabkan:
- User tidak dapat mengakses akun yang mengakibatkan churn & kehilangan kepercayaan
- Lonjakan tiket customer support
- Kebocoran informasi akun (email enumeration)
- Risiko account takeover jika link reset tidak aman
Oleh karena itu, skenario ini dikategorikan sebagai high-risk, high-impact flow.

✔ Automation
Automation dilakukan menggunakan Postman Collection.

Lokasi :
/automation/postman

Endpoint yang diautomasi :
- POST /auth/forgot-password
- POST /auth/reset-password
- POST /auth/login

Coverage automation mencakup :
- Valid & invalid forgot password request
- Token validation
- Token reuse rejection
- Login setelah reset berhasil

Untuk menjalankan automation melalui CLI :

newman run Password-Recovery.postman_collection.json -e Password-Recovery.environment.json

✔ Repository Structure
docs/
    test_plan.md
    risk_analysis.md
    bug_report.md
    /test-documentation
    /api-testing
automation/postman
    password_recovery.postman_collection.json
    password_recovery.environment.json
