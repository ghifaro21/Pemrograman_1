# Modul Pembelajaran: Dasar Web (HTML, CSS, dan Bootstrap)

Modul ini dirancang untuk memperkenalkan Anda pada teknologi fundamental pembuat antarmuka web (*front-end*). Kita akan memulai dari struktur dasar HTML, mengelola tata letak dan ukuran dengan CSS, hingga mempercepat proses desain menggunakan *framework* Bootstrap.

---

## Bagian 1: Fundamental HTML (Struktur dan Konten)

**HTML (HyperText Markup Language)** adalah kerangka dasar dari setiap halaman web. HTML menggunakan sistem "tag" (`<tag>`) untuk memberi tahu *browser* bagaimana mengklasifikasikan konten (apakah itu teks, gambar, atau tabel).

### 1. Struktur Dasar Dokumen HTML

Setiap dokumen HTML (disimpan dengan ekstensi `.html`) wajib memiliki struktur standar ini:

```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <title>Halaman Data Analitik</title>
</head>
<body>
    <!-- Semua konten yang bisa dilihat pengguna diletakkan di dalam tag body -->
    <h1>Dashboard Penjualan</h1>
    <p>Selamat datang di panel analitik data.</p>
</body>
</html>
```

### 2. Elemen-elemen HTML Esensial

*   **Heading (Judul):** `<h1>` (paling besar) hingga `<h6>` (paling kecil). Digunakan untuk hierarki judul.
*   **Teks dan Paragraf:** `<p>` untuk paragraf, `<b>` atau `<strong>` untuk teks tebal, `<i>` atau `<em>` untuk teks miring.
*   **Media (Gambar):** `<img src="grafik.png" width="400" alt="Grafik Tren">` 
    *(Catatan: Tag `<img>` tidak butuh tag penutup).*
*   **Tabel Data:** Sangat penting di ranah sains data untuk menampilkan struktur baris dan kolom.
    ```html
    <table border="1">
        <thead>
            <tr> <!-- Baris Header -->
                <th>ID</th>
                <th>Nama Produk</th>
                <th>Stok</th>
            </tr>
        </thead>
        <tbody>
            <tr> <!-- Baris Data -->
                <td>A01</td>
                <td>Laptop Server</td>
                <td>15</td>
            </tr>
        </tbody>
    </table>
    ```
*   **Input Data (Formulir):** Digunakan untuk membuat filter (seperti rentang tanggal) di dashboard.
    ```html
    <form>
        <label>Pilih Kategori:</label>
        <select>
            <option>Elektronik</option>
            <option>Pakaian</option>
        </select>
        <input type="date">
        <button type="submit">Filter Data</button>
    </form>
    ```

---

## Bagian 2: CSS (Cascading Style Sheets) - Estetika & Tata Letak

CSS bertugas "mendandani" kerangka HTML tadi. Dengan CSS, kita bisa mengatur warna, ukuran, jarak, dan posisi.

### 1. Konsep Wajib: CSS Box Model (Margin & Padding)
Sebelum menulis CSS, Anda wajib memahami bahwa **setiap elemen HTML dianggap sebagai sebuah kotak (box)**. 
*   **Width & Height:** Mengatur lebar dan tinggi elemen (biasanya menggunakan satuan `px` atau `%`).
*   **Padding:** Jarak **di dalam** kotak (antara konten teks dengan garis tepi/border). Membuat elemen terlihat lebih "berisi" atau luas.
*   **Border:** Garis tepi dari kotak tersebut.
*   **Margin:** Jarak **di luar** kotak (mendorong kotak lain agar menjauh). Digunakan untuk memberi jarak antar elemen (misalnya jarak antara judul dengan tabel).

### 2. Tiga Cara Menulis CSS

#### Cara 1: Inline CSS (Langsung di Tag HTML)
Ditulis menggunakan atribut `style` langsung di tag. Cocok untuk modifikasi cepat, tapi membuat kode HTML berantakan.
```html
<!-- Mengatur huruf biru, margin bawah 20px, dan ukuran huruf 24px -->
<h2 style="color: blue; margin-bottom: 20px; font-size: 24px;">Ringkasan Data</h2>

<!-- Kotak dengan lebar 50%, background abu-abu, dan padding dalam 15px -->
<div style="width: 50%; background-color: #eeeeee; padding: 15px;">
    Ini adalah kotak konten (div).
</div>
```

#### Cara 2: Internal CSS (Di bagian `<head>`)
Aturan CSS dikumpulkan di dalam tag `<style>`. Anda harus menggunakan **Selector** (penanda) untuk memilih tag mana yang mau dihias.

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        /* 1. Selector Tag: Mempengaruhi semua tag body */
        body {
            font-family: Arial, sans-serif;
            background-color: #f8f9fa;
        }

        /* 2. Selector Class (Ditandai titik): Bisa dipakai berulang-ulang */
        .kartu-metrik {
            background-color: white;
            width: 300px;           /* Lebar tetap 300 pixel */
            padding: 20px;          /* Jarak dalam 20px agar teks tidak menempel ke tepi */
            margin: 15px;           /* Jarak luar 15px agar antar kartu tidak berdempetan */
            border: 2px solid #ccc; /* Garis tepi abu-abu */
            border-radius: 8px;     /* Membuat sudut kotak menjadi melengkung/bulat */
        }

        /* 3. Selector ID (Ditandai hashtag): Hanya untuk 1 elemen unik */
        #judul-utama {
            color: darkred;
            text-align: center;
        }
    </style>
</head>
<body>
    <h1 id="judul-utama">Laporan Penjualan</h1>
    
    <!-- Memanggil class "kartu-metrik" -->
    <div class="kartu-metrik">
        <h3>Total Pendapatan</h3>
        <p>Rp 50.000.000</p>
    </div>
</body>
</html>
```

#### Cara 3: External CSS (Praktik Terbaik)
Memisahkan HTML dan CSS. CSS disimpan di file `style.css`, lalu dipanggil ke dalam HTML. Sangat disarankan untuk proyek nyata.
**Di file HTML (`index.html`):**
```html
<head>
    <link rel="stylesheet" href="style.css">
</head>
```
**Di file CSS (`style.css`):**
```css
/* Menambahkan shadow (bayangan) ke tabel */
.tabel-data {
    width: 100%;
    margin-top: 30px; 
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
}
```

---

## Bagian 3: Bootstrap (CSS Framework)

Mendesain tata letak yang sempurna (seperti *margin, padding*, letak kolom) dengan CSS murni membutuhkan banyak kode. **Bootstrap** adalah perpustakaan CSS yang sudah menyiapkan "class" siap pakai.

### 1. Cara Memasang (via CDN)
Letakkan baris ini di dalam `<head>` dokumen HTML Anda:
```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
```

### 2. Utility Class: Margin & Padding Otomatis
Di Bootstrap, Anda tidak perlu menulis `margin: 20px;` di CSS. Cukup gunakan class di HTML:
*   **`m`** untuk Margin, **`p`** untuk Padding.
*   Sisi: **`t`** (top/atas), **`b`** (bottom/bawah), **`s`** (start/kiri), **`e`** (end/kanan).
*   Ukuran: **`1`** (kecil) sampai **`5`** (besar).

```html
<!-- Kotak dengan padding besar di semua sisi (p-4) dan margin bawah (mb-3) -->
<div class="p-4 mb-3 bg-light border">
    Teks ini punya jarak yang luas dari tepinya!
</div>
```

### 3. Sistem Grid (Kolom Tata Letak)
Fitur terkuat Bootstrap adalah membagi halaman ke dalam **12 kolom**. Ini memudahkan kita menyejajarkan elemen (seperti tabel berdampingan dengan grafik).

```html
<!-- Container membungkus konten agar ada jarak dari tepi monitor -->
<div class="container mt-5"> 
    <div class="row">
        <!-- Mengambil 4 dari 12 kolom (1/3 layar) -->
        <div class="col-md-4">
            <div class="card p-3 shadow-sm">
                <h4>Filter Data</h4>
                <input type="text" class="form-control" placeholder="Cari...">
                <button class="btn btn-primary mt-3 w-100">Terapkan</button>
            </div>
        </div>
        
        <!-- Mengambil 8 dari 12 kolom (2/3 layar) -->
        <div class="col-md-8">
            <div class="card p-3 shadow-sm">
                <h4>Grafik Tren</h4>
                <p>Area grafik visualisasi diletakkan di sini.</p>
            </div>
        </div>
    </div>
</div>
```

### 4. Elemen Siap Pakai Lainnya
*   **Tabel Rapi:** Tambahkan `<table class="table table-bordered table-striped">` dan tabel Anda otomatis terlihat profesional, rapi, dengan warna selang-seling.
*   **Tombol:** `<button class="btn btn-success">Download CSV</button>` (membuat tombol berdesain modern warna hijau).
*   **Gambar Responsif:** `<img src="gambar.jpg" class="img-fluid">` (membuat gambar otomatis menyesuaikan lebar layar hp/komputer).

***

**Kesimpulan Pembelajaran:**
1. Gunakan **HTML** untuk mendata struktur konten dan form masukan.
2. Pahami konsep **Margin, Padding, dan Width/Height** di **CSS** untuk mengerti bagaimana elemen mengambil ruang di layar.
3. Kuasai **Sistem Grid & Spacing Bootstrap** (`col`, `p-3`, `mt-4`) untuk merakit *dashboard* data dengan cepat, bersih, dan kompatibel untuk HP maupun Desktop.