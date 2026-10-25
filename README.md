# Praktikum8-PBO
# Polimorfisme, Abstract, dan Interface

// Nirina Ariftiyanti
// L0325041

# 1. Studi Kasus Hewan (Inheritance dan Polimorfisme)
Studi kasus ini menunjukkan bagaimana satu pemanggilan method yang sama bisa menghasilkan perilaku berbeda tergantung objek yang dipanggil.
  # 1.1 Kelas Hewan
  Hewan adalah kelas induk (superclass). Kelas ini hanya memiliki satu method, yaitu bersuara(), yang mencetak teks Hewan ini mengeluarkan suara yang tidak       spesifik. Karena hewan secara umum tidak punya suara yang jelas. Method inilah yang nanti ditimpa oleh kelas-kelas turunan.

  # 1.2 Kelas Kucing
  Kucing mewarisi Hewan (extends Hewan). Kelas ini menulis ulang method bersuara() sehingga mencetak Kucing: Meow meow!. Penulisan ulang method milik induk dengan isi yang berbeda disebut method overriding. Konstruktor Kucing hanya memanggil konstruktor Hewan tanpa tambahan apa pun.

  # 1.3 Kelas Anjing
  Anjing juga mewarisi Hewan dan melakukan hal yang sama seperti Kucing, hanya dengan isi yang berbeda: bersuara() mencetak Anjing: Guk guk!. Dengan dua kelas turunan ini, satu induk punya tiga versi perilaku bersuara(): versi umum, versi kucing, dan versi anjing.

  # 1.4 Kelas PoliTester
  PoliTester adalah kelas main yang membuktikan polimorfisme. Program membuat sebuah array bertipe Hewan yang diisi tiga objek berbeda, yaitu Hewan, Kucing, dan Anjing, lalu melakukan perulangan dan memanggil bersuara() pada tiap elemen:

  Hewan[] daftar = { new Hewan(), new Kucing(), new Anjing() };
  for (Hewan h : daftar) {
      h.bersuara();
  }
  
  Walaupun variabel h bertipe Hewan, Java memilih versi bersuara() berdasarkan objek aslinya saat program berjalan. Mekanisme ini disebut dynamic binding dan menjadi inti dari polimorfisme. Outputnya:

  Hewan ini mengeluarkan suara yang tidak spesifik.
  Kucing: Meow meow!
  Anjing: Guk guk!

# 2. Studi Kasus Bangun Datar (Kelas Abstrak)
Studi kasus ini menunjukkan penggunaan kelas abstrak untuk membuat kerangka yang wajib dilengkapi oleh kelas turunannya.
  # 2.1 Kelas BangunDatar
  BangunDatar dideklarasikan sebagai abstract class, sehingga tidak bisa dibuat objeknya secara langsung. Kelas ini punya atribut warna bertipe String yang diisi lewat konstruktor BangunDatar(String warna).
  Di dalamnya ada dua jenis method. Pertama, hitungLuas() yang bersifat abstrak dan bertipe double. Method ini tidak punya isi, sebab rumus luas berbeda untuk tiap bangun, jadi setiap kelas turunan wajib menulisnya sendiri. Kedua, cetakWarna() yang merupakan method biasa dan sudah berisi, yaitu mencetak Warna bangun ini adalah: <warna>. Method ini langsung bisa dipakai semua turunan tanpa perlu ditulis ulang. Perpaduan method abstrak dan method biasa dalam satu kelas adalah ciri khas kelas abstrak.
  
  # 2.2 Kelas Lingkaran
  Lingkaran mewarisi BangunDatar dan menambahkan atribut jariJari bertipe double dengan akses private, sehingga hanya bisa diakses dari dalam kelas itu sendiri (encapsulation).
  Konstruktornya menerima dua parameter, yaitu warna dan jari-jari. Warna diteruskan ke konstruktor induk lewat super(warna), sedangkan jari-jari disimpan di atribut sendiri. Method hitungLuas() yang tadinya abstrak di induk kini diisi dengan rumus luas lingkaran: Math.PI * jariJari * jariJari.
  
  # 2.3 Kelas TesBangunDatar
  TesBangunDatar adalah kelas main yang membuat objek Lingkaran berwarna "Merah" dengan jari-jari 5.0. Program memanggil cetakWarna() yang diwarisi dari BangunDatar, lalu mencetak hasil hitungLuas(). Keluarannya:
  
  Warna bangun ini adalah: Merah
  Luas lingkaran: 78.53981633974483

# 3. Studi Kasus Perangkat Elektronik (Interface)
Studi kasus ini menunjukkan penggunaan interface sebagai kontrak perilaku, serta cara satu kelas memenuhi beberapa kontrak sekaligus.
  # 3.1 Interface AlatElektronik
  AlatElektronik adalah kontrak untuk perangkat elektronik umum. Interface ini hanya mendeklarasikan dua method tanpa isi, yaitu nyalakan() dan matikan(). Kelas apa pun yang mengaku sebagai alat elektronik wajib menyediakan kedua method tersebut.
  
  # 3.2 Interface Kamera
  Kamera adalah kontrak untuk perangkat yang bisa memotret. Isinya hanya satu method, yaitu ambilFoto(). Dengan memisahkannya dari AlatElektronik, kemampuan memotret bisa dipasang ke perangkat apa pun yang membutuhkannya, bukan hanya ke satu jenis perangkat.
  
  # 3.3 Kelas Smartphone
  Smartphone mengimplementasikan AlatElektronik dan Kamera sekaligus (implements AlatElektronik, Kamera). Java tidak mengizinkan sebuah kelas mewarisi dua kelas, tetapi mengizinkan implementasi banyak interface.
  Kelas ini punya atribut merk bertipe String dengan akses private, diisi lewat konstruktor Smartphone(String merk). Ketiga method kontrak diimplementasikan dengan mencetak pesan yang memuat nama merk: nyalakan() mencetak <merk> menyala. Booting OS..., matikan() mencetak <merk> dimatikan. Goodbye., dan ambilFoto() mencetak Cekrek! Foto berhasil disimpan di galeri <merk>.
  
  # 3.4 Kelas TesSmartphone
  TesSmartphone adalah kelas main yang membuat Smartphone bermerk "Samsung", lalu memanggil nyalakan(), ambilFoto(), dan matikan() secara berurutan. Keluarannya:

  Samsung menyala. Booting OS...
  Cekrek! Foto berhasil disimpan di galeri Samsung.
  Samsung dimatikan. Goodbye.

  
