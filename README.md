# Reflection
## Commit 1: 
- Pada commit 1 ini, hal yang dilakukan kode adalah server yang menerima request dari user dan membacanya. Alurnya request masuk melalui TCP di Main kemudian dilanjutkan ke handle_connection yang membaca buffer dari main dan mengubahnya ke result buffer, berupa http_request yang ditampilkan di terminal.
- Hal yang saya pelajari adalah bagaimana HTTP berjalan di atas TCP, yang dapat kita lihat request harus masuk melalui TCP terlebih dahulu, dan server membaca isi request kemudian memberikan response ke user. 

## Commit 2:
![Commit 2 screen capture](/assets/images/commit2.png)
- Pada commit ini, saya baru paham setelah server menerima request, server harus memberi tahu request berhasil, melalui 200 OK. Kemudian, server membaca file hello.html sebagai string, menghitung panjangnya, dan menyusun HTTP response yang lengkap. Terakhir, response tersebut dikirim melalui TCP ke browser.
## Commit 3:
## Commit 4:
## Commit 5: