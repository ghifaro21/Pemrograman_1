# Modul Praktikum: Membangun Antarmuka Web Interaktif dengan Bootstrapp

Pada praktikum ini, kita akan menggunakan **Bootstrap** (tersedia lengkap di [https://getbootstrap.com/](https://getbootstrap.com/)). Bootstrap adalah kerangka kerja (framework) CSS yang memungkinkan kita membuat desain web yang rapi, responsif, dan interaktif dengan sangat cepat.

Kabar baiknya: Untuk membuat animasi dan fitur interaktif (seperti jendela pop-up atau menu yang bisa dibuka-tutup), **kita tidak perlu menulis kode JavaScript sama sekali**. Kita hanya perlu menyusun tag HTML dan menambahkan atribut khusus yang sudah disediakan oleh Bootstrap.

Berikut adalah langkah-langkah mudah penggunaannya.

---

## Langkah 1: Memasang Bootstrap ke dalam HTML (Via CDN)

Langkah pertama adalah menghubungkan file HTML kita dengan perpustakaan Bootstrap. Kita menggunakan metode **CDN (Content Delivery Network)**, yaitu mengambil file Bootstrap langsung dari internet.

Ada dua baris kode penting yang harus dimasukkan ke kerangka HTML Anda:
1. **Link CSS:** Untuk tata letak dan warna (diletakkan di dalam `<head>`).
2. **Script JS Bundle Bootstrap:** Meskipun kita tidak akan *menulis* JS, kita tetap membutuhkan mesin penyokong dari Bootstrap agar fitur interaktifnya bisa berjalan. (Diletakkan di dalam `<body>` paling bawah).

**Template Dasar Wajib:**
```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dashboard Data Interaktif</title>
    
    <!-- 1. Pemasangan Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
    
    <!-- SEMUA KONTEN WEB ANDA DITULIS DI SINI -->
    <h1 class="text-center mt-4">Halo, Bootstrap!</h1>

    <!-- 2. Pemasangan Bootstrap JS Bundle (Wajib untuk animasi interaktif) -->
    <!-- Diletakkan tepat di atas tag penutup body -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
```

---

## Langkah 2: Memahami Cara Kerja Atribut Interaktif (`data-bs-*`)

Di Bootstrap, interaksi dan animasi dipicu murni menggunakan HTML. Kuncinya ada pada atribut awalan `data-bs-`.
* `data-bs-toggle="..."` : Berfungsi sebagai "saklar". Memberi tahu Bootstrap aksi apa yang harus dilakukan (contoh: buka *modal*, buka *collapse*).
* `data-bs-target="..."` : Menunjuk "sasaran". Elemen mana yang harus dimunculkan atau disembunyikan (menggunakan ID HTML).

---

## Langkah 3: Membuat Komponen Interaktif (Praktek)

Mari kita buat 3 komponen interaktif yang sangat sering digunakan dalam *Dashboard Sains Data*. Salin kode-kode di bawah ini ke dalam bagian `<body>` pada template dasar di atas.

### A. Collapse (Menyembunyikan & Memunculkan Detail Data)
Sangat berguna jika Anda memiliki informasi panjang (seperti metadata *dataset*) yang tidak ingin ditampilkan semua secara langsung agar halaman tidak penuh. Animasi yang dihasilkan adalah transisi *slide-down* (meluncur ke bawah).

```html
<div class="container mt-5">
    <h3>1. Fitur Collapse</h3>
    
    <!-- Tombol Saklar -->
    <!-- data-bs-toggle="collapse" mengaktifkan fitur lipat -->
    <!-- data-bs-target="#infoDataset" menunjuk ke kotak yang akan dibuka -->
    <button class="btn btn-primary" type="button" data-bs-toggle="collapse" data-bs-target="#infoDataset">
        Tampilkan Deskripsi Dataset
    </button>

    <!-- Kotak Sasaran -->
    <!-- Class "collapse" membuat kotak ini tersembunyi pada awalnya -->
    <div class="collapse mt-3" id="infoDataset">
        <div class="card card-body bg-light">
            <strong>Sumber Data:</strong> Kaggle (Kecelakaan Lalu Lintas 2025).<br>
            <strong>Jumlah Baris:</strong> 150.450 baris.<br>
            Dataset ini berisi informasi geospasial mengenai titik rawan kecelakaan.
        </div>
    </div>
</div>
```

### B. Accordion (Menu Akordeon untuk FAQ / Tahapan)
Mirip dengan Collapse, tetapi dalam bentuk daftar vertikal. Ketika satu bagian dibuka, bagian lainnya bisa otomatis tertutup. Sangat cocok untuk menampilkan "Langkah-langkah Analisis Data".

```html
<div class="container mt-5">
    <h3>2. Fitur Accordion</h3>
    
    <div class="accordion" id="alurAnalisis">
        
        <!-- Item Accordion 1 -->
        <div class="accordion-item">
            <h2 class="accordion-header">
                <!-- data-bs-target mengarah ke #tahap1 -->
                <button class="accordion-button" type="button" data-bs-toggle="collapse" data-bs-target="#tahap1">
                    Tahap 1: Data Cleaning (Pembersihan Data)
                </button>
            </h2>
            <!-- Class "show" membuat bagian ini langsung terbuka di awal -->
            <div id="tahap1" class="accordion-collapse collapse show" data-bs-parent="#alurAnalisis">
                <div class="accordion-body">
                    Menghapus nilai kosong (NULL) dan duplikat dari dataset mentah.
                </div>
            </div>
        </div>

        <!-- Item Accordion 2 -->
        <div class="accordion-item">
            <h2 class="accordion-header">
                <!-- Perhatikan tombol ini mengarah ke #tahap2 dan memiliki class "collapsed" -->
                <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#tahap2">
                    Tahap 2: Data Visualisasi
                </button>
            </h2>
            <div id="tahap2" class="accordion-collapse collapse" data-bs-parent="#alurAnalisis">
                <div class="accordion-body">
                    Membuat diagram batang dan scatter plot untuk melihat korelasi antar variabel.
                </div>
            </div>
        </div>

    </div>
</div>
```

### C. Modal (Jendela Pop-Up Mengambang)
Modal adalah jendela yang muncul di atas layar (pop-up) dengan efek latar belakang yang menggelap. Cocok untuk menampilkan detail hasil evaluasi *Machine Learning* tanpa harus pindah ke halaman HTML lain.

```html
<div class="container mt-5">
    <h3>3. Fitur Modal (Pop-up)</h3>
    
    <!-- Tombol Saklar -->
    <button type="button" class="btn btn-success" data-bs-toggle="modal" data-bs-target="#modalHasil">
        Lihat Hasil Prediksi Model
    </button>

    <!-- Struktur Kotak Sasaran (Modal) -->
    <!-- Class "fade" memberikan animasi memudar (fade-in) yang halus -->
    <div class="modal fade" id="modalHasil" tabindex="-1">
        <div class="modal-dialog">
            <div class="modal-content">
                
                <!-- Bagian Atas Modal -->
                <div class="modal-header">
                    <h5 class="modal-title">Akurasi Model Klasifikasi</h5>
                    <!-- Tombol X untuk menutup -->
                    <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
                </div>
                
                <!-- Bagian Isi Modal -->
                <div class="modal-body">
                    <p>Model K-Nearest Neighbors (KNN) berhasil dilatih.</p>
                    <h2 class="text-center text-success">92.5%</h2>
                </div>
                
                <!-- Bagian Bawah Modal -->
                <div class="modal-footer">
                    <!-- data-bs-dismiss="modal" adalah saklar khusus untuk menutup modal -->
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Tutup</button>
                </div>
                
            </div>
        </div>
    </div>
</div>
```

---

## Kesimpulan Praktikum

1. **Eksplorasi Mandiri:** Anda dapat melihat ratusan komponen lainnya dengan mengunjungi [https://getbootstrap.com/](https://getbootstrap.com/) lalu masuk ke menu **Docs -> Components**.
2. **Kekuatan Atribut HTML:** Dengan Bootstrap, HTML bukan lagi sekadar teks statis. Penggunaan `data-bs-toggle` dan `data-bs-target` mengubah HTML menjadi antarmuka interaktif yang profesional tanpa perlu memusingkan penulisan logika JavaScript.
3. **Pentingnya Class `.fade` dan `.collapse`:** Class bawaan inilah yang mengatur efek animasi transisi secara otomatis, membuat tampilan web menjadi tidak kaku.
