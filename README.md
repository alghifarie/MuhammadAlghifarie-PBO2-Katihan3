# MuhammadAlghifarie-PBO2-Katihan3


<dependency>
    <groupId>org.xerial</groupId>
    <artifactId>sqlite-jdbc</artifactId>
    <version>3.36.0.3</version>
</dependency>
Kompilasi dan Jalankan: Anda bisa mengompilasi dan menjalankan program menggunakan IDE (seperti IntelliJ IDEA atau Eclipse) atau terminal.
Deskripsi Kelas dan Metode
1. Konstruktor DataBaseHelper()
Konstruktor ini membuat koneksi ke database SQLite dengan nama file kontak.db. Jika file database tersebut tidak ada, SQLite akan otomatis membuatnya. Setelah itu, konstruktor ini akan memanggil metode createTable() untuk memastikan bahwa tabel kontak sudah ada di database.

2. Metode createTable()
Metode ini digunakan untuk membuat tabel kontak dengan kolom-kolom berikut:

id: INTEGER PRIMARY KEY AUTOINCREMENT
nama: TEXT NOT NULL
nomor: TEXT NOT NULL
kategori: TEXT NOT NULL
Tabel hanya akan dibuat jika belum ada.

3. Metode tambahKontak(String nama, String nomor, String kategori)
Metode ini digunakan untuk menambahkan kontak baru ke dalam tabel kontak. Kontak terdiri dari nama, nomor, dan kategori. Metode ini menggunakan PreparedStatement untuk menghindari SQL injection.

4. Metode hapusKontak(int id)
Metode ini digunakan untuk menghapus kontak berdasarkan ID yang diberikan. ID kontak yang ingin dihapus akan digunakan dalam query SQL untuk menghapus data yang sesuai.

5. Metode updateKontak(int id, String nama, String nomor, String kategori)
Metode ini digunakan untuk memperbarui data kontak yang sudah ada berdasarkan ID yang diberikan. Anda bisa memperbarui nama, nomor, dan kategori dari kontak yang dimaksud.

6. Metode getKontakList()
Metode ini akan mengambil semua kontak yang ada dalam tabel kontak dan mengembalikannya dalam bentuk List<String[]>. Setiap elemen dalam list ini adalah array yang berisi data kontak dalam format [id, nama, nomor, kategori].

Contoh Penggunaan
java
// Membuat instance DataBaseHelper
DataBaseHelper dbHelper = new DataBaseHelper();

// Menambahkan kontak baru
dbHelper.tambahKontak("John Doe", "081234567890", "Teman");

// Menghapus kontak berdasarkan ID
dbHelper.hapusKontak(1);

// Memperbarui kontak berdasarkan ID
dbHelper.updateKontak(2, "Jane Doe", "089876543210", "Keluarga");

// Mengambil semua kontak dan menampilkan data kontak
List<String[]> kontakList = dbHelper.getKontakList();
for (String[] kontak : kontakList) {
    System.out.println("ID: " + kontak[0] + ", Nama: " + kontak[1] + ", Nomor: " + kontak[2] + ", Kategori: " + kontak[3]);
}
