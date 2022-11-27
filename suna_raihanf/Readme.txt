NOTE : "FILE DIBUAT ZIP DAN MENJADI 2 BAGIAN KARENA GITHUB TIDAK BISA MENAMPUNG FILE LEBIH DARI 100 SERTA >25MB"
NOTE : "UNTUK DIJALANKAN FILE PERLU DIGABUNG TERLEBIH DAHULU"

Raihan Ferdyanza 2015061085 - SUNA

**Penjelasan Umum :

Rusunawa (Rumah Susun Sederhana Sewa) merupakan fasilitas yang sudah menjadi kebutuhan yang sangat penting bagi mahasiswa  meliputi kebutuhan rumah yang layak dan terjangkau bagi mahasiswa di Bandarlampung. 
Mengingat banyaknya jumlah mahasiswa yang berkunjung di masa pandemi ini, maka masalah  dalam pengelolaan informasi persediaan kamar, spesifikasi kamar, keamanan,dan pra-sarana menjadi sangat penting. 
Oleh karena itu, perlu kiranya dibuat sebuah sistem informasi Pemesanan. Sistem Perangkat lunak Pemesanan Rusunawa Unila (SUNA) berguna dalam mengelola segala informasi berkaitan Rusunawa,seperti pengelolaan informasi pemesan rusunawa yaitu nama,nomor hp,nik serta lama tinggal pemesan.

**Cara Menjalankan di local :

Aplikasi ini dapat dijalankan di local dengan cara sebagai berikut, yaitu :
1. Memindahkan folder suna_raihanf yang sudah disatukan ke htdocs yang berada di xampp
2. Menjalankan XAMPP serta mengaktifkan apache dan mysql
3. Memastikan perangkat terhubung dengan suatu jaringan
4. Memeriksa ip terkait dengan perangkat yang terhubung menggunakan ip config pada cmd
5. Menggunakan visual studio code untuk membuka direktori terkait
6. Menjalankan terminal yang ada di visual studio code
7. Menjalankan command php artisan serve --host *ip* --port 8000
8. Memastikan perangkat dapat membuka program web dengan menggunakan ip dan port tersebut

**Design Database :

Tabel yang dibuat yaitu Pereservasi dengan kolomnya yaitu id,nama,no_hp,nik,dan lama_tinggal.
Environment dan model yang digunakan dalam database mysql phpmyadmin ini lebih jelasnya yaitu :

APP_NAME=Laravel
APP_ENV=local
DB_DATABASE=laravel
DB_USERNAME=root
DB_PASSWORD=

class Pereservasi extends Model
{
    use HasFactory;
    protected $table = 'pereservasi';
    protected $fillable = ['nama','no_hp','nik','lama_tinggal'];
}

**Routes yang digunakan :

Route::get('/', function () {
    return view('welcome');
});
Route::get('/dashboard', function () {
    return view('dashboard');
})->middleware(['auth', 'verified'])->name('dashboard');
require _DIR_.'/auth.php';
Route::get('/pereservasi/about', function () {
    return view('pereservasi.about');
});
Route::get('/profile', function () {
    return view('profile');
});
Route::get('/pereservasi/contact', function () {
    return view('pereservasi.contact');
});
Route::get('/mahasiswa/index', [MahasiswaController::class, 'index'])->name('mahasiswa.index');
Route::get('/pereservasi', [PereservasiController::class, 'create'])->name('pereservasi.create');
Route::post('/pereservasi/store', [PereservasiController::class, 'store'])->name('pereservasi.store');
Route::get('/pereservasi/index', [PereservasiController::class, 'index'])->name('pereservasi.index');
Route::get('/pereservasi/{pereservasi}', [PereservasiController::class, 'show'])->name('pereservasi.show');
Route::get('/pereservasi/edit/{pereservasi}', [PereservasiController::class, 'edit'])->name('pereservasi.edit');
Route::put('/update/pereservasi/show/{pereservasi}', [PereservasiController::class, 'update'])->name('pereservasi.update');
Route::delete('/delete/pereservasi/show/{pereservasi}', [PereservasiController::class, 'delete'])->name('pereservasi.delete');


