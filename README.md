Latihan 1
Eksperimen 1
sessionTest: [hilang/ada?] ada
persistentTest: [hilang/ada?] ada

Eksperimen 2
|Halaman                    |cookieRoot|cookieAdmin|
|/index.html                |Muncul    |Tdk Muncul |
|/admin/index.html          |Muncul    |Muncul     |
|/admin/dashboard/index.html|Muncul    |Muncul     |

Cookie dengan Path=/admin akan dikirim ke:
- /admin ✓ atau ✗? _✓_
- /admin/dashboard ✓ atau ✗? _✓_
- /profile ✓ atau ✗? _✗_
- / ✓ atau ✗? _✗_

Eksperimen 3
Cookie Secure tersimpan di localhost HTTP? __Ya__ (Ya/Tidak)
Mengapa bisa tersimpan? Di localhost, Secure cookie bisa tersimpan karena browser exception. Di production HTTP, cookie akan ditolak - harus pakai HTTPS.

Pertanyaan Refleksi
Jawab pertanyaan berikut di bagian "Catatan Eksperimen":
1.Mengapa session cookie (tanpa Max-Age) berguna untuk login?
Jwb:Session cookie berguna untuk login karena cookie ini menyimpan session ID sementara yang digunakan server untuk mengenali pengguna setelah berhasil login. Cookie ini akan tetap aktif selama browser masih dibuka, sehingga pengguna tidak perlu login ulang setiap membuka halaman selama sesi masih berjalan.

2.Jika kamu membuat aplikasi e-commerce, atribut apa yang akan kamu gunakan untuk cookie session ID? Jelaskan alasannya.
Jwb:
-HttpOnly → agar cookie tidak bisa diakses oleh JavaScript, sehingga mengurangi risiko pencurian session    melalui
            serangan XSS.
-Secure → agar cookie hanya dikirim melalui koneksi HTTPS, sehingga lebih aman dari penyadapan jaringan.
-Path → supaya cookie bisa digunakan di seluruh halaman aplikasi.
-Max-Age → bisa dipakai jika ingin fitur “remember me”, tetapi jika tidak, lebih aman menggunakan session cookie.

3.Apa risiko keamanan jika cookie session TIDAK menggunakan HttpOnly?
Jwb:Jika cookie session tidak menggunakan HttpOnly, maka cookie bisa dibaca oleh JavaScript. Jika website terkena serangan XSS, penyerang dapat mencuri session ID dari cookie dan mengambil alih akun pengguna (session hijacking).

4.Kapan sebaiknya menggunakan Expires vs Max-Age?
Jwb:Expires sebaiknya digunakan jika ingin menentukan waktu kadaluarsa berdasarkan tanggal dan jam tertentu.
Max-Age sebaiknya digunakan jika ingin menentukan cookie kadaluarsa berdasarkan durasi (misalnya 3600 detik).
Biasanya Max-Age lebih direkomendasikan karena lebih konsisten dan tidak bergantung pada jam sistem.

5.Apa yang terjadi jika Domain cookie di-set ke `.example.com`?
Jwb:Jika Domain cookie diset ke .example.com, maka cookie akan dikirim ke semua subdomain dari example.com, sehingga pengguna bisa tetap dikenali di berbagai subdomain.
