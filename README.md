# UTS_pemrograman-sms-4
Laporan Eksperimen UTS Pemrograman Web
Topik: Keamanan Web (Cross-Site Scripting / XSS)

Identitas Mahasiswa

Nama: Mochammad Hafilla Dasuki

NIM: 312410375

Mata Kuliah: Pemrograman Web

Tautan Publikasi Tugas

Tautan Artikel Medium: https://medium.com/@hafilladasuki/membongkar-celah-keamanan-xss-seberapa-bahaya-fitur-input-di-website-kita-a9cdc6948f52

Skor Pengecekan Plagiasi: <img width="929" height="1021" alt="Screenshot 2026-04-29 143605" src="https://github.com/user-attachments/assets/c33da38d-31c4-4204-b1de-d9d80b518f66" />


1. Deskripsi Eksperimen
Eksperimen ini dilakukan untuk mendemonstrasikan secara langsung cara kerja kerentanan keamanan web bernama Cross-Site Scripting (XSS) beserta langkah-langkah pencegahannya (mitigasi). Eksperimen dikembangkan menggunakan bahasa pemrograman PHP murni di lingkungan server lokal (XAMPP). Terdapat dua skenario pengujian yang dilakukan, yaitu Reflected XSS pada fitur pencarian dan Stored XSS pada fitur buku tamu.

2. Skenario Eksperimen dan Hasil

A. Eksperimen 1: Reflected XSS (Fitur Pencarian)
Pada tahap ini, dibuat sebuah fitur kotak pencarian (search box) yang menerima input dari pengguna dan langsung menampilkannya kembali ke layar dokumen HTML tanpa adanya proses filterisasi. Ketika script JavaScript berbahaya (seperti eksekusi pop-up alert) dimasukkan ke dalam kotak pencarian, browser langsung mengeksekusi script tersebut. Hal ini membuktikan bahwa peretas dapat menyisipkan script jahat melalui URL atau input form untuk menyerang browser pengunjung.

B. Eksperimen 2: Stored XSS (Fitur Buku Tamu)
Pada skenario kedua, dibuat sebuah fitur komentar (buku tamu) di mana input pengguna disimpan secara permanen di dalam server menggunakan media file text. Saat script berbahaya dikirimkan melalui form komentar, script tersebut berhasil tersimpan di server. Akibatnya, setiap kali halaman buku tamu tersebut dimuat ulang oleh siapa pun, script jahat tersebut akan tereksekusi secara otomatis. Ini menunjukkan tingkat ancaman yang lebih fatal, karena serangan terjadi secara pasif kepada semua pengunjung halaman tersebut.

3. Langkah Mitigasi (Pencegahan)
Dari kedua skenario serangan di atas, kelemahan utama sistem terletak pada ketiadaan sanitasi data sebelum input ditampilkan ke layar. Untuk mencegah serangan XSS, diterapkan teknik filterisasi menggunakan fungsi bawaan PHP, yaitu htmlspecialchars().

Fungsi ini bertugas mengonversi karakter-karakter khusus (seperti < dan >) menjadi entitas HTML. Setelah mitigasi ini diimplementasikan, script jahat yang dimasukkan kembali ke dalam form pencarian maupun buku tamu tidak lagi dieksekusi oleh browser, melainkan hanya ditampilkan sebagai teks biasa.

4. Kesimpulan
Eksperimen ini membuktikan prinsip dasar keamanan web bahwa pengembang tidak boleh pernah mempercayai input dari pengguna (Never Trust User Input). Melakukan sanitasi dan filterisasi terhadap setiap data yang masuk dan keluar dari sistem adalah langkah esensial untuk mencegah kerentanan fatal seperti XSS.


