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