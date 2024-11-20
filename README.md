# FShop

**_Dibuat oleh Muhammad Fakhri dengan NPM 2306226731 dari kelas PBP C_**

## Tugas Indvidu 7

### 1. Jelaskan apa yang dimaksud dengan stateless widget dan stateful widget, dan jelaskan perbedaan dari keduanya.

1. StatelessWidget

StatelessWidget adalah widget yang bersifat statis dan tidak berubah-ubah selama siklus hidupnya. Artinya, widget ini hanya akan dirender satu kali dan tidak akan memperbarui tampilannya meskipun ada perubahan data. StatelessWidget cocok digunakan ketika kita memiliki elemen UI yang tidak bergantung pada perubahan data atau tidak membutuhkan interaksi pengguna. Misalnya, untuk menampilkan teks statis, gambar, atau ikon.

Contoh penggunaan :
```dart
class MyStatelessWidget extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Text('Ini adalah StatelessWidget');
  }
}
```

2. StatefulWidget

StatefulWidget adalah widget yang dinamis dan dapat berubah selama siklus hidupnya. Widget ini memiliki objek `State` yang memegang data atau nilai yang dapat diubah. Ketika data dalam `State` berubah, maka tampilan akan diperbarui secara otomatis. StatefulWidget cocok digunakan ketika kita membutuhkan UI yang responsif terhadap perubahan data atau interaksi pengguna. Misalnya, tombol yang menghitung jumlah klik, form input, atau widget yang mengupdate data secara real-time.

Contoh penggunaan :
```dart 
class MyStatefulWidget extends StatefulWidget {
  @override
  _MyStatefulWidgetState createState() => _MyStatefulWidgetState();
}

class _MyStatefulWidgetState extends State<MyStatefulWidget> {
  int counter = 0;

  void incrementCounter() {
    setState(() {
      counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        Text('Counter: $counter'),
        ElevatedButton(
          onPressed: incrementCounter,
          child: Text('Tambah'),
        ),
      ],
    );
  }
}
```

Perbedaan dari keduanya :

1. StatelessWidget tidak dapat berubah setelah dirender, sedangkan StatefulWidget dapat berubah selama siklus hidupnya.
2. StatelessWidget tidak menyimpan data yang berubah, sedangkan StatefulWidget menyimpan data yang dapat berubah (`State`).
3. StatelessWidget tidak bisa mengupdate tampilan, sedangkan StatefulWidget dapat mengupdate tampilan dengan `setState()`
4. StatelessWidget contoh penggunaan nya adalaha teks statis, ikon, dan gambar tidak interaktif, sedangkan StatefulWidget contohnya tombol dengan counter, form input, widget interaktif

### 2. Sebutkan widget apa saja yang kamu gunakan pada proyek ini dan jelaskan fungsinya.

1. Scaffold: Struktur dasar halaman yang menyediakan layout umum untuk elemen-elemen seperti AppBar dan body.
2. AppBar: Komponen bagian atas halaman yang menampilkan judul aplikasi, yaitu "FShop" dalam proyek ini.
3. Padding: Memberikan jarak (padding) di sekitar widget anaknya untuk mengatur tata letak.
4. Column: Menyusun widget secara vertikal. Digunakan untuk mengatur letak teks, grid, dan elemen-elemen lain dalam tampilan.
5. Row: Menyusun widget secara horizontal. Dalam contoh ini, Row digunakan untuk menampilkan tiga InfoCard secara berdampingan.
6. GridView.count: Menampilkan widget dalam bentuk grid dengan jumlah kolom tertentu. Di sini, GridView digunakan untuk menampilkan ItemCard dalam tiga kolom.
7. Center: Menyusun widget anaknya di tengah-tengah secara horisontal dan vertikal.
8. Text: Menampilkan teks statis. Digunakan untuk menampilkan informasi seperti "Welcome to FShop" dan nama item di dalam kartu.
9. SizedBox: Memberikan ruang atau jarak antar widget. Dalam proyek ini, SizedBox digunakan untuk memberikan jarak vertikal antar elemen.
10. Card: Membuat tampilan kotak dengan bayangan di bawahnya. Card digunakan untuk InfoCard, menampilkan informasi seperti NPM, Nama, dan Kelas.
11. Material: Memberikan efek material pada widget dan sering digunakan bersama InkWell untuk efek sentuhan.
12. InkWell: Menambahkan animasi sentuhan pada widget. Pada proyek ini, InkWell digunakan dalam ItemCard sehingga setiap item dalam grid bereaksi saat disentuh.
13. Icon: Menampilkan ikon yang mewakili setiap item dalam ItemCard, seperti ikon tambah atau logout.
14. SnackBar: Menampilkan notifikasi sementara di bagian bawah layar. Dalam proyek ini, digunakan untuk memberi tahu pengguna ketika mereka menekan suatu item.

### 3. Apa fungsi dari `setState()`? Jelaskan variabel apa saja yang dapat terdampak dengan fungsi tersebut.

`setState()` memberi tahu framework bahwa ada bagian dari State yang berubah dan perlu diperbarui. Hanya widget yang dipengaruhi oleh perubahan data yang akan dirender ulang, sehingga tidak semua elemen dalam aplikasi harus diperbarui, yang membuat aplikasi lebih efisien.
Variabel-variabel yang dapat terpengaruh oleh setState() adalah:

1. Variabel State

Hanya variabel yang didefinisikan di dalam kelas State dari StatefulWidget yang dapat dipengaruhi oleh setState(). Ini termasuk variabel yang digunakan untuk menyimpan data sementara seperti counter, daftar item, status login, dll.

2. Properti UI

Setiap properti UI yang tergantung pada nilai variabel state juga akan diperbarui. Contohnya, jika sebuah widget menampilkan teks dari variabel state, maka teks tersebut akan diperbarui setiap kali setState() dijalankan.

3. Objek yang Dapat Diubah

Jika variabel adalah objek yang kompleks seperti daftar atau map, perubahan pada item di dalam objek tersebut juga bisa memicu setState() untuk merender ulang bagian-bagian tertentu.

### 4. Jelaskan perbedaan antara const dengan final.

1. `const`

Variabel `const` harus diinisialisasi dengan nilai konstan yang sudah diketahui saat waktu kompilasi, artinya nilainya sudah tetap bahkan sebelum kode dijalankan. Semua variabel `const` bersifat immutable (tidak dapat diubah) dan akan tetap konstan di seluruh aplikasi. `const` dapat digunakan pada tingkat kelas atau global untuk membuat objek konstanta yang dapat diakses di seluruh aplikasi. Dengan `const`, objek hanya dibuat sekali di memori (singleton), sehingga menghemat memori.

2. `final`

Variabel `final` hanya bisa diinisialisasi satu kali, tetapi inisialisasinya dapat dilakukan saat runtime (saat aplikasi dijalankan). Jadi, kita tidak perlu tahu nilai dari variabel `final` saat kompilasi. Setelah diinisialisasi, nilai `final` tidak bisa diubah. Namun, berbeda dengan `const`, `final` memungkinkan nilai ditentukan saat runtime. Karena dapat diinisialisasi saat runtime, `final` lebih fleksibel dibandingkan `const`. Misalnya, `final` cocok digunakan untuk nilai yang diperoleh saat runtime, seperti hasil perhitungan atau input dari pengguna.

## Tugas Individu 8

### 1. Apa kegunaan `const` di Flutter? Jelaskan apa keuntungan ketika menggunakan `const` pada kode Flutter. Kapan sebaiknya kita menggunakan `const`, dan kapan sebaiknya tidak digunakan?

Kegunaan `const`:
1. Karena banyak widget di Flutter bersifat statis (tidak berubah setelah dibuat), mendefinisikan widget sebagai `const` memungkinkan Flutter untuk tidak membuat ulang widget tersebut setiap kali antarmuka dirender ulang.
2. Dengan menandai widget sebagai `const`, Flutter memahami bahwa widget tersebut tidak perlu diperbarui atau dirender ulang, yang mengurangi beban pemrosesan.
3. `const` juga digunakan untuk mendefinisikan struktur data tetap seperti daftar (List) atau map (Map) yang tidak akan diubah.

Keuntungan menggunakan `const`:
1. Objek `const` hanya disimpan sekali dalam memori (singleton). Flutter akan menggunakan instance yang sama dari objek tersebut jika digunakan beberapa kali, sehingga menghemat penggunaan memori.
2. Dengan menandai widget atau objek sebagai `const`, Flutter tidak perlu membuat ulang objek tersebut, sehingga proses rendering menjadi lebih cepat dan hemat sumber daya.
3. Menggunakan `const` membantu membuat kode lebih mudah dibaca dan dipahami sebagai elemen yang tidak berubah, sehingga mengurangi risiko bug akibat perubahan yang tidak disengaja.

Kapan sebaiknya menggunakan `const`:
1. Pada widget yang tidak akan mengalami perubahan, seperti `Text`, `Icon`, atau widget lain yang hanya menampilkan data statis.
```dart
  const Text('OK');
  const Icon(Icons.home);
```
2. untuk struktur data yang tidak akan berubah, seperti daftar atau map yang hanya dibaca.
```dart
  const List<String> colors = ['Red', 'Green', 'Blue'];
```
3. Jika tahu widget tidak akan berubah seiring waktu atau tidak terpengaruh oleh `setState()`, tandai sebagai `const`.

Kapan sebaiknya tidak menggunakan `const`:
1. Jika widget atau data dapat berubah, seperti ketika data diperoleh dari API atau dipengaruhi oleh `setState()`, hindari menggunakan `const`.
2. Jika nilai dari widget atau variabel diperbarui berdasarkan input pengguna atau hasil operasi yang dilakukan di runtime, `const` tidak cocok karena `const` membutuhkan nilai yang sudah diketahui saat kompilasi. Contohnya :
```dart
  final currentTime = DateTime.now();
```

### 2. Jelaskan dan bandingkan penggunaan Column dan Row pada Flutter. Berikan contoh implementasi dari masing-masing layout widget ini!

Column menyusun elemen secara vertikal (dari atas ke bawah) dan Row menyusun elemen secara horizontal (dari kiri ke kanan).
Contoh penggunaan Column :
```dart
  Column(
    mainAxisAlignment: MainAxisAlignment.center, // Mengatur posisi elemen di tengah secara vertikal
    crossAxisAlignment: CrossAxisAlignment.start, // Mengatur elemen rata kiri secara horizontal
    children: const [
      Text('Hello'),
      Text('Welcome to Flutter!'),
      Icon(Icons.thumb_up),
    ],
  );
```
Contoh penggunaan Row :
```dart
  Row(
    mainAxisAlignment: MainAxisAlignment.spaceAround, // Membagi elemen secara merata dengan jarak di antaranya
    crossAxisAlignment: CrossAxisAlignment.center, // Menempatkan elemen di tengah secara vertikal
    children: const [
      Icon(Icons.home),
      Text('Home'),
      Icon(Icons.search),
      Text('Search'),
    ],
  );
```
Perbedaan Column dan Row :
1. Column menyusun elemen secara vertikal sedangkan Row menyusun elemen secara horizontal.
2. `MainAxisAlignment` pada Column mengatur posisi di sumbu vertikal sedangkan pada Row mengatur posisi di sumbu horizontal.
3. `CrossAxisAlignment` pada Column mengatur posisi di sumbu horizontal sedangkan pada Row mengatur posisi di sumbu vertikal.
4. Column untuk menampilkan elemen di atas-bawah sedangkan Row untuk menampilkan elemen dari kiri ke kanan.
5. Column memperhatikan tinggi yang tersedia sedangkan Row memperhatikan lebar yang tersedia.

### 3. Sebutkan apa saja elemen input yang kamu gunakan pada halaman form yang kamu buat pada tugas kali ini. Apakah terdapat elemen input Flutter lain yang tidak kamu gunakan pada tugas ini? Jelaskan!

Elemen input yang digunakan:
1. TextFormField, digunakan untuk menerima masukan teks dari pengguna. Kamu menggunakan tiga TextFormField untuk mengambil input:
- Product: Untuk nama produk.
- Description: Untuk deskripsi produk.
- Quantity: Untuk jumlah produk. Ada validasi tambahan untuk memastikan bahwa input diisi dan berupa angka.
2. ElevatedButton, sebagai tombol aksi yang digunakan untuk menyimpan data form. Ketika ditekan, tombol ini memeriksa validasi form dan menampilkan dialog konfirmasi jika validasi berhasil.
3. AlertDialog, bukan elemen input, namun digunakan untuk menampilkan pesan pop-up setelah tombol "Save" ditekan dan data berhasil divalidasi.

Elemen Input yang tidak digunakan:
1. Checkbox untuk membuat kotak centang. Umumnya digunakan untuk memilih opsi biner (ya/tidak).
2. Switch, mirip dengan Checkbox, namun dalam bentuk saklar on/off.
3. Radio, untuk pilihan tunggal dari beberapa opsi, cocok untuk memilih satu item dari beberapa opsi.
4. DropdownButton, untuk menampilkan daftar opsi yang dapat dipilih pengguna dalam bentuk dropdown.
5. Slider, untuk menerima input berupa nilai rentang, seperti memilih angka dalam range tertentu.

### 4. Bagaimana cara kamu mengatur tema (theme) dalam aplikasi Flutter agar aplikasi yang dibuat konsisten? Apakah kamu mengimplementasikan tema pada aplikasi yang kamu buat?

Pada `main.dart`, dengan mendefinisikan ThemeData di MaterialApp, semua widget di aplikasi akan mengikuti aturan tema ini secara konsisten, termasuk warna, teks, dan gaya elemen. Saya menggunakan colorScheme untuk menetapkan warna utama dan sekunder. dan dengan mengaktifkan useMaterial3: true menyesuaikan aplikasi agar mendukung gaya terbaru dari Flutter, sehingga elemen UI akan lebih modern dan sesuai dengan pedoman desain Material 3.

### 5. Bagaimana cara kamu menangani navigasi dalam aplikasi dengan banyak halaman pada Flutter?

Saya menangani navigasi pada `left_drawer.dart` dengan menggunakan `Navigator.pushReplacement` agar ketika pengguna berpindah halaman, halaman sebelumnya tidak dapat diakses dengan tombol "back."
```dart
  onTap: () {
    Navigator.pushReplacement(
      context,
      MaterialPageRoute(builder: (context) => MyHomePage()),
    );
  }
```
Navigator digunakan untuk mengatur stack halaman. Dengan `Navigator.push`, halaman baru ditambahkan ke stack, sementara `Navigator.pushReplacement` mengganti halaman saat ini dengan halaman baru tanpa menumpuknya di stack.

## Tugas Individu 9
### 1. Jelaskan mengapa kita perlu membuat model untuk melakukan pengambilan ataupun pengiriman data JSON? Apakah akan terjadi error jika kita tidak membuat model terlebih dahulu?

1. Memastikan Konsistensi Data

Model membantu memastikan bahwa data yang diterima dari atau dikirim ke API memiliki struktur dan tipe data yang sesuai. Dengan model, kita dapat dengan mudah memetakan atribut JSON ke atribut objek dalam aplikasi kita.

2. Mengurangi Risiko Error

Tanpa model, data yang diterima dari JSON biasanya diakses melalui tipe `Map<String, dynamic>`. Jika ada kesalahan pada struktur JSON (seperti nama atribut berubah, tipe data salah, atau atribut tidak ada), maka akan lebih sulit mendeteksi kesalahan atau menangani kasus tersebut.

3. Mempermudah Pemrosesan Data

Model memudahkan pengelolaan data, seperti:

- Konversi JSON ke objek: `ProductEntry.fromJson(json)`
- Konversi objek ke JSON: `productEntry.toJson()`
- Mengelola data di UI atau logika aplikasi dengan struktur yang jelas.

Tanpa model, kita harus bekerja langsung dengan peta data `(Map<String, dynamic>)`, yang membuat kode sulit dipahami dan rawan kesalahan.

4. Skalabilitas

Jika aplikasi bertumbuh, penggunaan model memastikan bahwa kode tetap terstruktur. Tanpa model, semakin banyak data JSON yang harus ditangani, semakin sulit menjaga konsistensi, dan kemungkinan error akan meningkat.

**Apakah Akan Terjadi Error Jika Tidak Membuat Model?**
1. Tidak selalu error, tetapi kode menjadi lebih sulit di-maintain. Misalnya:
- Kamu bisa tetap membaca JSON dengan cara manual `(json['key'])`.
- Namun, ini membuat kode kurang aman dan rawan error saat runtime.

2. Kesalahan seperti berikut lebih mungkin terjadi:
- Null Safety Issue: Ketika key tidak ada atau bernilai null.
- Type Issue: Ketika tipe data dari JSON tidak sesuai.

### 2. Jelaskan fungsi dari library http yang sudah kamu implementasikan pada tugas ini

Pada kode yang saya gunakan, fungsi library http dalah untuk melakukan komunikasi antara aplikasi Flutter dan backend (Django). Library ini memungkinkan aplikasi Flutter mengirimkan permintaan HTTP dan menerima respons dari server. 

1. Fungsi `fetchMood` di `list_productentry.dart`

Mengambil data dari backend dalam format JSON menggunakan metode `GET`. Data JSON diterjemahkan menjadi objek Dart (`ProductEntry`) menggunakan metode `fromJson`. Fungsi ini membantu mengubah data yang diterima dari backend menjadi objek yang lebih mudah digunakan di aplikasi Flutter.

2. Fungsi `login` di `login.dart`

Mengautentikasi pengguna dengan mengirimkan username dan password ke endpoint login backend menggunakan metode `POST`. Endpoint login Django menerima data pengguna, memverifikasi kredensial, dan memberikan respons yang sesuai (misalnya, berhasil atau gagal).

3. Fungsi `onPressed` di `product_entryform.dart`

Mengirimkan data produk baru yang dimasukkan oleh pengguna ke backend menggunakan metode `POST`. Data yang dimasukkan pengguna diubah menjadi JSON menggunakan `jsonEncode` sebelum dikirim. URL endpoint Django menangani data dan menyimpannya ke database.

4. Fungsi `onPressed` di `register.dart`

Mendaftarkan pengguna baru dengan mengirimkan data pendaftaran (seperti username dan password) ke endpoint registrasi backend menggunakan metode `POST`. Data dikirim dalam format JSON ke endpoint Django yang memproses pendaftaran.

### 3. Jelaskan fungsi dari CookieRequest dan jelaskan mengapa instance CookieRequest perlu untuk dibagikan ke semua komponen di aplikasi Flutter.

**Fungsi Utama `CookieRequest`:**
1. `CookieRequest` secara otomatis menangani cookie yang diterima dari server (misalnya cookie sesi setelah login) dan menyertakannya dalam setiap permintaan HTTP berikutnya.Cookie ini memungkinkan backend mengenali pengguna yang sedang aktif tanpa perlu mengirim ulang token atau kredensial setiap kali ada permintaan.

2. Mempermudah penggunaan metode `GET`, `POST`, atau metode HTTP lainnya sambil memastikan cookie disertakan dalam header permintaan.

3. `CookieRequest` dapat digunakan untuk memeriksa apakah pengguna masih terautentikasi dengan memeriksa keberadaan atau validitas cookie sesi.

4. Dengan metode seperti `postJson` dan `get`, `CookieRequest` menyederhanakan pengiriman data JSON ke backend dan penerimaan respons dalam format yang sama.

**Mengapa `CookieRequest` Perlu Dibagikan ke Semua Komponen Aplikasi Flutter?**
1. Jika komponen berbeda di aplikasi (seperti halaman login, formulir entri, atau daftar produk) menggunakan instans `CookieRequest` yang sama, mereka akan berbagi cookie sesi yang sama. Hal ini memastikan backend dapat terus mengenali pengguna saat mereka berpindah halaman atau melakukan tindakan lain di aplikasi.

2. Membuat instans `CookieRequest` baru untuk setiap permintaan HTTP berarti cookie dan status sesi tidak akan dipertahankan, sehingga pengguna akan dianggap "baru" oleh server. Dengan berbagi instans, semua komponen bisa menggunakan cookie yang sama tanpa perlu otentikasi ulang.

3. Membagikan instans `CookieRequest` melalui seluruh aplikasi menyederhanakan kode karena semua komponen menggunakan alat yang sama untuk berkomunikasi dengan backend.

4. Setelah pengguna login dan cookie sesi tersimpan, halaman atau komponen lain dapat mengakses status login tersebut melalui instans `CookieRequest`.

### 4. Jelaskan mekanisme pengiriman data mulai dari input hingga dapat ditampilkan pada Flutter.

1. Pengumpulan Data dari Input Pengguna

Pada Flutter, data yang dimasukkan pengguna melalui elemen input seperti TextField atau TextFormField ditangkap dan disimpan dalam variabel atau state. Fungsi `onChanged` mengambil data yang dimasukkan pengguna dan `validator` memvalidasi apakah data sudah sesuai format yang diinginkan.

2. Pengiriman Data ke Backend

Setelah data terkumpul, data dikirim ke backend menggunakan pustaka seperti http atau CookieRequest dalam bentuk HTTP Request. Data dikirim dalam format tertentu seperti JSON, sesuai kebutuhan API. Fungsi `postJson` mengirim data dalam format JSON melalui metode HTTP POST ke endpoint API backend dan `jsonEncode`m engubah data menjadi format JSON agar kompatibel dengan API.

3. Pemrosesan Data di Backend

- Backend menerima request dari Flutter.
- Backend memvalidasi data yang diterima.
- Jika valid, data disimpan dalam database atau diproses sesuai kebutuhan.
- Backend mengirimkan respons ke Flutter, yang biasanya berisi status pengiriman atau data yang telah diolah.

4. Penerimaan Respons di Flutter

Flutter menerima respons dari backend, lalu respons tersebut di-decode menjadi objek atau model untuk diproses lebih lanjut. Fungsi `response` menyimpan data hasil respons dari backenddan `setState` memperbarui UI berdasarkan hasil respons.

5. Menampilkan Data di UI Flutter

Data yang diterima dari backend (misalnya hasil respons atau data baru dari API) ditampilkan kembali ke pengguna melalui widget, seperti Text, ListView, atau DataTable

### 5. Jelaskan mekanisme autentikasi dari login, register, hingga logout. Mulai dari input data akun pada Flutter ke Django hingga selesainya proses autentikasi oleh Django dan tampilnya menu pada Flutter.

#### 1. Register (Pendaftaran Akun Baru)

**Input Data di Flutter:**
1. Pengguna mengisi data akun melalui form input (misalnya `TextFormField`).
2. Data seperti `username`, `password`, dan `confirm_password` dikirimkan ke endpoint Django menggunakan HTTP POST.

**Proses di Django:**
1. Django menerima data pendaftaran melalui endpoint `/auth/register/`.
2. Backend memvalidasi:
- Apakah username sudah ada?
- Apakah password dan confirm_password cocok?
3. Jika validasi berhasil:
- Django menyimpan data pengguna ke database (misalnya, menggunakan model `User` dari Django's Authentication Framework).
- Django mengembalikan respons JSON
4. Jika terjadi kesalahan, Django mengembalikan respons dengan pesan error.

**Respons di Flutter:**
1. Flutter menerima respons dari Django.
2. Jika berhasil, pengguna diberi notifikasi sukses dan diarahkan ke halaman login.

#### 2.  Login (Autentikasi Pengguna)

**Input Data di Flutter:**
1. Pengguna memasukkan `username` dan `password` pada form login.
2. Data dikirimkan ke endpoint Django `/auth/login/` menggunakan HTTP POST.

**Proses di Django:**
1. Django menerima data login dan memvalidasi:
- Apakah username ada di database?
- Apakah password sesuai dengan hashed password yang disimpan?
2. Jika validasi berhasil:
- Django membuat sesi (session) atau token autentikasi (misalnya, JSON Web Token atau session cookie).
- Django mengembalikan respons JSON dengan status berhasil dan informasi sesi/token.
3. Jika validasi gagal, Django mengembalikan pesan error.

**Penyimpanan Token di Flutter:**
1. Flutter menerima respons dari Django.
2. Token disimpan secara lokal di perangkat pengguna, misalnya menggunakan `SharedPreferences` atau `secure_storage`.
3. Jika login berhasil, pengguna diarahkan ke halaman menu utama.

#### 3. Mengakses Menu Setelah Login

**Token Validasi:**
1. Flutter menggunakan token yang disimpan untuk mengakses data dari API Django.
2. Setiap permintaan HTTP ke Django disertai dengan token autentikasi di header.

**Proses di Django:**
1. Django memvalidasi token yang diterima dari permintaan HTTP.
2. Jika token valid, Django memberikan data yang diminta (misalnya, daftar produk atau profil pengguna).
3. Jika token tidak valid, Django mengembalikan pesan error dengan status tidak terautentikasi.

**Penerapan di Flutter:**
1. Jika respons valid, data ditampilkan kepada pengguna.
2. Jika tidak valid, pengguna diarahkan kembali ke halaman login.

#### 4. Logout (Mengakhiri Sesi)

**Proses di Flutter:**
1. Flutter mengirim permintaan HTTP ke endpoint Django `/auth/logout/` menggunakan HTTP POST atau DELETE.
2. Token atau sesi dihapus dari Django.
3. Token lokal di Flutter juga dihapus, biasanya menggunakan `SharedPreferences` atau `secure_storage`.

**Proses di Django:**
1. Django menerima permintaan logout.
2. Django menghapus sesi/token yang terkait dengan pengguna.
3. Django mengembalikan respons JSON

**Penyelesaian di Flutter:**
1. Token dihapus dari perangkat pengguna.
2. Pengguna diarahkan kembali ke halaman login.