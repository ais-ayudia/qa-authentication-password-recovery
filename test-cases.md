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
| TC-08 | TS-01 | Email field diisi script injection | Input disanitasi / ditolak |
