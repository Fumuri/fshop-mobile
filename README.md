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