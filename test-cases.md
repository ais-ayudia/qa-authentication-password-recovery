# Test Cases – Password Recovery

Semua test case di bawah ini merupakan turunan dari:
TS-01 – User dapat memulihkan akses akun melalui fitur Forgot Password secara aman dan dapat digunakan

| TC ID | Scenario Ref | Description | Expected Result |
|------|--------------|-------------|-----------------|
| TC-01 | TS-01 | Reset password menggunakan email terdaftar | User berhasil login dengan password baru, password lama tidak valid |
| TC-02 | TS-01 | Forgot password dengan email tidak terdaftar | Sistem menampilkan pesan umum tanpa mengonfirmasi keberadaan akun |
| TC-03 | TS-01 | Submit form dengan email kosong atau format tidak valid | Validasi muncul, request tidak diproses |
| TC-04 | TS-01 | Mengakses link reset yang sudah kadaluarsa | User mendapat pesan jelas dan diarahkan untuk request ulang |
| TC-05 | TS-01 | Password baru tidak memenuhi policy | Sistem menolak dan menampilkan aturan password |
| TC-06 | TS-01 | Menggunakan kembali password lama | Sistem menolak reuse password |
| TC-07 | TS-01 | Submit reset dengan password kurang dari 8 karakter | Validation error muncul |
| TC-08 | TS-01 | User submit email dengan huruf besar/kecil berbeda | Sistem tetap mengenali email secara case-insensitive |
| TC-09 | TS-01 | Password mengandung kombinasi huruf besar, kecil, angka, simbol sesuai policy | Diterima tanpa false rejection |
| TC-10 | TS-01 | User berhasil reset password, lalu mencoba akses halaman reset melalui history browser | Form tidak dapat digunakan ulang atau tampil pesan sesuai state |
| TC-11 | TS-01 | Submit forgot password dengan format email valid secara struktur tapi domain tidak wajar | Sistem tetap memberikan pesan generik tanpa error teknis |
| TC-12 | TS-01 | Setelah reset berhasil, cek apakah user tetap bisa mengakses halaman yang sebelumnya membutuhkan login tanpa re-auth | Sistem meminta login ulang jika session invalidated |
| TC-13 | TS-01 | User berhasil reset password, lalu logout, lalu login ulang dengan password baru | Login berhasil dan tidak terjadi loop ke halaman reset |
| TC-14 | TS-01 | User request reset dua kali berturut-turut | Token pertama invalid |
| TC-15 | TS-01 | User klik reset link setelah password sudah berhasil diubah | Link tidak dapat digunakan ulang |
| TC-16 | TS-01 | Response time untuk email valid dan tidak valid dibandingkan | Tidak ada perbedaan signifikan yang bisa digunakan untuk enumeration |
