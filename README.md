# Tugas 2 PBP F
Nama: Johanes Wisanggeni
NPM: 2206032425

[Aplikasi adaptable](https://toko-jo.adaptable.app/)
[Link aplikasi PaaS PBP](http://johanes-wisanggeni-tugas.pbp.cs.ui.ac.id)
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

# Tugas 5 PBP F

1.	Jelaskan manfaat dari setiap element selector dan kapan waktu yang tepat untuk menggunakannya.
2.	Jelaskan HTML5 Tag yang kamu ketahui.
3.	 Jelaskan perbedaan antara margin dan padding.
4.	 Jelaskan perbedaan antara framework CSS Tailwind dan Bootstrap. Kapan sebaiknya kita menggunakan Bootstrap daripada Tailwind, dan sebaliknya?
5.	 Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).

Jawaban: 

1. Jelaskan manfaat dari setiap element selector dan kapan waktu yang tepat untuk menggunakannya.
•	Selector Universal (*):
Manfaat: Memilih semua elemen dalam dokumen HTML.
Waktu yang Tepat: Saat perlu mempengaruhi semua elemen dalam dokumen.<br>
•	Selector Tag (Element Selector):
Manfaat: Memilih semua elemen dengan nama tag tertentu (misalnya, p untuk paragraf atau h1 untuk judul level 1).
Waktu yang Tepat: Cocok digunakan ketika Anda ingin memengaruhi semua elemen dengan tag tertentu dalam dokumen.<br>
•	Selector Class (.classname):
Manfaat: Memilih semua elemen yang memiliki atribut class dengan nilai tertentu.
Waktu yang Tepat: Berguna ketika Anda ingin memberikan gaya khusus kepada sekelompok elemen dengan class yang sama.<br>
•	Selector ID (#idname):
Manfaat: Memilih elemen dengan atribut id tertentu.
Waktu yang Tepat: Berguna untuk menargetkan elemen spesifik dengan ID tertentu, dan biasanya digunakan hanya sekali per halaman karena ID harus unik.<br>
•	Selector Universal dalam Konteks (descendant selectors, child selectors, sibling selectors):
Manfaat: Memilih elemen berdasarkan hubungannya dengan elemen lain dalam dokumen.
Waktu yang Tepat: Digunakan ketika Anda ingin memilih elemen yang berada dalam hierarki tertentu, seperti elemen anak, elemen saudara, atau elemen yang dalam elemen lain.<br>
•	Selector Pseudo-Class (:hover, :nth-child, dsb.):
Manfaat: Memungkinkan Anda memilih elemen berdasarkan status atau posisi mereka dalam dokumen.
Waktu yang Tepat: Berguna untuk memberikan gaya yang berbeda kepada elemen saat interaksi pengguna terjadi (contoh: mengubah warna teks saat kursor mengarah, atau merubah tampilan elemen ke-n dalam daftar).<br>
•	Selector Pseudo-Element (::before, ::after, dsb.):
Manfaat: Memungkinkan Anda menambahkan isi tambahan ke elemen tanpa harus menyisipkan elemen HTML baru.
Waktu yang Tepat: Berguna saat Anda ingin menambahkan elemen virtual (misalnya, ikon) sebelum atau sesudah elemen yang ada.<br>
Sumber: https://chat.openai.com/c/2f0cc243-7047-46d4-bc2c-f37d1c1feeb9

2. a	Tag untuk membuat hyperlink <br>
html	Tag untuk membuat sebuah dokumen HTML <br>
title	Tag untuk membuat judul dari sebuah halaman <br>
body	Tag untuk membuat tubuh dari sebuah halaman <br>
h1 to h6	Tag untuk membuat heading <br>
p	Tag untuk membuat paragraf <br>
br Memasukan satu baris putus <br>
hr	Tag untuk membuat perubahan dasar kata didalam isi <br>
div	Tag untuk membuat sebuah bagian dalam dokumen <br>
Sumber: https://gilacoding.com/read/tag-tag-pada-html-beserta-fungsinya
  
3.	Margin digunakan untuk menata letak dari sisi luar, sedangkan padding digunakan untuk menata letak dari sisi dalam. Perbedaan lainnya terletak pada warna. Margin biasanya tidak memiliki warna, sedangkan padding bisa menggunakan unsur warna sesuai dengan warna background halamannya.
Sumber: https://www.rumahweb.com/journal/padding-adalah/#:~:text=Secara%20garis%20besar%2C%20margin%20digunakan,sesuai%20dengan%20warna%20background%20halamannya.

4.	Secara umum, Bootstrap lebih difokuskan kepada tingkat responsif dan mobilitas-nya, sedangkan untuk Tailwind lebih mengutamakan utilitasnya. Jika kita bandingkan dari segi responsif, tentu Bootstrap akan lebih unggul dalam hal ini, dikarenakan Bootstrap sangat mementingkan responsif dan mobilitasnya. Namun sayang, Bootstrap memiliki framework yang jauh lebih besar dalam segi size, sehingga memungkinkan untuk mengurangi efisiensi ataupun tidak. Jika kita kembali melihat Tailwind yang masih muda, Tailwind berhasil memikat hati berkat tingkat utilitasnya dan plugins-nya yang memungkinkan  kita untuk bisa lebih bebas untuk men-design UI kita. Sayang, Tailwind masih dalam pengembangan dan mungkin dalam beberapa versi-nya akan memberikan bug.
Sumber: https://dumbways.id/blog/tailwind-vs-bootstrap

5.	Pertama-tama saya menambahkan bootstrap css dan js ke aplikasi. Lalu saya mengkustomisasi halaman login, register, dan tambah inventori dan mengganti background color ke bg-light. Lalu saya juga menambahkan navbar di daftar inventori mengikuti dokumentasi navbar: https://getbootstrap.com/docs/5.3/components/navbar/ yang saya warnai hitam; dan mengganti background colornya juga.

# Tugas 6 PBP F
1.	Jelaskan perbedaan antara asynchronous programming dengan synchronous programming.
2.	Dalam penerapan JavaScript dan AJAX, terdapat penerapan paradigma event-driven programming. Jelaskan maksud dari paradigma tersebut dan sebutkan salah satu contoh penerapannya pada tugas ini.
3.	Jelaskan penerapan asynchronous programming pada AJAX.
4.	Pada PBP kali ini, penerapan AJAX dilakukan dengan menggunakan Fetch API daripada library jQuery. Bandingkanlah kedua teknologi tersebut dan tuliskan pendapat kamu teknologi manakah yang lebih baik untuk digunakan.
5.	Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).

Jawaban:

1.	Pada proses synchronous setiap fungsi dijalankan berurutan, untuk dapat menjalankan fungsi berikutnya maka kita harus menunggu fungsi sebelumnya selesai (blocking). Berbeda dengan proses asynchronous dimana kita tidak perlu menunggu suatu fungsi selesai dijalankan untuk menjalankan fungsi lainnya (non-blocking).
Sumber: https://prosigmaka.com/article/apa-itu-asynchronous-programming/#:~:text=Pada%20proses%20synchronous%20setiap%20fungsi,lainnya%20(non%2Dblocking).

2.	Salah satu teknik pemrograman, yang konsep kerjanya tergantung dari kejadian atau event tertentu. Contoh: Add Product by Ajax di tugas.
Sumber: https://osf.io/3s8tw/download

3.	Penjelasan: (sumber: Tutorial 5)
•	Sebuah event terjadi pada halaman web (contohnya tombol submit data ditekan)
•	Sebuah XMLHttpRequest object dibuat oleh JavaScript
•	XMLHttpRequest object mengirimkan request ke server
•	Server memproses request tersebut
•	Server mengembalikan response kembali kepada halaman web
•	Response dibaca oleh JavaScript
•	Aksi berikutnya akan dipicu oleh JavaScript sesuai dengan langkah yang dibuat (contohnya memperbarui data di halaman tersebut)

4.	Fetch API menyediakan antarmuka JavaScript untuk mengakses dan memanipulasi bagian-bagian protokol, seperti requests dan responses. API ini juga menyediakan metode fetch() global yang menyediakan cara yang mudah dan logis untuk mengambil sumber daya secara asinkronus pada seluruh jaringan.

Tidak seperti XMLHttpRequest yang merupakan API berbasis callback, Fetch API berbasis Promise dan menyediakan alternatif yang lebih baik dan dapat dengan mudah digunakan pada service worker. Fetch API juga mengintegrasikan konsep HTTP tingkat lanjut seperti CORS dan ekstensi lain ke HTTP.

jQuery adalah library yang berisi beberapa fitur berikut:
● Manipulasi HTML/DOM
● Manipulasi CSS
● Methods event HTML
● Efek dan animasi
● AJAX
● Utilities

Menurut saya lebih baik Fetch API, karena API ini merupakan pengganti yang lebih kuat dan fleksibel untuk XMLHttpRequest. Fetch API secara umum digunakan untuk mengimplementasikan AJAX secara lebih mudah daripada AJAX dengan XMLHttpRequest. Fetch API juga mendukung lebih banyak metode HTTP dan header HTTP daripada AJAX biasa.

Sumber: (Slide dan tutorial PBP).

5.	Pertama saya membuat fungsi pada views untuk mengembalikan data JSON. Fungsi ini akan digunakan untuk menampilkan data produk pada HTML dengan menggunakan fetch, lalu saya membuat fungsi pada views untuk menambahkan produk baru ke basis data dengan AJAX. Lalu saya menambahkan routing untuk fungsi get_product_json dan add_product_ajax di urls.py. Lalu saya menampilkan data product dengan Fetch() API dengan mengubah dan menambahkan code (membuat script) di main.html pada main/templates. Lalu saya membuat modal sebagai form untuk menambahkan produk di main.html. Lalu saya membuat fungsi JavaScript baru untuk menambahkan data berdasarkan input ke basis data secara AJAX dengan memanfaatkan modal dengan form. Lalu saya melakukan perintah collectstatic, bertujuan untuk mengumpulkan file static dari setiap aplikasi ke dalam suatu folder yang dapat dengan mudah disajikan pada produksi. 

