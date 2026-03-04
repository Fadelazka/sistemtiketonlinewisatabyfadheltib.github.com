HTML adalah kerangka website. Setiap bagian punya peran masing-masing.
•	<nav class="navbar">
Bagian navigasi di atas. Ada logo DDELTIKET! dan tools menu: Beranda, Destinasi, Paket, Kontak, dan tombol Masuk. Semua bisa diklik dan akan membawa si user ke bagian tertentu atau membuka form login.
•	<section class="hero">
Hero section (bagian depan). Ada teks yang bisa berubah-ubah (efek mengetik). Fungsinya menarik perhatian pengguna dan memberi kesan pertama.
•	<h2 class="section-title">Destinasi Populer</h2>
Judul untuk bagian destinasi. Di bawahnya ada container (#destinasiContainer) yang nantinya diisi kartu destinasi secara otomatis oleh JavaScript.

•	<div class="destinasi-container" id="destinasiContainer">
Tempat menampung kartu-kartu destinasi. Setiap kartu berisi gambar, nama, lokasi, harga, dan ada tombol "Pesan Sekarang" bisa diklik buat memilih destinasi.
•	<section class="paket-section">
Bagian paket wisata. Mirip dengan destinasi, tapi khusus menampilkan paket-paket seperti "Paket Keluarga", "Paket Romantis", dll.
•	<section class="order-panel">
Panel pemesanan utama. Terdiri dari dua:
o	Kiri: Form untuk memilih destinasi, tanggal kunjungan, jumlah tiket, dan opsi tambahan (pemandu, makan siang).
o	Kanan: Ringkasan pesanan yang langsung berubah saat pengguna memilih atau mengubah jumlah tiket. Ada tombol "Pesan Sekarang".
•	<section class="kontak-section">
Bagian kontak di bawah. Menampilkan alamat, nomor telepon, email, dan Instagram.
•	Modal (#destinasiModal dan #loginModal)
Dua  dialog yang muncul di tengah :
o	Modal destinasi: Muncul saat pengguna klik "Pesan Sekarang" di kartu destinasi. Menampilkan deskripsi singkat destinasi dan form pemesanan cepat.
o	Modal login: Muncul saat tombol "Masuk" diklik. Tetapi hanya Simulasi login sederhana.
•	Toast (#toast)
Kotak notifikasi kecil yang muncul sebentar di bawah layar, misalnya "Pesanan berhasil" atau "Pilih destinasi dulu".

 CSS – Tampilan dan  style web

CSS mengatur bagaimana semua elemen terlihat keren dan kece.
•	Reset (* { margin:0; padding:0; box-sizing:border-box; })
Menghilangkan jarak default browser agar tampilan konsisten.
•	body
Mengatur font (Quicksand), warna latar biru muda, dan warna teks gelap. Nuansa fresh dan nyaman dibaca.
•	.navbar
Navbar dibuat sticky (tetap di atas saat scroll), putih dengan bayangan tipis. Menu diberi jarak dan efek hover berubah warna biru.
•	.hero
Gambar latar dengan lapisan gelap, teks putih dan besar. Ada efek kursor berkedip (@keyframes blink) untuk mempercantik animasi mengetik.
•	.section-title
Setiap judul section punya garis oranye di bawahnya, biar keliatan rapi dan konsisten.
•	Kartu destinasi (.card)
Kartu putih dengan sudut membulat, bayangan halus. Saat di-hover, kartu naik sedikit dan tepinya berubah oranye. Efek ini memberi kesan interaktif.
•	.card-img
Gambar di kartu. Masing-masing destinasi punya gambar latar yang berbeda (disesuaikan dengan data-id).
•	Tombol (.btn-card, .btn-order, .btn-outline)
Tombol berwarna oranye atau biru dengan sudut membulat. Efek hover menggelapkan atau membesarkan tombol, memberi respons visual saat diklik.
•	Panel pemesanan (.order-panel)
Latar putih, bayangan di atas, dan dua kolom (grid). Input dan select punya border abu-abu yang berubah oranye saat fokus, memudahkan pengguna melihat sedang mengisi apa.
•	Ringkasan (.order-summary)
Latar biru muda, border, dan garis putus-putus pemisah item. Total harga ditampilkan besar agar terlihat jelas.
•	Modal (.modal)
Latar gelap transparan, konten di tengah dengan latar putih dan sudut membulat. Ada tombol silang untuk menutup.
•	Toast (.toast)
Kotak notifikasi di tengah bawah, awalnya tersembunyi, muncul saat ada aksi.
•	Media query (@media (max-width:800px))
Untuk layar kecil (HP), panel dua kolom berubah jadi satu kolom, dan ukuran teks hero mengecil. Website jadi responsif.

JavaScript – Interaktivitas
JavaScript yang membuat website ini hidup. Semua logika ada di sini.
Data
•	destinations – Array berisi daftar destinasi (id, nama, lokasi, harga, rating, emoji, deskripsi).
•	paketWisata – Array berisi daftar paket wisata (nama, harga, ikon, fitur).
Kedua array ini ibarat katalog produk yang akan ditampilkan.
Fungsi-Fungsi Utama
•	renderCards()
Membuat kartu destinasi satu per satu dari data destinations. Setiap kartu diberi gambar, nama, lokasi, harga, dan tombol "Pesan Sekarang".
o	Jika area kartu (selain tombol) diklik, destinasi akan dipilih di panel utama dan halaman akan scroll ke panel pemesanan.
o	Jika tombol "Pesan Sekarang" diklik, akan membuka modal detail destinasi.
•	renderPaket()
Sama seperti renderCards, tapi untuk paket wisata. Tombol "Lihat Detail" hanya menampilkan notifikasi bahwa fitur belum tersedia.
•	populateSelect()
Mengisi dropdown "Pilih Destinasi" di panel utama dengan opsi dari data destinasi. Pengguna bisa memilih destinasi lewat dropdown.
•	setSelectedDest(dest)
Menyimpan destinasi yang dipilih (selectedDest), meng-update dropdown, lalu memanggil updateSummaryAndInfo().
•	updateSummaryAndInfo()
Menghitung total harga berdasarkan destinasi terpilih, jumlah tiket, dan opsi tambahan (pemandu/makan). Kemudian menampilkan ringkasan di panel kanan dan info destinasi di panel kiri.
•	openDetailModal(dest)
Membuka modal destinasi. Mengisi modal dengan nama, lokasi, deskripsi, dan gambar (emoji) destinasi. Juga mengatur tanggal minimal hari ini dan mereset checkbox.
•	showToast(message, isError)
Menampilkan notifikasi toast. Jika isError true, warna latar merah; jika sukses, biru. Toast hilang setelah 3 detik.
•	setMinDate()
Mengatur input tanggal visitDate agar tidak bisa memilih tanggal kemarin. Nilai default diisi hari ini.
•	Efek mengetik (typeEffect)
Mengubah teks di hero secara bergantian seperti sedang diketik ulang. Ada jeda dan kecepatan yang berbeda saat mengetik dan menghapus.
•	initEventListeners()
Memasang semua "pendengar" ke elemen-elemen interaktif:
o	Dropdown destinasi → saat berubah, panggil setSelectedDest.
o	Input jumlah tiket → validasi minimal 1 dan update ringkasan.
o	Checkbox → update ringkasan.
o	Tombol "Pesan Sekarang" di panel utama → validasi dan tampilkan toast.
o	Tombol tutup modal dan klik di luar modal → nutup modal.
o	Tombol "Pesan Sekarang" di modal → hitung total dan tampilkan toast.
o	Tombol "Masuk" → buka modal login.
o	Tombol login di modal → validasi sederhana (email dan password tidak boleh kosong).
o	Menu navigasi → scroll halus ke bagian terkait.
o	Tombol cari → ambil teks input dan tampilkan notifikasi.
Eksekusi Awal
Setelah semua fungsi didefinisikan, kita panggil:
•	renderCards() – menampilkan kartu destinasi.
•	renderPaket() – menampilkan kartu paket.
•	populateSelect() – mengisi dropdown.
•	setMinDate() – mengatur tanggal minimal.
•	initEventListeners() – memasang semua event listener.
•	setTimeout(typeEffect, 1000) – memulai efek mengetik setelah 1 detik.
Dengan begitu, saat halaman pertama dibuka, semua sudah siap dan pengguna bisa langsung berinteraksi.
