# Tugas 2 PBP F
Nama: Johanes Wisanggeni
NPM: 2206032425

[Aplikasi adaptable](https://toko-jo.adaptable.app/)
1. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).
Langkah pertama adalah saya membuat repo public toko-jo. Lalu saya membuat direktori lokal toko-jo dan saya inisiasi dengan git. Lalu saya menghubungkan keduanya. Di direktori toko-jo, saya membuat virtual
environment, menyiapkan dan memasang dependencies, kemudian membuat proyek django toko-jo. Lalu saya menambahkan * pada ALLOWED_HOSTS di settings.py untuk keperluan deployment. Lalu saya
menambahkan .gitignore di direktori toko-jo untuk bersiap-siap. Lalu saya membuat aplikasi main di virtual environment dan mendaftarkannya ke proyek. Lalu saya membuat berkas main.html di dalam direktori templates yang mana templates berada di dalam direktori main; main.html berfungsi sebagai template fungsi pada views.py. Kemudian saya mengubah berkas models.py di dalam main sesuai keperluan dan membuat serta
mengaplikasikan migrasi model. Saya kemudian mengimplementasikan fungsi show_main di dalam views.py (terletak di dalam main) untuk me-render template dengan data yang telah diambil dari model. Saya kemudian
mengubah main.html dan memanfaatkan sintaks django untuk menampilkan nilai dari variabel yang telah didefinisikan dalam context. Saya kemudian mengatur routing url agar aplikasi main dapat diakses melalui
web browser. Cara saya mengatur routing url yaitu dengan mendefinisikan pola url di urls.py yang berada di direktori main, kemudian saya menambahkan rute URL dalam urls.py proyek untuk menghubungkannya ke
tampilan main; dengan cara menambahkan rute URL untuk mengarahkan ke tampilan main di dalam variabel urlpatterns (berada di urls.py proyek). Lalu saya add, commit dan push ke repo toko-jo, dan saya deploy di
adaptable dengan men-connect ke repo toko-jo, memilih deployment branch (main), memilih template deployment, memilih tipe basis data, melakukan start command dengan command:
python manage.py migrate && gunicorn toko_jo.wsgi, memilih nama dan domain web aplikasi, kemudian men-deploy aplikasi saya.

2. Buatlah bagan yang berisi request client ke web aplikasi berbasis Django beserta responnya dan jelaskan pada bagan tersebut kaitan antara urls.py, views.py, models.py, dan berkas html.
![MVT_rev](https://github.com/johaneswisa/toko-jo/assets/119523455/315774d9-75e9-4a93-8c9f-c9a44802b591)

Pada bagan, user me-request sebuah resource ke django. Django bekerja sebagai sebuah pengontrol dan akan mengecek resource yang tersedia di url. Kemudian pergi ke function yang match di views.py dan function di
views.py akan mengambil web request dari urls.py dan memberi response web ke template (berkas html). Mungkin akan berinteraksi pula dengan models.py yaitu pergi ke data access layer di models.py. views kemudian
me-render template dan django me-respond kembali ke user dan mengirim template sebagai response.

3. Jelaskan mengapa kita menggunakan virtual environment? Apakah kita tetap dapat membuat aplikasi web berbasis Django tanpa menggunakan virtual environment?
Kita menggunakan virtual environment agar dependencies proyek-proyek yang berbeda bisa terpisah satu sama lain dengan membuat virtual environment python yang terisolasi untuk mereka. Untuk pertanyaan kedua,
sebenarnya bisa-bisa saja, namun akan repot apabila dependencies proyek-proyek berbeda, misalnya satu proyek memakai django versi 3.4 dan yang satu lagi 3.10.

4. Jelaskan apakah itu MVC, MVT, MVVM dan perbedaan dari ketiganya.
MVC (Model View Controller): Software design pattern yang digunakan untuk meng-implement UI dan memberi penekanan pada memisahkan representasi data dari komponen-komponen yang berinteraksi dan memroses data.
MVT (Model View Template): Design pattern yang mirip MVC namun bagian pengontrolnya dilakukan oleh framework.
MVVM (Model View ViewModel): Design pattern yang memiliki kesamaan dengan MVP(Model — View — Presenter) namun MVVM memisahkan logic presentasi data (views atau UI) dari bagian core business logic aplikasi.
Beberapa perbedaan ketiganya:
-Di MVC dan MVT, user input di-handle oleh controller. Di MVVM, user input di-handle oleh view dan view menjadi entry point aplikasi.
-Di MVC, controller dan view memiliki hubungan one-to-many. Satu controller bisa memilih dari view berbeda-beda tergantung operasi. MVT bagian controller dilakukan oleh framework. Sementara di MVVM,
beberapa view bisa di-map oleh satu ViewModel.

# Tugas 3 PBP F

1. Apa perbedaan antara form POST dan form GET dalam Django?
POST: POST digunakan untuk mengirim data ke suatu server untuk membuat/meng-update resource.
GET: GET digunakan untuk meminta data dari resource tertentu.
Notes tentang GET:
Permintaan GET dapat di-cache
Permintaan GET tetap ada dalam riwayat browser
Permintaan GET dapat di-bookmark
Permintaan GET tidak boleh digunakan saat menangani data sensitif
Permintaan GET memiliki batasan panjang
Permintaan GET hanya digunakan untuk meminta data (tidak memodifikasi)
Notes tentang POST:
Permintaan POST tidak pernah di-cache
Permintaan POST tidak tersimpan dalam riwayat browser
Permintaan POST tidak dapat dibookmark
Permintaan POST tidak memiliki batasan panjang data
sumber: https://www.w3schools.com/tags/ref_httpmethods.asp

2. Apa perbedaan utama antara XML, JSON, dan HTML dalam konteks pengiriman data?
XML lebih cocok untuk data yang memerlukan struktur yang sangat terinci dan validasi yang ketat, sementara JSON sering digunakan untuk pertukaran data yang lebih sederhana dan cepat. HTML, di sisi lain, digunakan untuk membangun halaman web dan tampilan konten di peramban web.

3. Mengapa JSON sering digunakan dalam pertukaran data antara aplikasi web modern?
Dapat menyimpan data dalam bentuk array dan menjadikan transfer data menjadi lebih mudah.
Sintaks yang lebih ringan dan berukuran lebih kecil.
Mendukung beberapa bahasa pemrograman lain.
Lebih cepat dalam parsing data di sisi server.
sumber: https://www.dicoding.com/blog/apa-itu-json/

4. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).
Pertama-tama saya mengatur routing dari main/ ke / agar lebih sesuai dengan konvensi yang ada. Lalu saya mengimplementasi skeleton sebagai
kerangka views agar dapat memastikan adanya konsistensi dalam desain situs web saya serta memperkecil kemungkinan terjadinya redundansi kode. Lalu saya membuat sebuah form sederhana untuk menginput data barang pada aplikasi sehingga nantinya saya dapat menambahkan data baru untuk ditampilkan pada halaman utama; data item ditampilkan pada html. Lalu di views.py folder main saya mengimplementasi fungsi-fungsi agar dapat mengembalikan data dalam bentuk XML, JSON, dan mengembalikan data berdasarkan ID dalam bentuk XML dan JSON. Lalu saya membuat routing URL untuk masing-masing views di urls.py.

5. Mengakses kelima URL di poin 2 menggunakan Postman, membuat screenshot dari hasil akses URL pada Postman, dan menambahkannya ke dalam README.md.

![Alt text](<Screenshot (328).png>)
![Alt text](<Screenshot (327).png>)
![Alt text](<Screenshot (326).png>)
![Alt text](<Screenshot (325).png>)
![Alt text](<Screenshot (324).png>)

# Tugas 4 PBP F
1.	Apa itu Django UserCreationForm, dan jelaskan apa kelebihan dan kekurangannya?
From tutorial 3: UserCreationForm adalah impor formulir bawaan yang memudahkan pembuatan formulir pendaftaran pengguna dalam aplikasi web. Dengan formulir ini, pengguna baru dapat mendaftar dengan mudah di situs web Anda tanpa harus menulis kode dari awal. 
Kelebihan: 
-Mudah digunakan
Tinggal di-import saja.
-Terintegrasi dengan database
Data yang dimasukkan melalui formulir akan otomatis disimpan dalam database pengguna.
-Validasi
Terdapat validasi bawaan seperti verifikasi email yang unik, validasi kata sandi yang kuat, dll.
Kekurangan:
-Tampilan default sederhana, bila ingin lebih estetis perlu menambahkan css/html lagi
-Tidak memenuhi fitur tertentu secara bawaan, UserCreationForm tidak selalu memenuhi semua kebutuhan aplikasi, kita harus menambahkan bidang-bidang kustom ke formulir atau menggunakan Custom User model.

2.	Apa perbedaan antara autentikasi dan otorisasi dalam konteks Django, dan mengapa keduanya penting?
Secara umum, autentikasi adalah proses memverifikasi siapa anda, otorisasi adalah proses memverifikasi bahwa anda punya akses ke sesuatu. 
Dalam konteks Django, Django memiliki sistem autentikasi bawaan yang mencakup pengguna, sesi, cookie, dan berbagai alat autentikasi pihak ketiga yang dapat diintegrasikan. Django juga memiliki sistem otorisasi yang memungkinkan pengembang untuk mendefinisikan peran dan hak akses pengguna dengan sangat detail, dapat mengendalikan akses ke tampilan (views), model, dan sumber daya lainnya dalam aplikasi. Keduanya penting dalam menjaga keamanan aplikasi web dan membantu melindungi data sensitif dan mencegah akses yang tidak sah.

3.	Apa itu cookies dalam konteks aplikasi web, dan bagaimana Django menggunakan cookies untuk mengelola data sesi pengguna?
Cookies adalah berkas kecil yang berisi data yang dikirim oleh server web dan disimpan di sisi klien (browser), untuk kemudian dikirim kembali oleh browser saat page requests di masa depan.
Django menyediakan metode bawaan untuk men-set dan mem-fetch cookie.
Metode set_cookie() digunakan untuk men-set cookie dan metode get() digunakan untuk meng-get cookie.
Array request.COOKIES['key'] juga dapat digunakan untuk mendapatkan nilai cookie.

4.	Apakah penggunaan cookies aman secara default dalam pengembangan web, atau apakah ada risiko potensial yang harus diwaspadai?
Secara umum, cookie sangat aman bila diterapkan dengan benar. Namun, ada beberapa cara yang bisa dilakukan oknum jahat untuk mencuri cookie. Beberapa security concerns ini adalah: Man-in-the-middle attacks, CSRF attacks, XSS attacks. 



5.	Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).
Pertama-tama, saya membuat fungsi dan form registrasi menggunakan UserCreationForm di views.py. Kemudian saya membuat register.html sebagai template, dan mengimpor dan menambahkan path url fungsi di urls.py, agar dapat diakses. Kemudian saya melakukan hal yang serupa seperti di atas untuk fungsi login, namun saya meng-import authenticate dan login agar digunakan untuk melakukan autentikasi dan login jika autentikasi berhasil; dan membuat perubahan bersesuaian di fungsi login views. Kemudian saya membuat fungsi logout dengan meng-import logout di views dan menggunakan logout(request) untuk menghapus sesi pengguna yang saat ini masuk dan return redirect('main:login') untuk mengarahkan pengguna ke halaman login dalam aplikasi Django di fungsi logout. Saya menambahkan button logout di main.html dan menambahkan path url di urls. Lalu saya menambahkan @login_required(login_url='/login') di views untuk mengharuskan pengguna masuk (login) sebelum dapat mengakses suatu halaman web. Kemudian saya menggunakan cookies dengan menambahkan data last login dan menampilkannya ke halaman main. Caranya adalah saya menambahkan cookie yang bernama last_login untuk melihat kapan terakhir kali pengguna melakukan login di fungsi login_user di views, kemudian saya menambahkan informasi cookie last_login di show_main agar ditampilkan di halaman web. Saya kemudian mengimplement code di logout_user untuk menghapus cookie last_login saat pengguna melakukan logout, dan menambahkan potongan kode di main.html untuk menampilkan data last login. Kemudian saya membuat dua akun pengguna dengan masing-masing tiga dummy data menggunakan model yang telah dibuat pada aplikasi sebelumnya untuk setiap akun di lokal. Kemudian saya akan menghubungkan Item dengan User. Saya menambahkan code user = models.ForeignKey(User, on_delete=models.CASCADE) di class Item di models untuk menghubungkan satu produk dengan satu user melalui sebuah relationship, dimana sebuah produk pasti terasosiasikan dengan seorang user. Kemudian saya menambahkan code di main/views agar ada Parameter commit=False yang digunakan pada potongan kode diatas berguna untuk mencegah Django agar tidak langsung menyimpan objek yang telah dibuat dari form langsung ke database. Hal tersebut memungkinkan untuk memodifikasi terlebih dahulu objek tersebut sebelum disimpan ke database. Pada kasus ini, field user akan terisi dengan objek User dari return value request.user yang sedang terotorisasi untuk menandakan bahwa objek tersebut dimiliki oleh pengguna yang sedang login. Kemudian saya mengubah show_main agar menampilkan objek Item yang terasosiasikan dengan pengguna yang sedang login dan menampilkan username pengguna yang login dengan request.user.username. Kemudian saya melakukan migrasi model dan mengaplikasikan migrasi. 
