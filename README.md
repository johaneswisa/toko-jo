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


