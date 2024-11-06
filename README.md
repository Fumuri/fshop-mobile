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

Center: Menyusun widget anaknya di tengah-tengah secara horisontal dan vertikal.

Text: Menampilkan teks statis. Digunakan untuk menampilkan informasi seperti "Welcome to FShop" dan nama item di dalam kartu.

SizedBox: Memberikan ruang atau jarak antar widget. Dalam proyek ini, SizedBox digunakan untuk memberikan jarak vertikal antar elemen.

Card: Membuat tampilan kotak dengan bayangan di bawahnya. Card digunakan untuk InfoCard, menampilkan informasi seperti NPM, Nama, dan Kelas.

Material: Memberikan efek material pada widget dan sering digunakan bersama InkWell untuk efek sentuhan.

InkWell: Menambahkan animasi sentuhan pada widget. Pada proyek ini, InkWell digunakan dalam ItemCard sehingga setiap item dalam grid bereaksi saat disentuh.

Icon: Menampilkan ikon yang mewakili setiap item dalam ItemCard, seperti ikon tambah atau logout.

SnackBar: Menampilkan notifikasi sementara di bagian bawah layar. Dalam proyek ini, digunakan untuk memberi tahu pengguna ketika mereka menekan suatu item.