# StrukturData-Q1-2501010004-DewaGedeAgungDwiAnggaSuputra-A

## 1 Karakteristik Memori dan Akses Data
> Jelaskan mengapa operasi akses elemen pada Array dapat dilakukan dalam waktu konstan
O(1), sedangkan pada Singly Linked List membutuhkan waktu linear O(n). Hubungkan
jawaban Anda dengan konsep alamat memori (kontinu vs non-kontinu).

Array dapat mengakses elemen dalam waktu konstan O(1) karena elemen-elemennya disimpan di dalam memori yang bersifat kontinu (bersebelahan). Dengan struktur ini, komputer dapat menghitung langsung alamat suatu elemen menggunakan rumus berdasarkan alamat awal array dan indeks elemen yang diinginkan. Karena alamat setiap elemen bisa ditentukan secara matematis tanpa perlu menelusuri elemen lain, maka proses akses menjadi sangat cepat dan tidak bergantung pada ukuran data.

Sebaliknya, Singly Linked List membutuhkan waktu linear O(n) untuk mengakses elemen karena setiap node pada struktur ini tidak disimpan secara berurutan di memori (non-kontinu). Setiap node hanya memiliki data dan pointer yang menunjuk ke node berikutnya, sehingga untuk mencapai elemen tertentu, sistem harus memulai dari node pertama (head) dan mengikuti setiap pointer satu per satu sampai menemukan elemen yang dituju. Proses ini membuat waktu akses bergantung pada posisi elemen dalam list, sehingga semakin jauh posisi elemen, semakin lama waktu yang dibutuhkan.

---

## 2 Analisis Efisiensi Operasi Manipulasi
> Dalam kondisi apa sebuah Linked List lebih diunggulkan dibandingkan Array untuk operasi penyisipan (insertion) dan penghapusan (deletion) data? Berikan alasan teoritisnya.

Linked List lebih diunggulkan dibandingkan Array dalam operasi penyisipan (insertion) dan penghapusan (deletion) terutama ketika operasi dilakukan di posisi tengah atau awal struktur data, serta ketika ukuran data sering berubah secara dinamis.

Pada Array, elemen disimpan secara kontinu di memori. Hal ini menyebabkan jika terjadi penyisipan atau penghapusan di posisi tertentu, maka elemen-elemen setelahnya harus digeser (shift) untuk menjaga keteraturan indeks. Proses pergeseran ini membutuhkan waktu O(n), sehingga menjadi tidak efisien untuk data yang besar atau sering berubah. Sedangkan pada Singly Linked List, elemen disimpan secara non-kontinu dan dihubungkan menggunakan pointer. Pada operasi penyisipan dan penghapusan, tidak diperlukan pergeseran elemen, melainkan hanya mengubah pointer dari node yang terkait. Jika posisi node yang dituju sudah diketahui (misalnya setelah proses traversal), maka proses penyisipan dan penghapusan dapat dilakukan dalam waktu O(1).

---

## 3 Konsep Doubly Linked List
> Jelaskan struktur anatomi dari sebuah node pada Doubly Linked List. Apa dampak keberadaan pointer tambahan tersebut terhadap penggunaan memori serta fleksibilitas penelusuran dibandingkan dengan Singly Linked List?

Dalam Doubly Linked List, setiap node memiliki tiga komponen utama : 
1. Data
2. Pointer ke node berikutnya (next)
3. Pointer ke node sebelumnya (prev)

Jadi struktur ini memungkinkan setiap node terhubung dua arah, yaitu ke depan dan ke belakang.

Keberadaan pointer tambahan (prev) memberikan dampak pada penggunaan memori karena setiap node membutuhkan ruang penyimpanan lebih besar dibandingkan Singly Linked List yang hanya memiliki satu pointer (next). Dengan kata lain, Doubly Linked List memiliki overhead memori yang lebih tinggi karena harus menyimpan satu pointer tambahan di setiap node.

Tetapi, pointer tambahan ini memberikan keuntungan signifikan dalam hal fleksibilitas penelusuran. Jika pada Singly Linked List penelusuran hanya bisa dilakukan satu arah dari head ke tail, maka pada Doubly Linked List penelusuran bisa dilakukan dua arah, baik maju maupun mundur. Hal ini juga membuat operasi seperti penghapusan node menjadi lebih efisien, karena node sebelumnya dapat langsung diakses tanpa harus melakukan traversal ulang dari head.

--- 

## 4 Mekanisme Circular Linked List
> Apa yang membedakan Circular Linked List dari Linked List biasa secara teoritis? Sebutkan satu contoh skenario penggunaan (use case) di mana struktur melingkar ini lebih
efektif digunakan.

Secara teoritis, Circular Linked List berbeda dari Linked List biasa (Singly maupun Doubly Linked List) pada struktur ujungnya. Pada Linked List biasa, node terakhir (tail) menunjuk ke NULL yang menandakan akhir list. Sedangkan pada Circular Linked List, node terakhir tidak menunjuk ke NULL, tetapi kembali menunjuk ke node pertama (head), sehingga membentuk struktur melingkar tanpa ujung.

Contoh use case dari Circular Linked List adalah pada sistem playlist musik yang diputar berulang (repeat mode).

Dalam aplikasi pemutar musik, lagu-lagu disimpan dalam urutan tertentu. Dengan menggunakan Circular Linked List, lagu terakhir tidak menunjuk ke NULL, tetapi kembali ke lagu pertama. Hal ini memungkinkan sistem untuk terus memutar lagu secara otomatis dari awal setelah lagu terakhir selesai, tanpa perlu melakukan reset atau traversal ulang secara manual.

--- 

## 5 Array Dinamis di Python
> Python list secara internal diimplementasikan sebagai Dynamic Array. Jelaskan mekanisme yang terjadi ”di balik layar” ketika sebuah Dynamic Array kehabisan kapasitas saat
melakukan operasi append.

Python list yang diimplementasikan sebagai Dynamic Array memiliki kapasitas internal yang terbatas. Ketika melakukan operasi append, elemen akan dimasukkan ke ruang memori yang masih tersedia. Namun, jika kapasitas tersebut sudah penuh, maka terjadi proses yang disebut resizing (pengubahan ukuran array) di balik layar.

Saat kapasitas penuh, Python tidak hanya menambah satu slot baru, tetapi akan membuat array baru dengan kapasitas yang lebih besar (biasanya sekitar 1.25x hingga 2x dari ukuran sebelumnya, tergantung implementasi). Setelah itu, seluruh elemen dari array lama akan disalin (copy) ke array baru yang lebih besar. Setelah proses penyalinan selesai, elemen baru yang di-append akan dimasukkan ke array tersebut, dan array lama akan dilepaskan dari memori (garbage collected jika tidak digunakan lagi).

Proses ini membutuhkan waktu O(n) saat resizing terjadi karena harus menyalin seluruh elemen, tetapi karena resizing tidak terjadi setiap kali append, maka secara rata-rata (amortized), operasi append pada Python list tetap memiliki kompleksitas waktu O(1).
