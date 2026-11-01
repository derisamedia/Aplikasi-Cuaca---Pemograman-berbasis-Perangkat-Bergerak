aplikasi **Prakiraan Cuaca Jakarta** yang dibangun menggunakan **Ionic Vue 3** dan **Vite**.
**Muhamad Deri Sahertian**
**053561396**

Alur aplikasi ini dimulai dari file `main.js` dan `router` yang langsung mengarahkan halaman utama ke komponen `HomePage.vue`.

Saat halaman pertama kali dibuka, fungsi `ambilDataCuaca` secara otomatis memanggil **API Open-Meteo** sesuai koordinat kota Jakarta, yaitu latitude `-6.2` dan longitude `106.8`. Data waktu dan suhu per jam yang diterima dari API kemudian digabungkan menggunakan fungsi `map` dan disimpan ke dalam variabel reaktif `daftarCuaca`.

Pada bagian tampilan, aplikasi ini memiliki tiga bagian utama:
1. **Pertama, Kartu Utama (Hero Card) dengan Tema Dinamis.** Tampilan aplikasi otomatis menyesuaikan waktu menjadi mode **Siang** atau **Malam** lengkap dengan ilustrasi siluet gedung dan Monas, serta menampilkan suhu pada jam saat ini. Mode tampilan ini juga bisa diubah secara manual dengan menekan tombol waktu di sebelahnya.
2. **Kedua, Filter Jumlah Data.** Menggunakan komponen `ion-segment`, kita bisa memilih untuk menampilkan 10 data pertama, 24 jam pertama, atau seluruh data cuaca yang berjumlah 168 data.
3. **Ketiga, Tabel Prakiraan Cuaca.** Tabel ini menampilkan waktu pengukuran, format tanggal dan jam yang sudah dirapikan, nilai suhu dalam derajat Celcius, serta keterangan indikator suhu yaitu **Sejuk**, **Hangat**, atau **Panas** yang warnanya otomatis menyesuaikan tingkat suhu.