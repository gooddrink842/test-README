## Tugas 1 - Platform Essay

[Platform: What is it?](https://drive.google.com/file/d/10xfIkMP9gC5HLdUUkkHPvTSbV1zxJWBr/view?usp=sharing)

## Tugas 2 - Katalog

### Deployed App

[Catalog App](https://pbp-assignment-2106750540.herokuapp.com/katalog/)

### Django Scheme

![Bagan Django](https://github.com/AdrianRamadhan27/assignment-pbp/blob/main/assignment1_chart.gif)


*Made with [Canva](https://www.canva.com)*

Pada framework **Django**, kita dapat membuat suatu aplikasi yang mengimplementasikan struktur **MVT** (Model, View, Template). Model di sini merepresentasikan *entity* pada database (dipelahari di Basis Data). Views bisa dibilang adalah tempat algoritma yang melakukan proses atas *request* dan *response* sehingga aplikasi bisa berjalan. Template adalah tampilan (*front-end*) yang akan dilihat oleh pengguna.

Ketika seorang user membuat request untuk aplikasi ini, `urls.py` pada folder `project_django` akan melakukan *routing* berdasarkan jenis url request yang diterima. Setelah itu, ia akan memanggil aplikasi yang ada, salah satunya adalah **katalog**. Dalam folder katalog, juga ada `urls.py` yang mengatur routing untuk url dengan prefix `katalog/`. Jika tidak ada prefix tambahan, yang akan dipanggil adalah function `show_katalog()` dari `views.py`. Function ini akan memanggil data bermodelkan `CatalogItem` yang terdefinisikan pada `models.py` dari database yang masih berupa file `.json`. Setelah itu, function ini juga akan me-*render* file template `katalog.html` dengan konteks berupa data tadi. Baru lah user akan ditampilkan aplikasi katalog dengan tabel data yang ada. 

### Usage of Virtual Environment

Dalam pengembangan aplikasi Django di repositori lokal komputer kita, dibutuhkan sebuah Virtual Environment yang dapat kita buat dengan command `python -m venv [nama_environment]`. Command ini akan membuat folder dengan nama environment yang kita pilih dan kita dapat mengaktifkan Virtual Environment dengan `/Scripts/activate.bat` di dalam folder ini. Menurut [Andrade (2021)](https://towardsdatascience.com/why-you-need-a-python-virtual-environment-and-how-to-set-it-up-35019841697d), Virtual Environment ini digunakan agar kita tidak perlu menyesuaikan *requirements*/*dependencies* yang dibutuhkan project di komputer kita secara global. Kita hanya perlu meng-*install* nya di virtual environment dan project kita bisa dijalankan. 

### How I Did It

Dari template project yang sudah disediakan, aku ditugaskan untuk:
1. Membuat sebuah fungsi pada views.py yang dapat melakukan pengambilan data dari model dan dikembalikan ke dalam sebuah HTML.
Pertama, aku clone repositori github ku ke repositori lokal. Lalu aku membuat sebuah fungsi `show_katalog()` yang mengambil data dengan memanggil `CatalogItem.objects.all()` yang berisi data yang dibuat dari command `python manage.py loaddata inital_catalog_data.json`. Aku lalu membuat sebuah dictionary `context` yang isinya adalah data yang akan ditampilkan pada file HTML. Nama data beserta value yang ada diantaranya adalah nama, npm, dan list_catalog. Setelah itu aku me-`return` pemanggilan function `render` dengan parameter pertama adalah request, parameter kedua adalah file `katalog.html`, dan parameter ketiga adalah `context`. Oiya, file `index.html` di dalam `/katalog/templates/` kuganti namanya agar tidak berkomplikasi dengan file dengan nama yang sama di `example_app`.   
2. Membuat sebuah routing untuk memetakan fungsi yang telah kamu buat pada views.py.
Untuk membuat sebuah routing, aku pertama-tama membuat file `urls.py` di dalam folder katalog. Di dalamnya ada sebuah array `urlpatterns`. Isinya merupakan path apa saja yang bisa dipanggil oleh aplikasi katalog ini. Untuk path dengan request hanya `katalog/`, ia akan memanggil function `show_katalog()` dari views. Tak lupa, aku juga menambahkan path `katalog/` pada urlpatterns dari `project_django/urls.py`. 
3. Memetakan data yang didapatkan ke dalam HTML dengan sintaks dari Django untuk pemetaan data template.
Untuk memetakan data ke file HTML, aku menggunakan sintaks `{% statement %}` untuk menjalankan proses kode seperti for loop dan `{{ variable }}` untuk menampilkan value dari suatu variable. Aku membuat for each loop dari setiap data `CatalogItem` yang diterima dari context. Setiap iterasinya akan membuat sebuah row berisikan cell data yang masing-masing cell nya berisikan atribut dari data item. Aku juga menampilkan nama dan NPM pada bagian atas tabel.
4. Melakukan deployment ke Heroku terhadap aplikasi yang sudah kamu buat sehingga nantinya dapat diakses oleh teman-temanmu melalui Internet.
Untuk deployment, aku pertama membuka [Heroku](https://www.heroku.com) dan membuat app baru. Kemudian, aku membuka Account Settings dan meng-*copy* API Key. Setelah itu, aku commit perubahan yang telah aku lakukan ke repositori github. Di github, aku buka settings repositoriku dan menambahkan **secrets**. Secrets yang kutambahkan adalah `HEROKU_APP_NAME` dan `HEROKU_API_KEY`. Selanjutnya aku buka tab Actions dan di bagian workflow aku lakukan `Re-run all jobs`pada commit terakhir. Akhirnya, aplikasiku bisa dibuka di domain yang disediakan Heroku.

### Testing
Setelah aplikasi Django sudah jadi, aku menambahkan sebuah unit test sederhana yaitu model testing. Pada file `tests.py` terdapat sebuah test case yang akan mengecek apabila model yang dibuat merupakan instance dari `CatalogItem`. Testing ini dapat dijalankan dengan command `python manage.py test`.

## Tugas 3 - MyWatchlist

### 🌐 Deployed App 

[My Watchlist App](https://pbp-assignment-2106750540.herokuapp.com/mywatchlist/html/)

### 📙 HTML, XML, and JSON
- **HTML** adalah HyperText Markup Language yang biasanya digunakan untuk pengembangan tampilan website. 
- **XML** adalah eXtensible Markup Language yang biasanya digunakan untuk menyimpan, mengirim, dan merekonstruksi data arbitrary.
- **JSON** adalah JavaScript Object Notation yang biasanya digunakan untuk merepesentasikan data dan transmitnya pada website.


Perbedaan dari ketiganya ini adalah sebagai berikut


| HTML | XML | JSON |
|------|-----|------|
| Merupakan bahasa markup | Merupakan bahasa markup dan format file | Merupakan format data-interchange |
| Difokuskan pada presentasi | Difokuskan pada transfer data | Difokuskan pada transfer data |
| Mengutamakan format | Mengutamakan konten/data | Mengutamakan konten/data |
| Tagnya predefined dan terbatas | Tagnya tidak predefined tetapi extensible | Tidak menggunakan tag |
| Tidak menyediakan namespace | Menyediakan namespace | Tidak menyediakan namespace |

### 🚚 Data Delivery
Ketika kita ingin mengimplementasikan suatu platform, kita tidak bisa hanya menggunakan data *static* atau template karena akan menjadi percuma. Kita memerlukan data asli *real-time* yang disimpan dalam database dan perlu kita tampilkan ketika seorang user memanggil request. Untuk itu, data yang tersimpan itu perlu adanya sistem untuk mengirim data dari satu tampilan ke tampilan lainnya. Dengan data delivery inilah user dapat menerima data secara langsung. Data delivery dapat keluar dalam bentuk API layaknya JSON setelah suatu proses back-end, yang kemudian dapat dimasukkan ke template front-end layaknya HTML. 

### 📝 How I Did It
- [x] Membuat suatu aplikasi baru bernama `mywatchlist` di proyek Django Tugas 2 pekan lalu
Untuk membuat app baru, aku pertama membuka terminal di root folder dari django_project dan menjalankan `python manage.py startapp mywatchlist`. Setelah itu akan muncul folder baru bernama `mywatchlist` yang digunakan untuk pengembangan aplikasi mywatchlist.

- [x] Menambahkan path `mywatchlist` sehingga pengguna dapat mengakses http://localhost:8000/mywatchlist
Untuk menambah path ke app baru, aku pertama membuat file `urls.py` di folder mywatchlist dan mengisinya dengan array urlpatterns (untuk sementara kosongkan dulu). Setelah itu, aku buka folder `project_django` dan pada file `urls.py` nya kutambahkan path baru di dalam urlpatterns. Path yang dibuat adalah `path('/mywatchlist', include('mywatchlist.urls'))`. Tak lupa, aku juga menambahkan 'mywatchlist' pada array **INSTALLED_APPS** di dalam `settings.py`.

- [x] Membuat sebuah model `MyWatchList`
Sesuai dengan kriteria atribut di soal, pada file `models.py` aku membuat class baru bernama `MyWatchlist` dengan sebagai berikut.
  - [x] `watched` bertipe BooleanField
  - [x] `title` bertipe CharField
  - [x] `rating` bertipe IntegerField (dengan validator `MinValueValidator(1)` & `MaxValueValidator(5)`)
  - [x] `release_date` bertipe DateField
  - [x] `review` bertipe TextField 

### 👮 Postman Request Results
- ![HTML Request](https://github.com/AdrianRamadhan27/assignment-pbp/blob/main/static/images/postman-mywatchlist-html.jpg)
*Accesing https://pbp-assignment-2106750540.herokuapp.com/mywatchlist/html/*


- ![XML Request](https://github.com/AdrianRamadhan27/assignment-pbp/blob/main/static/images/postman-mywatchlist-xml.jpg)
*Accesing https://pbp-assignment-2106750540.herokuapp.com/mywatchlist/xml/*


- ![JSON Request](https://github.com/AdrianRamadhan27/assignment-pbp/blob/main/static/images/postman-mywatchlist-json.jpg)
*Accesing https://pbp-assignment-2106750540.herokuapp.com/mywatchlist/json/*


### Testing
Aku telah mengimplementasikan 3 url di `mywatchlist`. Untuk menjalankannya, hanya perlu run `python manage.py test mywatchlist`tapi pastikan sudah menjalankan `python manage.py collectstatic` sebelumnya. Test ini akan mengecek `status_code` dari response yang diberikan setiap url dan hanya akan bisa lulus tes jika mengembalikan `200 OK`.

## Tugas 4 - ToDoList

### 🌐 Deployed App 

[To Do List App](https://pbp-assignment-2106750540.herokuapp.com/todolist/)

### 💽 csrf_token
CSRF atau Cross Site Request Forgery dapat terjadi ketika suatu situs yang _malicious_ menyebabkan browser pengguna membuat request ke server yang menyebabkan suatu perubahan pada server. Server akan mengira bahwa request yang dibuat merupakan niatan dari pengguna karena memiliki _credentials_ pengguna yaitu cookies.
Dengan menambahkan tag `csrf_token` ke dalam tag `<form>` di dalam template project django, kita dapat memastikan bahwa request-request yang tergolong 'unsafe' seperti **POST**, **PUT**, dan **DELETE** dapat terlindungi dari adanya CSRF.

### 📋 Making Forms Manually
Jika kita tidak ingin menggunakan `ModelForm` dari `django.forms`, kita dapat membuat form secara manual. Untuk tag yang digunakan pada template masih sama, yaitu tag `<form>` yang di dalamnya kita masukkan juga `{% csrf_token %}`. Nah, yang membedakan adalah pada isi form, kita akan membuat widgets nya secara manual dengan menggunakan tag `<input>` dan sebagainya. Pada tiap widgets ini kita akan berikan attribute `name` yang nantinya akan digunakan untuk mengidentifikasikan jenis atribut model yang dimasukkan. Contohnya  sebagai berikut untuk form create-task.

```html
<form method="POST" action="">
        {% csrf_token %}
        <label for="title">Title</label>
        <input type="text" id="title" name="title"/>
        
        <label for="description">Description</label>
        <textarea id="description" name="description"></textarea>

        <input type="submit", value="Create">
</form>
```

Lalu, pada file `views.py`, function untuk method POST perlu diubah juga. Pertama, kode untuk method get atau yang hanya menampilkan template form nya perlu dipisah dari kode yang memproses form nya. Sehingga kita buat if-statement yang mengecek apakah `request.method` adalah `"POST"`. Lalu di dalam blok if-statement ini, kita buat instance model baru berdasarkan atribut yang dimasukkan dalam form. Kita dapat mengidentifikasi jenis atributnya dengan menggunakan `request.POST.get(name)`. Setelah itu, kita save instance modelnya dan redirect ke halaman yang ditujukan. Contohnya sebagai berikut untuk create-task.
```python
def create_task(request):
    if request.method == 'POST':
        title = request.POST.get('title')
        description = request.POST.get('description')
        task = Task.objects.create(title=title, description=description, user=request.user)
        task.save()
        return redirect('todolist:show_todolist')

    context = {}
    return render(request, 'create_task.html', context)
```

### 📊 Data Flow
Alur data yang terjadi ketika pengguna menambahkan data adalah bagian dari CRUD (Create, Retrieve, Update, Delete). Ketika pengguna mengisi form di template HTML, data tiap atribut akan disimpan dan dioper ke function di `views.py`. Setelah itu, akan dibuat (create) instance dari model baru berdasarkan atribut yang tersimpan. Kemudian, instance model ini akan disimpan pada database. Terakhir, tiap instance yang ada pada di database akan diambil (retrieve) dengan query khusus agar tampil di template HTML.

### 📝 How I Did It
Berikut adalah caraku mengimplementasikan daftar tugas yang perlu dilakukan
- [x] Membuat suatu aplikasi baru bernama `todolist` di proyek tugas Django yang sudah digunakan sebelumnya. \
Sama seperti tugas pekan sebelumnya, jalankan `python manage.py startapp todolist` di terminal proyek django. 
- [x] Menambahkan path `todolist` sehingga pengguna dapat mengakses http://localhost:8000/todolist. \
Tambahkan `'todolist'` ke INSTALLED_APPS di `settings.py`, dan tambahkan `path('/todolist')` ke urlspattern di `urls.py`. Jangan lupa untuk membuat `urls.py` di dalam folder todolist yang berisi array urlpatterns.
- [x] Membuat sebuah model `Task` yang memiliki atribut sebagai berikut: \
        - `user` menggunakan ForeignKey() dengan parameter `django.contrib.auth.models.User` \
        - `date` menggunakan DateField() dengan parameter auto_now_add = `True` agar otomatis ditambahkan ketika Task dibuat \
        - `title` menggunakan CharField() \
        - `description` menggunakan TextField() \
        - Aku juga menambahkan atribut `id` menggunakan AutoField() sebagai primary key dan `is_finished` menggunakan BooleanField() \
        
- [x] Mengimplementasikan form registrasi, login, dan logout agar pengguna dapat menggunakan todolist dengan baik. \
1. Untuk registrasi, buat function `register()` pada `views.py`. Tambahkan form ke context template yang akan di render. Form yang digunakan adalah `UserCreationForm()` dari `django.contrib.auth.forms`. Buat template `register.html` yang berisi tag `<form>`. Di dalam tag form jangan lupa sertakan `csrf_token`. Terakhir, tambahkan `{{ form.as_table }}` untuk memanggil form user yang ada di function dalam bentuk tabel.
2. Halaman login akan menjadi halaman paling awal yang bisa diakses pengguna. Buat terlebih dahulu template `login.html` yang berisi form login. Form login berisi input title dan input description yang pada tag nya terdapat atribut `name` yang akan digunakan pada function di `views.py`. Function `login_user()` yang dibuat akan mengambil data username dan password dari `request.POST` lalu dengan function authenticate akan dicek apakah terdapat user yang cocok di database. Tambahkan cookies agar data user setelah login disimpan oleh server. Baru setelah itu redirect ke halaman utama todolist.
3. Tambahkan function `logout_user()` Function ini akan memanggil function logout(request) dan menghapus cookies yang telah dibuat setelah login. Simpelnya, function ini melakukan opposite dari login_user().

- [x] Membuat halaman utama todolist yang memuat username pengguna, tombol Tambah Task Baru, tombol logout, serta tabel berisi tanggal pembuatan task, judul task, dan deskripsi task. \
Buat function `show_todolist()` yang memiliki context berisi username yang berasal dari cookies dan data Task yang telah dibuat oleh user saat ini. Gunakan method `objects.filter()` untuk me-*retrieve* Task yang memenuhi `user = request.user`. Pada template `todolist.html`, Panggil username context untuk menampilkan pengguna saat ini. Buat tabel yang isi `<tbody>` nya adalah for loop untuk setiap task yang diterima dari context. Tambahkan tombol `logout` di bawah tabel tersebut. Agar pengguna tidak dapat mengakses halaman todolist tanpa login, tambahkan `@login_required(login_url='/todolist/login')` di atas pendefinisian function `show_todolist()`.
- [x] Membuat halaman form untuk pembuatan task. Data yang perlu dimasukkan pengguna hanyalah judul task dan deskripsi task. \
Buat file baru bernama `forms.py` didalam folder todolist. Pada file ini, buat sebuah class bernama TaskForm yang meng-*extend* class `ModelForm` dari django.forms. Di dalam definisi class ini, buat class Meta dengan 2 atribut. Atribut pertama adalah model yang menyimpan model Task. Atribut satunya lagi adalah fields yang merupakan array berisi field yang dapat diisi user pada form saat pembuatan Task. Pada kasus ini, fields yang perlu diisi hanyalah `title` dan `description`. 
Setelah itu, buat function `create_task()` di `views.py`. Implementasi function ini kurang lebih sama dengan function `register()` hanya saja setelah membuat object task, assign attribute user menjadi request.user lalu save lagi objek task agar disimpan pada database.
Pada template `create_task.html` tidak perlu banyak yang perlu diubah jika menyalin dari template `register.html`. Modifikasi sesuka hati agar lebih relevan dengan fungsi halamannya.
- [x] Membuat routing sehingga beberapa fungsi dapat diakses melalui URL berikut:
 - http://localhost:8000/todolist berisi halaman utama yang memuat tabel task. 
 Tambahkan path('') pada urlpatterns yang memanggil function `show_todolist()`.
 - http://localhost:8000/todolist/login berisi form login.
 Tambahkan path('login/') pada urlpatterns yang memanggil function `login_user()`
 - http://localhost:8000/todolist/register berisi form registrasi akun.
 Tambahkan path('register/') pada urlpatterns yang memanggil function `register()`
 - http://localhost:8000/todolist/create-task berisi form pembuatan task.
 Tambahkan path('create-task/') pada urlpatterns yang memanggil function `create_task()`
 - http://localhost:8000/todolist/logout berisi mekanisme logout.
 Tambahkan path('logout/') pada urlpatterns yang memanggil function `logout_user()`
- [x] Melakukan deployment ke Heroku terhadap aplikasi yang sudah kamu buat sehingga nantinya dapat diakses oleh teman-temanmu melalui Internet. \
Karena aplikasi dari tugas 2 sudah dideploy menggunakan repository yang sama, yang perlu dilakukan hanyalah commit perubahan ke repository github.
- [x] Membuat dua akun pengguna dan tiga dummy data menggunakan model Task pada akun masing-masing di situs web Heroku.
Tambahkan User baru dengan membuka aplikasi yang telah di deploy dengan 2 cara. Cara pertama adalah memanfaatkan fitur admin django. Agar bisa login ke situs admin. Jalankan `python manage.py createsuperuser` di terminal aplikasi heroku dan buat sebuah akun admin. Masuklah ke halaman admin dan tambahkan user baru di database User.
User baru juga bisa dibuat dengan mendaftarkan akun pada halaman register yang telah dibuat. Setelah itu, buat 3 task dengan form create-task pada masing-masing akun. Mirisnya, jumlah tugas pekan ini lebih dari 6 :(.

## Tugas 5 - Web Design

### Inline vs Internal vs External CSS
- Inline CSS - Metode styling ini memanfaatkan atribut `style` dari tag HTML di dalam template. Value dari atribut style nantinya adalah string styling. Metode ini efektif digunakan jika hanya sebatas menambahkan styling pada 1 selector yang digunakan dan tidak akan digunakan lagi. Karena itu juga, metode ini kurang cocok jika ingin membuat style yang ingin digunakan kembali.
- Internal CSS - Metode styling ini menggunakan tag `<style>` dan styling ditulis di dalam tag tersebut. Dengan metode ini, kita dapat mendefinisikan styling dari selector. Sehingga untuk tiap instance dari selector (kecuali ID) yang dibuat di dalam file template yang berisi `<style>` styling nya akan selalu berlaku. Kelemahannya adalah jika style yang ingin dibuat banyak akan memenuhi file template yang seharusnya hanya diisi dengan tag endpoint. 
- External CSS - Metode styling ini menggunakan file dengan ekstensi .css untuk menuliskan stylingnya. File ini nantinya di-referensikan dengan tag `<link>` di dalam tag `<head>` dari template. Sama dengan internal CSS, styling yang dibuat akan berlaku pada tiap instance selector. Bedanya adalah yang mana internal CSS hanya berlaku pada 1 file, external CSS dapat di-referensikan di berbagai file sehingga 1 styling file `.css` dapat digunakan untuk beberapa template. Kelemahannya mungkin akan memengaruhi waktu render halaman website, karena perlu mereferensikan file luar.


### HTML5 Tags
- `<p>` - Teks yang diapit oleh tag ini akan tampil dengan ukuran normal.
- `<h1>` ... `<h6>` - Teks yang diapit oleh tag ini akan tampil sebagai heading/sub-heading. Ukuran teks `<h1>` paling besar dan ukuran teks `<h6>` paling kecil.
- `<a>` - Teks yang diapit oleh tag ini akan tampil sebagai link. Tujuan dari linknya dapat ditentukan dengan attribut `href`.
- `<div>` - Tag ini dapat membungkus dan memisahkan elemen-elemen lain.
- `<form>` - Tag ini akan membuat form yang dapat mengirimkan request POST/UPDATE/DELETE.
- `<input>` - Tag ini digunakan di dalam tag `<form>` yang dapat menerima masukan dari pengguna. Atribut `type` menentukan jenisnya.
- `<button>` - Tag ini akan membuat sebuah kotak yang dapat ditekan layaknya tombol.
- `<span>` - Tag ini bekerja mirip dengan `<div>` tapi hanya dalam 1 baris teks.
- `<br>` - Tag ini akan membuat bari baru.
- `<hr>` - Tag ini akan membuat garis pemisah.
- `<table>` - Tag ini akan membuat tabel dengan `<tr>` sebagai baris dan `<td>` sebagai kolom/data.


### CSS Selectors
- Element Selector - Selector ini menggunakan tag HTML sebagai selector untuk mengubah properti yang terdapat dalam tag tersebut. 
Format penulisan element selector adalah sebagai berikut.
```CSS
h1 {
  color: #fca205;
  font-family: "Monospace";
  font-style: italic;
}
```
- ID Selector - Selector ini menggunakan ID yang ditambahkan pada tag sebagai selector-nya. Ia hanya akan mengubah properti tag yang memiliki ID yang dijadikan selector. Jika ada elemen lain dengan tag yang sama, properti nya tidak akan diubah karena ID nya tidak sama. 
Format penulisan ID selector adalah sebagai berikut.
```CSS
#header {
  background-color: #f0f0f0;
  margin-top: 0;
  padding: 20px 20px 20px 40px;
}
```
- Class Selector - Selector ini menggunakan class yang ditambahkan pada tag sebagai selector-nya. Ia hanya akan mengubah properti tag yang memiliki class yang dijadikan selector. Bedanya adalah class yang sama dapat digunakan berkali-kali pada elemen yang berbeda.
Format penulisan ID selector adalah sebagai berikut.
```CSS
.content_section {
  background-color: #3696e1;
  margin-bottom: 30px;
  color: #000000;
  font-family: cursive;
  padding: 20px 20px 20px 40px;
}
```
### How I did it
- [x] Kustomisasi templat HTML yang telah dibuat pada Tugas 4 dengan menggunakan CSS atau CSS framework (seperti Bootstrap, Tailwind, Bulma) dengan ketentuan sebagai berikut:
        Aku menggunakan framework Tailwind CSS untuk styling aplikasi Todolist. Untuk cara menambahkannya cukup simpel, aku hanya perlu menambahkan baris berikut ke dalam tag `<head>` dari `base.html`.
```HTML
<script src="https://cdn.tailwindcss.com"></script>
```
  - [x]  Kustomisasi templat untuk halaman login, register, dan create-task semenarik mungkin. \
        Untuk kustomisasi menggunakan Tailwind, aku hanya perlu melakukan styling lewat utility class yang telah disediakan. Berikut adalah contoh potongan template todolist.html yang memanfaatkan utility class dari Tailwind.
```HTML
<div class = "h-screen flex flex-col items-center justify-center">

<h1 class="block text-black-1000 text-xl font-bold mb-2">Login</h1>


<div class="w-full max-w-xs">
<form method="post" class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
  {% csrf_token %}
  <div class="mb-4">
    <label class="block text-gray-700 text-sm font-bold mb-2" for="username">
      Username
    </label>
    <input type="text" name="username" placeholder="Username" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="username">
  </div>
  <div class="mb-6">
    <label class="block text-gray-700 text-sm font-bold mb-2" for="password">
      Password
    </label>
...
```
Dapat terlihat bahwa styling yang digunakan serupa dengan inline CSS. Bedanya kita tidak memakai atribut style, melainkan class. Seperti yang dijelaskan sebelumnya tentang CSS selector, tiap class yang tersedia di Tailwind sudah diberikan CSS yang menyesuaikan sehingga kita hanya perlu menambahkan class untuk menambah style.
  - [x]  Kustomisasi halaman utama todo list menggunakan cards. (Satu card mengandung satu task). \
  Untuk membuat card, aku menggunakan template tailwind yang kudapat dari website berikut [17 Tailwind CSS Card Examples](https://ordinarycoders.com/blog/article/17-tailwindcss-cards) dengan sedikit perubahan yang kubuat agar menyesuaikan. Aku juga menggunakan class grid dari tailwind untuk membuat grid tiap kartu yang tiap baris nya berisi 3 kolom. Berikut potongan kodenya.
```HTML
<div class="w-full ">
<div class="h-20 lg:h-auto lg:w-48 flex-none bg-cover rounded-t lg:rounded-t-none lg:rounded-l text-center overflow-hidden">
</div>
<div class="border-r border-b border-l border-gray-400 lg:border-l lg:border-t lg:border-gray-400 bg-white rounded-b lg:rounded-b-none lg:rounded-r p-4 flex flex-col justify-between leading-normal hover:bg-gray-100 text-white font-bold py-2 px-4">
    <p class="text-gray-600">{{task.date}}</p>
    <div class="mb-8">
    <div class="text-gray-900 font-bold text-xl mb-2">{{task.title}}</div>
    <p class="text-gray-700 text-base">{{task.description}}</p>
  </div>
  <div class=" flex flex-col items-end ">
    <div class="text-sm ">
      <p class="text-gray-900 leading-none">{% if task.is_finished %} Selesai {% else %} Belum Selesai {% endif %}</p>
      <button class="bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline">
        <a href="/todolist/update/{{task.id}}">Update</a>
    </button>
      <button class="bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline">
        <a href="/todolist/delete/{{task.id}}">Delete</a>
    </button>
    </div>
  </div>
</div>
</div>
```
- [x]  Membuat keempat halaman yang dikustomisasi menjadi responsive. \
Agar membuat halaman yang responsive di Tailwind, aku menggunakan prefix breakpoint. Utility class dengan prefix ini berkesinambungan dengan CSS `@media (min-width: [width in px]) { ... }`. Dengan adanya prefix ini, aku bisa melakukan kustomisasi sesuai dengan ukuran minimal dari layar sehingga akan menyesuaikan dengan *device* yang digunakan. Ada 5 prefix default yang disediakan Tailwind.
- `'sm'` - Width minimal adalah 640px
- `'md'` - Width minimal adalah 780px
- `'lg'` - Width minimal adalah 1024px
- `'xl'` - Width minimal adalah 1280px
- `'2xl'` - Width minimal adalah 1536px

Karena width minimal yang disediakan hanyalah 640px (yang mana ini masih lebih lebar dari banyak *mobile device* pada umumnya), dalam penulisan styling yang harus diprioritaskan pertama adalah untuk ukuran mobile. Baru setelah itu tambahkan prefix breakpoint untuk styling ukuran yang lebih besar. Contohnya pada kode berikut untuk pembuatan grid hanya di layar selebar minimum 1024px
```HTML

<div class="h-auto flex flex-col items-center justify-center p-2 lg:grid grid-cols-3 gap-3">

    
            {% for task in tasks%}
            
            <div class="w-full ">
```

## Tugas 6 - Javascript and AJAX

### 🌐 Deployed App 

[To Do List App](https://pbp-assignment-2106750540.herokuapp.com/todolist/)


### 🔄 Asynchronous vs Synchronous Programming
- **Asynchronous** Programming adalah teknik yang memungkinkan program untuk memulai task yang berpotensi berjalan lama dan masih dapat responsif terhadap event lain saat task itu berjalan, sehingga tidak perlu menunggu task tersebut usai. 

- **Synchronous** Programming adalah model pemrograman di mana task berlangsung secara berurutan. Dalam model ini, operasi terjadi satu demi satu. Program pindah ke task berikutnya ketika task saat ini telah menyelesaikan eksekusi dan telah mengembalikan hasil.

| Asynchronous | Synchronous |
| ------------ | ----------- |
| Multi-thread, operasi pada program berjalan secara paralel | Single-thread, hanya satu operasi yang berjalan tiap waktu |
| Non-blocking, dapat mengirimkan lebih dari 1 request ke server | Blocking, hanya dapat mengirimkan satu request dan harus menunggu response |
| Lebih cepat | Lebih lambat dan metodikal |
 
### 🖱 Event-Driven Programming
Event-Driven Programming adalah paradigma di mana entitas (objek, layanan, dan sebagainya) berkomunikasi secara tidak langsung dengan mengirimkan pesan satu sama lain melalui perantara. Pesan biasanya disimpan dalam sebuah queue sebelum dijalankan.
Event adalah potongan data yang dikirim oleh user dan akhirnya diterima oleh program. Salah satu contohnya adalah sebagai berikut.

```Javascript
$("#close-modal").click(function() {
   $("#my-modal").attr("style", "display:none");
});
```
Pada blok kode di atas, script akan mengubah atribut dari tag HTML dengan id `my-modal` setelah button `close-modal` di-_click_. Click ini lah yang merupakan salah satu contoh dari event.

### 🔃 Asynchronous Programming in AJAX
Jelaskan penerapan asynchronous programming pada AJAX.
AJAX adalah singkatan dari Asynchronous Javascript And XML. Ini adalah teknik yang digunakan mengirim dan mengambil data dari server. Proses ini dilakukan secara asinkron agar tidak mengganggu keadaan halaman web saat ini. AJAX mencakup bidang teknologi web development yang saling berinteraksi satu sama lain. Ini termasuk HTML (XHTML), CSS, DOM, JSON (XML), dan Javascript.
Berikut adalah cara kerja AJAX. \
![image](https://user-images.githubusercontent.com/58902925/194973930-83735b0e-133f-4b74-991e-561e3f011a39.png) \
_https://www.w3schools.com/_
1. Sebuah event terjadi pada halaman web
2. Object `XMLHttpRequest` dibuat oleh JavaScript
3. Object `XMLHttpRequest` mengirimkan request ke server
4. Server memproses request tersebut
5. Server mengembalikan response ke halaman web
6. Response tersebut dibaca oleh JavaScript
7. Sebuah _action_ dilakukan oleh JavaScript

### 📝 How I did it
- [x] Mengubah tugas 4 yang telah dibuat sebelumnya menjadi menggunakan AJAX.
  - [x] AJAX GET
    - [x] Buatlah view baru yang mengembalikan seluruh data task dalam bentuk JSON.
    
    Aku membuat function `show_json()` yang mengembalikan object `HttpResponse`tipe json.
    - [x] Buatlah path /todolist/json yang mengarah ke view yang baru kamu buat.
    
    Aku tambahkan path('json/') ke `urls.py` yang memanggil function `show_json()`
    - [x] Lakukan pengambilan task menggunakan AJAX GET.
    
    Pertama aku ubah function `show_todolist()` untuk tidak perlu retrieve semua object task. Lalu pada template `todolist.html` aku tambahkan script jQuery yang dibungkus `$(document).ready(function{})` agar script langsung jalan saat halaman di-load. Script yang digunakan adalah `$getJSON()` untuk menerima json dari `todolist/json/` dan `$each()` yang melakukan iterasi untuk tiap object task pada database. Pada tiap iterasi, aku menambahkan tag HTML yang sebelumnya sudah ada secara synchronous programming. Berikut adalah potongan kode yang dimaksud.
```Javascript
$(document).ready(function(){
   $.getJSON("{% url 'todolist:show_json' %}", function(data) {
       var grid = [];
       $.each(data, function(index, value) {
           var cards = [];
           var content = [];
           var status = ""
           if ((value.fields.is_finished)){
               status = "Selesai";
           } else {
               status = "Belum Selesai"
           }
           . . .
```
  - [x] AJAX POST
    - [x] Buatlah sebuah tombol Add Task yang membuka sebuah modal dengan form untuk menambahkan task.

    Tombol yang sudah kubuat di Tugas 4 dan Tugas 5 aku gunakan kembali, hanya saja tombol ini tidak mengarah ke halaman create-task. Aku membuat sebuah modal menggunakan tailwind-CSS yang aku ikuti dari tutorial berikut: [Creating a Modal Dialog With Tailwind CSS](https://www.section.io/engineering-education/creating-a-modal-dialog-with-tailwind-css/). Aku atur style display nya menjadi none untuk default. Dengan jQuery aku buat jika tombol ditekan display nya menjadi block. Pada modal ini kubuat form secara manual.
    - [x] Buatlah view baru untuk menambahkan task baru ke dalam database
    
    Aku membuat function `add_task_ajax()` yang akan membuat object Task dari form add task modal jika method dari request adalah POST. Setelah itu, function ini akan mengembalikan response dalam bentuk Json sebagai status keberhasilan data yang ditambahkan.
    - [x] Buatlah path /todolist/add yang mengarah ke view yang baru kamu buat.
    
    Aku tambahkan path(`add/`) ke urls.py.
    - [x] Hubungkan form yang telah kamu buat di dalam modal kamu ke path /todolist/add
    
    Ketika form task di-_submit_, Jquery akan memanggil request ajax dengan method post ke url todolist/add yang sebelumnya ditambahkan. Berikut kode yang dimaksud.
    
```Javascript
$("#task-form").submit(function(e){
    e.preventDefault();
    $("#add-btn").prop('disabled', true);
    $("#add-btn").text('Processing...');
    var $form = $(this);
    var serializedData = $form.serialize();
    $.ajax({
        url: "{% url 'todolist:add_task' %}",
        type: "POST",
        data: serializedData,
        dataType: 'json',
        success: function (data) {
        . . . 
```

   - [x] Tutup modal setelah penambahan task telah berhasil dilakukan.
   
   Selain menambahkan data task, submit form juga akan mengembalikan style dari modal menjadi display:none.
   
```Javascript
$("#my-modal").attr("style", "display:none");
```
   - [x] Lakukan refresh pada halaman utama secara asinkronus untuk menampilkan list terbaru tanpa reload seluruh page.
   
   Agar halaman dapat te-_refresh_ secara asinkronus tanpa reload seluruh page. Aku ulangi proses getJSON dari method GET setelah sebuah form disubmit.
