# Reflection
## Commit 1: 
- Pada commit 1 ini, hal yang dilakukan kode adalah server yang menerima request dari user dan membacanya. Alurnya request masuk melalui TCP di Main kemudian dilanjutkan ke handle_connection yang membaca buffer dari main dan mengubahnya ke result buffer, berupa http_request yang ditampilkan di terminal.
- Hal yang saya pelajari adalah bagaimana HTTP berjalan di atas TCP, yang dapat kita lihat request harus masuk melalui TCP terlebih dahulu, dan server membaca isi request kemudian memberikan response ke user. 

## Commit 2:
![Commit 2 screen capture](/assets/images/commit2.png)
- Pada commit ini, saya baru paham setelah server menerima request, server harus memberi tahu request berhasil, melalui 200 OK. Kemudian, server membaca file hello.html sebagai string, menghitung panjangnya, dan menyusun HTTP response yang lengkap. Terakhir, response tersebut dikirim melalui TCP ke browser.
## Commit 3:
![Commit 3 screen capture](/assets/images/commit3.png)
- Pada commit ini, saya belajar bagaimana server memberi response berdasarkan pada request header yang diterimanya. Server akan melakukan pnegecekan pada request line (GET /HTTP/1.1). Jika request sesuai, server akan memberikan status 200 dan menampilkan halaman yang valid, yaitu hello.html. Jika tidak sesuai, server memberikan status 404 NOT FOUND dan menampilkan halaman yang tidak valid, yaitu 404.html.
- Refactoring perlu dilakukan karena sebelumnya terdapat redudansi kode di bagian if-else yang melanggar konsep DRY. Jika nantinya kita ingin menambah endpoint baru, kita perlu menduplikasi kode yang sama secara terus-menerus.
## Commit 4:
- Commit 4 ini menunjukkan pada saya bagaiamana bagaimana server single-threaded berjalan. Saat mengakses 2 window, dengan /sleep terlebih dahulu, window kedua akan load sampai window pertama selesai selama 10 detik. Hal ini akan menimbulkan masalah saat banyak orang yang mengakses /sleep karena semuanya saling menunggu satu sama lain. Oleh karenanya, kita perlu menerapkan multithread supaya tiap request berjalan dengan concurrent dan tidak akan memperlambat user ketika mengakses /sleep secara bersamaan.
## Commit 5:
- ThreadPool bekerja dengan membuat worker thread yang aktif saat kita run program. Tiap worker tersebut akan menunggu job yang nantinya dikirimkan. Ketika server menerima request, request tidak langsung diproses oleh main thread, tapi dikirim sebagai job baru ke ThreadPool dengan execute(). Salah satu worker akan menerima dan menjalankan job tersebut secara paralel. Selain itu, di kode ini, mpsc bekerja sebagai alat komunikasi antarthread, lalu Arc dan Mutex digunakan supaya banyak thread dapat berbagi akses ke receiver dengan aman.
## Bonus:
- Build sekarang dapat menghandle error jika size == 0, yang mana lebih baik dibanding new sebelumnya yang menghentikan program.