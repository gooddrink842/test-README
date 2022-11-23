# counter_7

Pemrograman Berbasis Platform (CSGE602022) - diselenggarakan oleh Fakultas Ilmu Komputer Universitas Indonesia, Semester Ganjil 2022/2023

Muhammad Nabiel Andityo Purnomo - 2106750465

## Tugas 9 - Integrasi Web Service pada Flutter

### Apakah bisa kita melakukan pengambilan data JSON tanpa membuat model terlebih dahulu? Jika iya, apakah hal tersebut lebih baik daripada membuat model sebelum melakukan pengambilan data JSON?

Jawaban singkatnya adalah bisa. Kita bisa saja mengambil data JSON tanpa membuat modelnya terlebih dahulu salah satunya dengan menggunakan 
*dynamic map*. Namun hal ini tidak membuat pengolahan data menjadi mudah, tidak efisien, dan rawan terjadi kesalahan, karena kita harus memproses respon 
JSON secara manual setelah menerima respon dari *web service*. Jadi, tidak ada cara yang lebih baik selain membuat model terlebih dahulu 
sebelum mengambil data JSON.

### Sebutkan widget apa saja yang kamu pakai di proyek kali ini dan jelaskan fungsinya.

Pada tugas ini, saya menggunakan widget yang hampir sama pada tugas-tugas sebelumnya. Namun, terdapat beberapa tambahan widget yang
saya gunakan 

1. CheckboxListTile() : *Creates a combination of a list tile and a checkbox.*
2. ListTile() : *Used to populate a ListView in Flutter. A widget that represents a single row of fixed height.*
3. RichText() : *Widget that can display text using several different styles.*
4. GestureDetector() : *A widget that can detect user gestures.*
5. FutureBuilder() : *Creates a widget that builds itself based on the latest snapshot of interaction with a `Future`.*

### Jelaskan mekanisme pengambilan data dari json hingga dapat ditampilkan pada Flutter.

Data diambil menggunakan HTTP dalam fungsi `fetchMyWatchlist` yang memanggil fungsi get oleh instance HTTP. Fungsi mengembalikan daftar objek `MyWatchList`. 
FutureBuilder akan memanggil fungsi dan menunggu responsnya. Saat data diambil, `FutureBuilder` mengembalikan `ListView.builder` yang membangun ListTiles 
berisi data yang dipetakan yang kita dapatkan dari fungsi fetchMyWatchlist.

### Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas.

1. Menambahkan tombol navigasi pada drawer/hamburger untuk ke halaman mywatchlist.<br>
- Dilakukan dengan menambahkan tombol navigasi pada `drawer.dart` dengan widget `ListTile` yang akan mengarahkan ke `MyWatchListPage`<br>
2. Membuat satu file dart yang berisi model mywatchlist.<br>
- Pada step ini, saya menggunakan bantuan dari website QuickType yang akan membuat model berdasarkan data JSON.<br>
3. Menambahkan halaman mywatchlist yang berisi semua watch list yang ada pada endpoint JSON di Django yang telah kamu deploy ke Heroku sebelumnya (Tugas 3). Pada bagian ini, kamu cukup menampilkan judul dari setiap mywatchlist yang ada.<br>
- Dilakukan dengan membuat file `mywatchlist_page.dart` untuk menampilkan watchlist. berdasarkan data yang telah di ambil oleh file `fetch_mywatchlist.dart`  <br>
	- Membuat navigasi dari setiap judul watch list ke halaman detail<br>
	Pada step ini, saya menggunakan widget GestureDetector dan menggunakan properti `onTap` untuk kehalaman detail<br>
4. Menambahkan halaman detail untuk setiap mywatchlist yang ada pada daftar tersebut. Halaman ini menampilkan judul, release date, rating, review, dan status (sudah ditonton/belum).<br>
- Dilakukan dengan membuat file `mywatchlist_detail.dart` yang berfungsi untuk menampilkan halaman detail setiap watchlist.<br>
5. Menambahkan tombol untuk kembali ke daftar mywatchlist<br>
- Dilakukan dengan menambahkan `TextButton` di halaman detail yang akan mengarahkan kembali ke halaman `mywatchlist_page.`<br>

## Tugas 8 - Flutter Form

### Jelaskan perbedaan `Navigator.push` dan `Navigator.pushReplacement`.

Saat mengganti halaman, `Navigator.push` menimpa(stack) halaman baru di atas halaman saat ini, sedangkan `Navigator.pushReplacement` 
mengganti halaman lama dengan halaman baru. Misalnya, ketika kita berada di halaman kedua, ketika gunakan metode `pushReplacement()` 
dan buka halaman ketiga, ketika kita menekan tombol kembali kita akan pergi ke halaman pertama dan melewati halaman kedua.

### Sebutkan widget apa saja yang kamu pakai di proyek kali ini dan jelaskan fungsinya.

- TextFormField() = Widget sebagai TextField berguna untuk input text
- Form : Widget sebagai container form
- Scaffold : Membuat kerangka dalam membuat widget.
- Appbar : Widget default untuk membuat appbar seperti navbar
- Center : Layout widget untuk memposisikan *children* di *center*
- Column : Layout widget untuk tampilan *column*
- Row : Layout widget untuk Tampilan *row*
- Text : Berguna dalam pembuatan teks
- Padding : Widget untuk *wrap children* dengan padding
- Icon : Widget untuk menampilkan *icon* di dalam aplikasi
- IconButton = widget icon yang berfungsi sebagai button
- SizedBox = widget untuk membuat box dengan ukuran yang sesuai
- TextButton = widget sebagai tombol
- InputDatePickerFormField = untuk menerima tanggal yang di-masukkan oleh user
- MyHomePage = widget yang berfungsi sebagai home page awal
- MyDrawer = widget untuk sebagai drawer menu
- MyFormPage = widget untuk menampilkan halaman form

### Sebutkan jenis-jenis event yang ada pada Flutter (contoh: `onPressed`).

onPressed:  Kode dalam event onPressed akan tereksekusi saat sebuah tombol di klik.<br>
onHover:  Kode dalam event ini akan tereksekusi saat mouse bergerak dalam sebuah tombol (tapi tidak di klik)<br> 
onFocusChange:  Kode dalam event ini akan tereksekusi saat fokus berubah.<br> 
onChanged:  Kode dalam event ini akan tereksekusi dalam TextField saat user melakukan insert atau delete sebuah text.<br> 
onTap:  Mirip dengan onPressed. Namun onPressed cenderung hanya untuk button sedangkan onTap untuk gestur apapun.<br> 
onSaved:  Kode dalam event ini akan tereksekusi saat nilai final dari form disimpan melalui FormState.save.<br>

### Jelaskan bagaimana cara kerja `Navigator` dalam "mengganti" halaman dari aplikasi Flutter.

Secara umum, cara kerja Navigator hampir sama dengan Stack. Saat ingin membuka suatu *page*, maka dilakukan push ke dalam
Stack yang berisi halaman tersebut, sehingga item paling atas dari Stack tersebutlah yang akan ditampilkan. Jika ingin kembali
ke *page/route* sebelumnya maka bisa dilakukan dengan `Navigator.pop` untuk menghapus route paling atas dari Stack. Dengan demikian, 
pengguna akan ditujukan ke halaman sebelumnya

### Jelaskan bagaimana cara kamu mengimplementasikan *checklist* di atas.
1. Menambahkan 3 tombol navigasi pada drawer/hamburger, dilakukan dengan menggunakan widget Column yang berisi ListTile dari
setiap halaman, saya menggunakan pushReplacement untuk menghapus dari stack route dan masukan di top stack.
2. Lalu, menambahkan drawer/humberger menu pada setiap halaman (link to drawer.dart)
`drawer: const MyDrawer(),`
3. Membuat class Budget untuk model penyimpanan data
4. Menambahkan halaman baru pada form.dart dengan form yang berisi judul, nominal, tanggal, dan jenis budget yang disusun vertikal.
5. Membuat data untuk menampilkan list budget, membuat method `addDataBudget` untuk iterasi semua data budget.
Setelah itu, ditampilkan dalam halaman `Data Budget`.

## Tugas 7 - Elemen Dasar Flutter

### Jelaskan apa yang dimaksud dengan *stateless widget* dan *stateful widget* dan jelaskan perbedaan dari keduanya.

Secara sederhana Stateless Widget dapat diartikan sebagai Widget yang tidak dapat dirubah atau tidak akan pernah berubah. 
state yang dimaksud, dapat berupa warna, data, dan atau variabel.<br>
Stateful Widget merupakan widget yang interaktif dan dinamis atau dapat berubah. Berbanding terbalik dengan stateless, 
stateful widget dapat mengupdate tampilan, merubah warna, menambah jumlah baris (style) dll. Jadi dapat disimpulkan bahwa 
apapun widget yang dapat berubah maka itulah stateful widget.

### Sebutkan widget apa saja yang kamu pakai di proyek kali ini dan jelaskan fungsinya.

- Scaffold : Membuat kerangka dalam membuat widget.
- Appbar : Widget default untuk membuat appbar seperti navbar
- Center : Layout widget untuk memposisikan *children* di *center*
- Column : Layout widget untuk tampilan *column*
- Row : Layout widget untuk Tampilan *row*
- Text : Berguna dalam pembuatan teks
- Padding : Widget untuk *wrap children* dengan padding
- FloatingActionButton : tombol yang dapat diklik dan terlihat *floating* di layar
- Spacer : Widget untuk menciptakan ruang di antara *children*, berperilaku seperti `flex`

### Apa fungsi dari `setState()`? Jelaskan variabel apa saja yang dapat terdampak dengan fungsi tersebut.

`setState` akan memberitahu *framework* akan perubahan state, *framework* akan merespon dengan mengupdate *state* yang berupa 
*framework* melakukan *build* ulang pada objek tersebut (*re-render*) pada UI aplikasi. Variabel yang dapat terdampak adalah 
variabel/data yang di-*pass* sebagai argumen pada *function* `setState`. Pada tugas ini, variabel `counter` diubah dalam `setState`.

### Jelaskan perbedaan antara `const` dengan `final`.

`const` adalah modifier variabel yang membuat value sebuah variabel menjadi tetap dan nilainya harus diketahui saat *compile time*. Sedangkan, 
`final` adalah modifier yang membuat *reference* dari sebuah variabel menjadi tetap, namun valuenya masih bisa berubah. Nilai dari `final` tidak harus diketahui saat *compile time*.

### Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas.

1. Membuat variable penentu di dalam function build, seperti `isEven` dan `isGreaterThanZero`
2. Variabel tersebut digunakan untuk melakukan conditional styling dan render.
```dart
 Text(
      isEven ? 'GENAP' : 'GANJIL',
      style : TextStyle(color: isEven ? Colors.red : Colors.blue )
 ) 
```
3. Selanjutnya, membuat Widget Padding yang men-*warp* Row Layout, dan menerapkan padding.
4. Buat dua tombol "+" dan "-", dan melakukan positioning dan definisikan `onPressed` event.

#### Thanks !
