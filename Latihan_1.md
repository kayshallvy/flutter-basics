# Tugas Latihan 1

**1. Bagaimana cara membuat project Flutter menggunakan terminal/cmd?**

Jawaban:
Pertama buka terminal atau cmd, lalu ketikkan perintah: `flutter create nama_project` (misalnya: `flutter create project_flutter_pertama`).

**2. Apa aturan dalam memberikan nama project pada Flutter?**

Jawaban:
Aturan dalam memberikan nama project adalah:
- Semua huruf kecil.
- Bila terdapat lebih dari 1 kata, dihubungkan dengan karakter underscore (`_`).

**3. Apa saja folder yang secara khusus disiapkan oleh Flutter untuk menjalankan aplikasi pada platform tertentu?**

Jawaban
Folder yang secara khusus disiapkan adalah `android`, `ios`, `linux`, `macos`, `web`, dan `windows`.

**4. Apa fungsi dari folder .dart_tools dan .idea?**

Jawaban:
- Folder `.idea` menyimpan beberapa konfigurasi untuk Android Studio.
- Folder `.dart_tool` berisi konfigurasi dart package yang di-generate oleh flutter.

**5. Bagaimana cara membuka project Flutter menggunakan Visual Studio Code?**

Jawaban:
Untuk menggunakan Visual Studio Code, buka terminal,  masuk dulu ke folder project dengan perintah `cd nama_project_kamu`. Setelah itu ketik perintah `code .` lalu enter.
Cara lainnya adalah jika menggunakan VS Code untuk mengenerate project langsung (menggunakan CTRL/CMD + Shift + P -> Flutter: New Project), otomatis folder project flutter akan terbentuk dan dibuka oleh vscode.

**6. Mengapa kita perlu memastikan Android SDK terinstall untuk menjalankan aplikasi Flutter di sistem operasi Android?**

Jawaban:
Karena tools Android SDK dibutuhkan untuk me-manage Android Emulator, mengkompilasi file dart agar disuntikkan menjadi aplikasi asli android, serta memungkinkan flutter untuk mem-build dan me-run project ke Android. 

**7. Apa langkah-langkah untuk mengatasi masalah "Android Toolchain error" pada perintah flutter doctor?**

Jawaban:
Langkah-langkahnya adalah:
1. Download dan Install Android Studio.
2. Buka Android Studio.
3. Buka SDK Manager (Pilih *More Actions* -> klik *SDK Manager*).
4. Pilih Tab *SDK Tools*, lalu centang `Android SDK Command-line tools` dan install.
5. Setelah terinstall, buka terminal lagi dan jalankan perintah `flutter doctor --android-licenses`, lalu ketik `y` lalu enter sampai semua lisensi diterima.

**8. Bagaimana cara menambahkan Android SDK Command-line tools melalui Android Studio?**

Jawaban:
Buka Android Studio, klik *More Actions*, lalu pilih *SDK Manager*. Kemudian pilih pada Tab *SDK Tools*, centang opsi `Android SDK Command-line Tools`, dan klik OK/Apply untuk mendownloadnya.

**9. Apa fungsi dari file .gitignore dalam struktur folder Flutter?**

Jawaban:
File `.gitignore` berisi list folder atau file yang tidak akan ikut masuk kedalam git repository ketika kita melakukan push ke repository.

**10. Mengapa file pubspec.yaml sangat penting dalam pengembangan aplikasi Flutter?**

Jawaban:
Karena file ini memungkinkan kita untuk mengelola sebagian besar dependensi project (seperti memanggil package pihak ketiga dari pub.dev) serta mengkonfigurasi asset lain seperti font atau gambar yang ingin import.

**11. Apa yang dimaksud dengan widget dalam konteks Flutter?**

Jawaban:
Widget adalah blok penyusun UI yang dapat kita lihat di layar. Segala hal yang menjadi tampilan layar pada aplikasi Flutter disusun dari widget, hingga membentuk "Widget Tree".

**12. Bagaimana pewarisan (inheritance) digunakan dalam pembuatan widget Flutter?**

Jawaban:
Pewarisan digunakan dengan membuat class baru yang mewarisi class yang sudah disediakan oleh flutter (melalui kata kunci `extends`). Misalnya `class MyApp extends StatelessWidget`. Dengan begitu, kita mendapatkan fitur class dasar tersebut, lalu wajib mengimplementasikan method `build` untuk menggambarkan UI-nya.

**13. Apa peran widget MaterialApp dalam pembuatan aplikasi Flutter?**

Jawaban:
MaterialApp adalah widget yang disediakan flutter melalui class `material.dart` yang digunakan sebagai wrapper UI berdesain material. Widget ini memiliki argumen `home` untuk menampung widget lain (misal Scaffold) agar nantinya diteruskan ke widget tree kemudian dieksekusi dengan `runApp`.

**14. Mengapa kita membutuhkan fungsi runApp untuk menjalankan aplikasi Flutter?**

Jawaban:
Karena fungsi `runApp()` bertugas untuk menjalankan aplikasi flutter setelah aplikasi android atau ios di-boot. Ia akan mengambil widget tree (root aplikasi) dan menggambarnya (render) ke kanvas atau layar device.

**15. Apa kegunaan widget Scaffold dalam struktur aplikasi Flutter?**

Jawaban:
Scaffold berguna untuk memberikan tampilan visual yang tertata dengan mengimplementasikan tata letak dasar material design. Scaffold membagi layar ke bagian-bagian khusus seperti untuk AppBar, body, floating action button, dsb.

**16. Bagaimana cara menambahkan app bar dan body pada widget Scaffold?**

Jawaban:
Dengan mengisikan argumen (named argument) `appBar` dan `body` pada Scaffold. 
Contohnya:
```dart
Scaffold(
   appBar: AppBar(title: const Text('Coding Flutter')),
   body: const Text('Ini adalah body content')
)
```

**17. Apa perbedaan antara Stateless Widget dan Stateful Widget?**

Jawaban:
- Stateless Widget adalah widget yang tidak memiliki state. Tampilan UI-nya fix (statis) dan render bergantung sepenuhnya pada data ketika widget itu dipanggil/diinisialisasi pertama kali.
- Stateful Widget adalah widget yang memiliki internal state di dalamnya. Data/state tersebut bisa diubah dengan metode `setState()`, sehingga widget bisa di-render ulang secara mandiri ketika datanya berubah.

**18. Mengapa Stateful Widget disebut memiliki state internal?**

Jawaban:
Karena di dalam class `StatefulWidget` dipasangkan dengan class `State` yang menyimpan data atau informasi widget secara mandiri (local). Karena memiliki state tersebut, UI-nya dapat memanggil metode `setState()` untuk memberitahu flutter agar menjalankan ulang `build()` dengan state baru yang diperbarui.

**19. Berikan contoh penggunaan Stateless Widget dalam pembuatan aplikasi Flutter.**

Jawaban:
Contoh yang umum adalah widget yang hanya menampilkan teks statis seperti instruksi, misalnya:
```dart
class ShowTextWidget extends StatelessWidget {
  final String text;
  const ShowTextWidget({super.key, required this.text});

  @override
  Widget build(BuildContext context) {
    return Text(text);
  }
}
```

**20. Berikan contoh penggunaan Stateful Widget dalam pembuatan aplikasi Flutter beserta alasan penggunaannya.**

Jawaban:
Contoh:
```dart
class ChangeTimeWidget extends StatefulWidget {
  const ChangeTimeWidget({super.key});

  @override
  State<ChangeTimeWidget> createState() => _ChangeTimeWidgetState();
}

class _ChangeTimeWidgetState extends State<ChangeTimeWidget> {
  DateTime time = DateTime.now();

  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        Text('Jam Sekarang: $time'),
        ElevatedButton(
          onPressed: () {
            setState(() { time = DateTime.now(); });
          },
          child: const Text('Perbarui Waktu'),
        ),
      ],
    );
  }
}
```
Alasan Penggunaan: Widget di atas membutuhkan stateful widget karena ia menyimpan data/informasi jam sekarang yang terus berubah saat user menekan "Perbarui Waktu". Saat tombol dipanggil bersama `setState()`, internal state-nya akan berubah dan layarnya berhasil merepresentasikan waktu yang baru, tanpa me-rebuild widget lain secara acak.
