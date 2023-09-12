# Tugas 2 PBP F
[Aplikasi adaptable](https://toko-jo.adaptable.app/)
1. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).
Langkah pertama adalah saya membuat repo public toko-jo. Lalu saya membuat direktori lokal toko-jo dan saya inisiasi dengan git. Lalu saya menghubungkan keduanya. Di direktori toko-jo, saya membuat virtual
environment, menyiapkan dan memasang dependencies, kemudian membuat proyek django toko-jo. Lalu saya menambahkan * pada ALLOWED_HOSTS di settings.py untuk keperluan deployment. Lalu saya
menambahkan .gitignore di direktori toko-jo untuk bersiap-siap. Lalu saya membuat aplikasi main di virtual environment dan mendaftarkannya ke proyek. Lalu saya membuat berkas main.html di dalam direktori templates
yang mana templates berada di dalam direktori main; main.html berfungsi sebagai template fungsi pada views.py. Kemudian saya mengubah berkas models.py di dalam main sesuai keperluan dan membuat serta
mengaplikasikan migrasi model. Saya kemudian mengimplementasikan fungsi show_main di dalam views.py (terletak di dalam main) untuk me-render template dengan data yang telah diambil dari model. Saya kemudian
mengubah main.html dan memanfaatkan sintaks django untuk menampilkan nilai dari variabel yang telah didefinisikan dalam context. Saya kemudian mengatur routing url agar aplikasi main dapat diakses melalui
web browser. Cara saya mengatur routing url yaitu dengan mendefinisikan pola url di urls.py yang berada di direktori main, kemudian saya menambahkan rute URL dalam urls.py proyek untuk menghubungkannya ke
tampilan main; dengan cara menambahkan rute URL untuk mengarahkan ke tampilan main di dalam variabel urlpatterns (berada di urls.py proyek). Lalu saya add, commit dan push ke repo toko-jo, dan saya deploy di
adaptable dengan men-connect ke repo toko-jo, memilih deployment branch (main), memilih template deployment, memilih tipe basis data, melakukan start command dengan command:
python manage.py migrate && gunicorn toko_jo.wsgi, memilih nama dan domain web aplikasi, kemudian men-deploy aplikasi saya. 
