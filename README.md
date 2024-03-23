**Nama: Vina Myrnauli Abigail Siallagan** <br>
**NPM: 2206825776** <br>
**Kelas: Pemrograman Lanjut - A** <br>

## COMMIT 1
### **Apa yang `handle_connection` lakukan?**
1. Fungsi ini menerima referensi mutable ke `TcpStream` sebagai argumennya. Selanjutnya, ia membuat `BufReader` yang membungkus aliran TCP yang diberikan. Hal ini membantu dalam melakukan pembacaan yang telah di-*buffer* dari aliran dengan efisien.
2. `BufReader` membantu dalam pembacaan yang telah di-*buffer* dari aliran TCP, memastikan efisiensi dalam pengambilan data.
3. Selanjutnya, fungsi membaca baris-baris dari `BufReader` yang telah di-buffer sampai mencapai baris kosong. Baris kosong ini merupakan penanda akhir dari *header* permintaan HTTP, yang umumnya terjadi dalam format permintaan HTTP. Header biasanya diikuti oleh baris kosong sebelum badan pesan.
4. Setelah membaca baris-baris tersebut, fungsi mengumpulkannya menjadi sebuah vektor. Vektor ini merepresentasikan permintaan HTTP yang telah dibuat oleh klien.
5. Terakhir, `handle_connection` mencetak permintaan HTTP yang telah terkumpul untuk inspeksi lebih lanjut. Ini memungkinkan pengguna untuk melihat detail permintaan yang diterima oleh server untuk tujuan *debugging* atau analisis.

Jadi, `handle_connection` membaca aliran TCP masuk secara baris per-baris sampai menemukan baris kosong yang menandakan akhir dari header permintaan HTTP. Lalu, baris-baris yang telah terkumpul tersebut dicetak sebagai permintaan HTTP untuk inspeksi lebih lanjut.
<p align="center">
    <img src="images/reflection1.jpg"/>
</p>

## COMMIT 2
### **Apa yang dilakukan oleh barisan tambahan kode `handle_connection`?**
1. Mengonfigurasi status_line yang menunjukkan bahwa respons HTTP adalah `200 OK`, yang artinya permintaan berhasil. 
2. Membaca isi dari file bernama `hello.html` menjadi sebuah string menggunakan `fs::read_to_string()`. Asumsinya bahwa ada file bernama `hello.html` dalam direktori yang sama dengan program yang berjalan. 
3. Menghitung panjang string isi file. 
4. Mengatur format respons HTTP, termasuk baris status, panjang konten, dan isi dari file hello.html. 
5. Menulis respons kembali ke aliran TCP, mengirimkannya kepada klien menggunakan `write_all()`.

Jadi, fungsi `handle_connection` yang dimodifikasi membaca konten dari file `hello.html`, membuat respons HTTP dengan status 200 OK, dan mengirimkannya kembali kepada klien melalui aliran TCP.
<p align="center">
    <img src="images/reflection2.jpg"/>
</p>