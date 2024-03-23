## COMMIT 1
### **Apa yang `handle_connection` lakukan?**
1. Fungsi ini menerima referensi mutable ke `TcpStream` sebagai argumennya. Selanjutnya, ia membuat `BufReader` yang membungkus aliran TCP yang diberikan. Hal ini membantu dalam melakukan pembacaan yang telah di-*buffer* dari aliran dengan efisien.
2. `BufReader` membantu dalam pembacaan yang telah di-*buffer* dari aliran TCP, memastikan efisiensi dalam pengambilan data.
3. Selanjutnya, fungsi membaca baris-baris dari `BufReader` yang telah di-buffer sampai mencapai baris kosong. Baris kosong ini merupakan penanda akhir dari *header* permintaan HTTP, yang umumnya terjadi dalam format permintaan HTTP. Header biasanya diikuti oleh baris kosong sebelum badan pesan.
4. Setelah membaca baris-baris tersebut, fungsi mengumpulkannya menjadi sebuah vektor. Vektor ini merepresentasikan permintaan HTTP yang telah dibuat oleh klien.
5. Terakhir, `handle_connection` mencetak permintaan HTTP yang telah terkumpul untuk inspeksi lebih lanjut. Ini memungkinkan pengguna untuk melihat detail permintaan yang diterima oleh server untuk tujuan *debugging* atau analisis.

Jadi, `handle_connection` membaca aliran TCP masuk secara baris per-baris sampai menemukan baris kosong yang menandakan akhir dari header permintaan HTTP. Lalu, baris-baris yang telah terkumpul tersebut dicetak sebagai permintaan HTTP untuk inspeksi lebih lanjut.