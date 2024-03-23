## COMMIT 1
### **Apa yang `handle_connection` lakukan?**
1. Fungsi ini menerima referensi *mutable* ke `TcpStream` sebagai argumennya. membuat `BufReader` yang membungkus aliran TCP yang diberikan. 
2. Membantu dalam pembacaan yang telah di-*buffer* dari aliran dengan efisien.
3. Membaca baris-baris dari pembaca yang telah di-*buffer* (`BufReader`) sampai mencapai baris kosong. Ini adalah format umum dari permintaan HTTP, dengan *header* diikuti oleh baris kosong.
4. Mengumpulkan baris-baris tersebut menjadi vektor, yang mewakili permintaan HTTP.
5. Mencetak permintaan HTTP untuk inspeksi. `handle_connection` membaca aliran TCP masuk baris per-baris sampai menemukan baris kosong yang menandakan akhir dari header permintaan HTTP. Lalu, mencetak baris-baris yang terkumpul sebagai permintaan HTTP.