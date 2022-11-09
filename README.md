# counter_7

Pemrograman Berbasis Platform (CSGE602022) - diselenggarakan oleh Fakultas Ilmu Komputer Universitas Indonesia, Semester Ganjil 2022/2023

Muhammad Nabiel Andityo Purnomo - 2106750465

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
