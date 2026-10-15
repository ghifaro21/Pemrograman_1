# 📘 Modul Praktikum: Membuat Personal Blog dengan HTML, CSS & Bootstrap 5.3

**Topik:** HTML, CSS, Bootstrap 5.3
**Tujuan:** Mahasiswa mampu membangun sebuah website blog personal multi-halaman

---

## 📋 Daftar Isi

1. [Persiapan: Struktur Folder &amp; File](#1-persiapan-struktur-folder--file)
2. [Shortcut &amp; Prettier di VS Code](#2-shortcut--prettier-di-vs-code)
3. [Instalasi Bootstrap 5.3 via CDN](#3-instalasi-bootstrap-53-via-cdn)
4. [Navbar &amp; Footer (Berlaku di Semua Halaman)](#4-navbar--footer-berlaku-di-semua-halaman)
5. [Halaman Home - Hero Section](#5-halaman-home--hero-section)
6. [Halaman Home - Blog Posts (Cards)](#6-halaman-home--blog-posts-cards)
7. [Halaman Gallery - Carousel](#7-halaman-gallery--carousel)
8. [Halaman Gallery - Photo Cards](#8-halaman-gallery--photo-cards)
9. [Halaman Contact - Page Header](#9-halaman-contact--page-header)
10. [Halaman Contact - Contact Form](#10-halaman-contact--contact-form)
11. [Halaman About - Copy dari CV/Biografi](#11-halaman-about--copy-dari-cvbiografi)
12. [CSS di Masing-Masing Halaman](#12-css-di-masing-masing-halaman)

---

## 1. Persiapan: Struktur Folder & File

### 1.1 Membuat Folder Proyek

Buat folder utama proyek dengan nama `Blog1`. Di dalamnya buat subfolder dan file berikut:

```
Blog1/
├── index.html          <- Halaman utama (Home)
├── public/             <- Folder untuk gambar/aset
│   ├── maskman.jpg
│   ├── aduh (1).jpg
│   ├── aduh (2).jpg
│   ├── aduh (3).jpg
│   ├── aduh (4).jpg
│   └── aduh (5).jpg
├── gallery/
│   └── gallery.html    <- Halaman Gallery
├── about/
│   └── about.html      <- Halaman About
└── contact/
    └── contact.html    <- Halaman Contact
```

### 1.2 Cara Membuat Struktur di VS Code

1. Buka VS Code
2. Klik **File → Open Folder** → pilih folder `Blog1`
3. Di panel **Explorer** (kiri), klik ikon **New Folder** untuk membuat subfolder:
   - Buat folder: `public`, `gallery`, `about`, `contact`
4. Klik ikon **New File** untuk membuat file:
   - Di root: `index.html`
   - Di dalam `gallery/`: `gallery.html`
   - Di dalam `about/`: `about.html`
   - Di dalam `contact/`: `contact.html`
5. Masukkan foto/gambar ke dalam folder `public/`

> **Penting tentang Path (Alamat File):**
> Karena file HTML ada di subfolder, gunakan `../` untuk naik satu level ke folder induk.
> Contoh: dari `gallery/gallery.html` ke gambar → `../public/namagambar.jpg`
> Contoh: dari `gallery/gallery.html` ke home → `../index.html`

---

## 2. Shortcut & Prettier di VS Code

### 2.1 Shortcut Penting VS Code

| Shortcut             | Fungsi                              |
| -------------------- | ----------------------------------- |
| `Ctrl + S`         | Simpan file                         |
| `Ctrl + Z`         | Undo                                |
| `Ctrl + Shift + Z` | Redo                                |
| `Ctrl + /`         | Komentar / uncomment baris          |
| `Alt + Shift + F`  | **Format dokumen (Prettier)** |
| `Ctrl + D`         | Pilih kata berikutnya yang sama     |
| `Ctrl + Shift + P` | Buka Command Palette                |
| `! + Enter`        | Emmet: generate boilerplate HTML    |
| `Tab`              | Auto-complete Emmet snippet         |

### 2.2 Instalasi Prettier

1. Buka VS Code
2. Klik ikon **Extensions** di sidebar kiri (atau `Ctrl + Shift + X`)
3. Cari: **Prettier - Code formatter**
4. Klik **Install**
5. Setelah terpasang, buka **File → Preferences → Settings**
6. Cari `Default Formatter` → pilih **Prettier**
7. Cari `Format On Save` → centang agar otomatis format saat `Ctrl + S`

### 2.3 Cara Pakai Prettier

- **Manual:** Tekan `Alt + Shift + F` di dalam file HTML yang sedang dibuka
- **Otomatis:** Jika Format On Save aktif, cukup tekan `Ctrl + S`

> **Apa yang dilakukan Prettier?**
> Prettier merapikan indentasi, spasi, dan tanda kutip kode kita secara otomatis agar lebih rapi dan mudah dibaca.

---

## 3. Instalasi Bootstrap 5.3 via CDN

### 3.1 Apa itu CDN?

CDN (Content Delivery Network) adalah cara menggunakan library dari internet tanpa perlu download file-nya. Kita cukup copy-paste link yang disediakan Bootstrap ke dalam HTML kita.

### 3.2 Mengambil CDN dari Website Bootstrap

1. Buka browser → pergi ke **https://getbootstrap.com**
2. Klik tombol **Get started**
3. Scroll ke bagian **CDN links**
4. Copy bagian **CSS** dan **JS Bundle**

### 3.3 Boilerplate HTML Dasar

Setiap file HTML diawali dengan struktur dasar berikut. Buat ini di setiap file:

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>MyBlog - Nama Halaman</title>

    <!-- Bootstrap CSS (CDN) - diletakkan di dalam head -->
    <link
      href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.8/dist/css/bootstrap.min.css"
      rel="stylesheet"
      integrity="sha384-sRIl4kxILFvY47J16cr9ZwB07vP4J8+LH7qKQnuqkuIAvNWLzeN8tE5YBujZqJLB"
      crossorigin="anonymous"
    />
  </head>
  <body>

    <!-- Semua konten halaman ditulis di sini -->

    <!-- Bootstrap JS Bundle (CDN) - diletakkan sebelum penutup body -->
    <script
      src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.8/dist/js/bootstrap.bundle.min.js"
      integrity="sha384-FKyoEForCGlyvwx9Hj09JcYn3nv7wiPVlz7YYwJrWVcXK/BmnVDxM+D2scQbITxI"
      crossorigin="anonymous"
    ></script>
  </body>
</html>
```

**Penjelasan tiap bagian:**

| Tag / Atribut                  | Fungsi                                                                                                           |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------- |
| `<!doctype html>`            | Memberitahu browser ini adalah dokumen HTML5                                                                     |
| `<html lang="en">`           | Bahasa halaman (bisa diganti `"id"` untuk Indonesia)                                                           |
| `<meta charset="UTF-8">`     | Mengizinkan karakter khusus (huruf, simbol, emoji) ditampilkan                                                   |
| `<meta name="viewport" ...>` | Mengatur tampilan di layar HP (responsif)                                                                        |
| `<title>`                    | Teks yang muncul di tab browser                                                                                  |
| `<link ... CSS>`             | Memanggil file CSS Bootstrap dari internet                                                                       |
| `<script ... JS>`            | Memanggil file JavaScript Bootstrap — wajib untuk komponen interaktif seperti navbar toggle, carousel, dropdown |
| `integrity="..."`            | Kode keamanan (hash) untuk memastikan file tidak dimodifikasi pihak lain                                         |
| `crossorigin="anonymous"`    | Izin akses lintas domain tanpa mengirim kredensial                                                               |

> **Mengapa JS di bawah, bukan di head?**
> Agar halaman tampil lebih cepat — browser membaca HTML dari atas ke bawah, jadi konten ditampilkan dulu baru script dijalankan.

---

## 4. Navbar & Footer (Berlaku di Semua Halaman)

> **Navbar diambil dari:** Bootstrap Docs → **Components → Navbar**
> **Footer:** menggunakan tag semantik HTML standar `<footer>`

Navbar dan footer dipakai di **semua halaman**. Copy-paste bagian ini ke setiap file, lalu sesuaikan path-nya.

### 4.1 Kode Navbar

```html
<!-- Navbar Start -->
<nav class="navbar navbar-expand-lg">
  <div class="container">
    <a class="navbar-brand fw-bold" href="index.html">NamaBlog</a>
    <button
      class="navbar-toggler"
      type="button"
      data-bs-toggle="collapse"
      data-bs-target="#navbarSupportedContent"
      aria-controls="navbarSupportedContent"
      aria-expanded="false"
      aria-label="Toggle navigation"
    >
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <a class="nav-link active" aria-current="page" href="...">Home</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="...">Gallery</a>
        </li>
        <li class="nav-item dropdown">
          <a
            class="nav-link dropdown-toggle"
            href="#"
            role="button"
            data-bs-toggle="dropdown"
            aria-expanded="false"
          >
            More
          </a>
          <ul class="dropdown-menu">
            <li><a class="dropdown-item" href="...">About</a></li>
            <li><a class="dropdown-item" href="...">Contact</a></li>
          </ul>
        </li>
      </ul>
      <form class="d-flex" role="search">
        <input
          class="form-control me-2"
          type="search"
          placeholder="Search"
          aria-label="Search"
        />
        <button class="btn btn-custom" type="submit">Search</button>
      </form>
    </div>
  </div>
</nav>
<!-- Navbar End -->
```

### 4.2 Penjelasan Class Navbar

| Class / Atribut                              | Diambil dari            | Fungsi                                                                                                                 |
| -------------------------------------------- | ----------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `navbar`                                   | Components → Navbar    | Class utama Bootstrap untuk membuat navbar                                                                             |
| `navbar-expand-lg`                         | Components → Navbar    | Navbar tampil horizontal di layar `lg` (>=992px). Di bawah ukuran itu, navbar akan collapse (menjadi hamburger menu) |
| `container`                                | Layout → Containers    | Membungkus konten dengan lebar maksimal dan margin kanan-kiri otomatis                                                 |
| `navbar-brand`                             | Components → Navbar    | Style untuk nama/logo website di navbar                                                                                |
| `fw-bold`                                  | Utilities → Text       | Font weight bold                                                                                                       |
| `navbar-toggler`                           | Components → Navbar    | Tombol hamburger yang muncul di layar kecil (mobile)                                                                   |
| `data-bs-toggle="collapse"`                | —                      | Atribut Bootstrap JS: menginstruksikan Bootstrap untuk toggle (buka/tutup) elemen                                      |
| `data-bs-target="#navbarSupportedContent"` | —                      | Menunjuk ID elemen mana yang akan di-toggle                                                                            |
| `collapse navbar-collapse`                 | Components → Navbar    | Elemen yang disembunyikan/ditampilkan saat hamburger diklik                                                            |
| `id="navbarSupportedContent"`              | —                      | ID unik yang dipanggil oleh `data-bs-target`                                                                         |
| `navbar-nav`                               | Components → Navbar    | Container untuk daftar item navigasi                                                                                   |
| `me-auto`                                  | Utilities → Spacing    | `margin-end: auto` — mendorong elemen ke kiri, sehingga search form ke kanan                                        |
| `mb-2 mb-lg-0`                             | Utilities → Spacing    | Margin bottom 2 (di layar kecil), 0 di layar `lg` ke atas                                                            |
| `nav-item`                                 | Components → Navbar    | Satu item dalam daftar navigasi                                                                                        |
| `nav-link`                                 | Components → Navbar    | Style link di dalam navbar                                                                                             |
| `active`                                   | Components → Navbar    | Menandai halaman yang sedang aktif/dibuka                                                                              |
| `aria-current="page"`                      | —                      | Aksesibilitas: memberitahu screen reader bahwa ini halaman aktif                                                       |
| `dropdown`                                 | Components → Dropdowns | Menandai item sebagai dropdown                                                                                         |
| `dropdown-toggle`                          | Components → Dropdowns | Menambahkan panah kecil dan fungsionalitas buka/tutup dropdown                                                         |
| `data-bs-toggle="dropdown"`                | —                      | Bootstrap JS: mengaktifkan fungsionalitas dropdown                                                                     |
| `dropdown-menu`                            | Components → Dropdowns | Kotak menu yang muncul saat dropdown diklik                                                                            |
| `dropdown-item`                            | Components → Dropdowns | Style satu item di dalam dropdown menu                                                                                 |
| `d-flex`                                   | Utilities → Display    | `display: flex` — menyusun form secara horizontal                                                                   |
| `form-control`                             | Forms → Form controls  | Style Bootstrap untuk elemen input                                                                                     |
| `me-2`                                     | Utilities → Spacing    | `margin-end: 0.5rem` (jarak kanan antara input dan tombol)                                                           |

### 4.3 Penyesuaian Path Navbar per Halaman

Karena tiap halaman ada di folder berbeda, link harus disesuaikan:

| Dari halaman             | Home              | Gallery                     | About                   | Contact                     |
| ------------------------ | ----------------- | --------------------------- | ----------------------- | --------------------------- |
| `index.html`           | `index.html`    | `gallery/gallery.html`    | `about/about.html`    | `contact/contact.html`    |
| `gallery/gallery.html` | `../index.html` | `gallery.html`            | `../about/about.html` | `../contact/contact.html` |
| `about/about.html`     | `../index.html` | `../gallery/gallery.html` | `about.html`          | `../contact/contact.html` |
| `contact/contact.html` | `../index.html` | `../gallery/gallery.html` | `../about/about.html` | `contact.html`            |

> **`../` artinya:** naik satu level ke folder induk.

### 4.4 Kode Footer

```html
<!-- Footer Start -->
<footer>
  <div class="container">
    <p class="mb-0">© 2024 MyBlog · Nama. All rights reserved.</p>
  </div>
</footer>
<!-- Footer End -->
```

**Penjelasan:**

| Tag / Class           | Fungsi                                                             |
| --------------------- | ------------------------------------------------------------------ |
| `<footer>`          | Tag semantik HTML5 untuk bagian bawah halaman                      |
| `class="container"` | Memberikan lebar maksimal dan margin otomatis seperti konten utama |
| `mb-0`              | Menghilangkan margin bawah default dari tag `<p>`                |

> **Letak Footer:** Footer ditulis **di dalam `<body>`**, tepat **sebelum tag `<script>`** Bootstrap JS.
> Jangan taruh footer di luar `<body>` atau di dalam tag yang tidak valid seperti `<tail>`.

---

## 5. Halaman Home - Hero Section

> **Diambil dari:** Bootstrap Docs → **Layout → Grid system**

Hero section adalah bagian pertama yang dilihat pengunjung saat membuka website.

### 5.1 Kode Hero Section

Tulis kode ini di `index.html`, tepat setelah tag penutup navbar `</nav>`:

```html
<!-- Hero Section Start -->
<section class="hero-section">
  <div class="container">
    <div class="row align-items-center">

      <!-- Kolom teks (kiri) - 7 dari 12 kolom -->
      <div class="col-md-7">
        <h1>Welcome to My Blog! 👋</h1>
        <p>
          Halo! Saya <strong>Nama</strong>, mahasiswa Data Science di ULBI.
          Blog ini berisi catatan, karya, dan pengalaman saya sehari-hari.
        </p>
        <a href="about/about.html" class="btn btn-custom me-2">About Me</a>
        <a href="contact/contact.html" class="btn btn-outline-secondary">Contact</a>
      </div>

      <!-- Kolom gambar (kanan) - 5 dari 12 kolom -->
      <div class="col-md-5 text-center mt-4 mt-md-0">
        <img
          src="..."
          class="hero-img"
          alt="Profile picture"
        />
      </div>

    </div>
  </div>
</section>
<!-- Hero Section End -->
```

### 5.2 Penjelasan Class Hero Section

| Class / Tag               | Diambil dari          | Fungsi                                                                                                                                    |
| ------------------------- | --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| `<section>`             | HTML Semantik         | Tag semantik untuk menandai bagian/seksi halaman                                                                                          |
| `hero-section`          | CSS Kustom            | Class buatan sendiri — akan diberi style di bagian `<style>`                                                                           |
| `container`             | Layout → Containers  | Membatasi lebar konten dan menambah padding horizontal                                                                                    |
| `row`                   | Layout → Grid        | Membuat satu baris grid Bootstrap (12 kolom tersedia)                                                                                     |
| `align-items-center`    | Layout → Grid        | Menyelaraskan semua kolom secara **vertikal** ke tengah                                                                             |
| `col-md-7`              | Layout → Grid        | Kolom ini mengambil **7 dari 12 kolom** saat di layar medium (>=768px) ke atas. Di layar kecil, otomatis jadi 12 kolom (full width) |
| `col-md-5`              | Layout → Grid        | Kolom ini mengambil **5 dari 12 kolom** di layar medium ke atas. `7 + 5 = 12` (satu baris penuh)                                  |
| `text-center`           | Utilities → Text     | Rata tengah teks dan elemen inline                                                                                                        |
| `mt-4`                  | Utilities → Spacing  | `margin-top: 1.5rem` — jarak atas di layar kecil                                                                                       |
| `mt-md-0`               | Utilities → Spacing  | Di layar medium ke atas, margin top menjadi 0                                                                                             |
| `hero-img`              | CSS Kustom            | Class buatan sendiri untuk styling gambar profil bulat                                                                                    |
| `btn`                   | Components → Buttons | Class utama Bootstrap untuk tombol                                                                                                        |
| `btn-custom`            | CSS Kustom            | Warna tombol sesuai tema kita                                                                                                             |
| `btn-outline-secondary` | Components → Buttons | Tombol dengan border abu-abu tanpa background                                                                                             |
| `me-2`                  | Utilities → Spacing  | `margin-end: 0.5rem` — jarak kanan tombol pertama                                                                                      |

> **Konsep Grid Bootstrap:**
> Bootstrap menggunakan sistem **12 kolom**. Kita bisa membagi satu baris menjadi beberapa kolom selama totalnya = 12.
>
> - `col-md-7` + `col-md-5` = 12 (satu baris)
> - `col-md-4` + `col-md-4` + `col-md-4` = 12 (tiga kolom sama rata)
> - Prefix `md` artinya aturan ini berlaku di layar >=768px. Di bawah itu, kolom otomatis jadi full width.

---

## 6. Halaman Home - Blog Posts (Cards)

> **Diambil dari:** Bootstrap Docs → **Components → Card**

Cards adalah komponen Bootstrap untuk menampilkan konten dalam kotak yang rapi.

### 6.1 Kode Blog Posts

Tulis kode ini di `index.html`, tepat setelah hero section:

```html
<!-- Blog Posts Start -->
<div class="container mt-5">
  <h2 class="mb-4">📝 Recent Posts</h2>
  <div class="row row-cols-1 row-cols-md-3 g-4">

    <!-- Card 1 -->
    <div class="col">
      <div class="card h-100">
        <img
          src="..."
          class="card-img-top"
          style="height: 200px; object-fit: cover;"
          alt="Post 1"
        />
        <div class="card-body">
          <span class="badge badge-custom mb-2">Photography</span>
          <h5 class="card-title">Momen yang Tak Terlupakan</h5>
          <p class="card-text text-muted">
            Sebuah koleksi foto dari perjalanan dan momen berharga.
          </p>
        </div>
        <div class="card-footer text-muted small">
          📅 Oktober 2024
        </div>
      </div>
    </div>

    <!-- Card 2 -->
    <div class="col">
      <div class="card h-100">
        <img
          src="..."
          class="card-img-top"
          style="height: 200px; object-fit: cover;"
          alt="Post 2"
        />
        <div class="card-body">
          <span class="badge badge-custom mb-2">Life</span>
          <h5 class="card-title">Cerita Hari Ini</h5>
          <p class="card-text text-muted">
            Hal-hal kecil yang sering terlewatkan namun menyimpan makna.
          </p>
        </div>
        <div class="card-footer text-muted small">
          📅 Oktober 2024
        </div>
      </div>
    </div>

    <!-- Card 3 -->
    <div class="col">
      <div class="card h-100">
        <img
          src="..."
          class="card-img-top"
          style="height: 200px; object-fit: cover;"
          alt="Post 3"
        />
        <div class="card-body">
          <span class="badge badge-custom mb-2">Art</span>
          <h5 class="card-title">Kreativitas Tanpa Batas</h5>
          <p class="card-text text-muted">
            Eksplorasi seni dan desain sebagai cara mengekspresikan diri.
          </p>
        </div>
        <div class="card-footer text-muted small">
          📅 Oktober 2024
        </div>
      </div>
    </div>

  </div>
</div>
<!-- Blog Posts End -->
```

### 6.2 Penjelasan Class Blog Posts

| Class                          | Diambil dari            | Fungsi                                                            |
| ------------------------------ | ----------------------- | ----------------------------------------------------------------- |
| `container`                  | Layout → Containers    | Membatasi lebar konten di tengah halaman                          |
| `mt-5`                       | Utilities → Spacing    | `margin-top: 3rem` — jarak dari hero section                   |
| `mb-4`                       | Utilities → Spacing    | `margin-bottom: 1.5rem` — jarak bawah judul                    |
| `row`                        | Layout → Grid          | Baris grid                                                        |
| `row-cols-1`                 | Layout → Grid          | Secara default (layar kecil/HP): **1 card per baris**       |
| `row-cols-md-3`              | Layout → Grid          | Di layar medium ke atas: **3 card per baris**               |
| `g-4`                        | Layout → Grid          | `gap: 1.5rem` — jarak antar card (horizontal dan vertikal)     |
| `col`                        | Layout → Grid          | Satu kolom — lebarnya otomatis ditentukan oleh `row-cols-*`    |
| `card`                       | Components → Card      | Class utama Bootstrap untuk membuat card                          |
| `h-100`                      | Utilities → Sizing     | `height: 100%` — semua card dalam satu baris punya tinggi sama |
| `card-img-top`               | Components → Card      | Gambar di bagian atas card, otomatis rounded corners atas         |
| `card-body`                  | Components → Card      | Area konten utama card (padding sudah otomatis)                   |
| `badge`                      | Components → Badges    | Label kecil seperti tag kategori                                  |
| `badge-custom`               | CSS Kustom              | Warna badge sesuai tema kita                                      |
| `mb-2`                       | Utilities → Spacing    | Jarak bawah badge                                                 |
| `card-title`                 | Components → Card      | Style judul di dalam card                                         |
| `card-text`                  | Components → Card      | Style teks paragraf di dalam card                                 |
| `text-muted`                 | Utilities → Colors     | Warna teks abu-abu (lebih soft)                                   |
| `card-footer`                | Components → Card      | Bagian bawah card (diberi border atas otomatis)                   |
| `small`                      | Utilities → Typography | Ukuran font lebih kecil dari teks normal                          |
| `style="object-fit: cover;"` | CSS Inline              | Agar gambar mengisi area tanpa stretch                            |

> **Tips `h-100`:**
> Tanpa `h-100`, card dengan teks lebih sedikit akan lebih pendek. Dengan `h-100`, semua card menyesuaikan tinggi card paling tinggi di baris yang sama.

---

## 7. Halaman Gallery - Carousel

> **Diambil dari:** Bootstrap Docs → **Components → Carousel**

Carousel adalah komponen slideshow gambar yang bisa berpindah otomatis atau dikontrol manual.

### 7.1 Kode Carousel

Tulis kode ini di `gallery/gallery.html`, setelah navbar:

```html
<!-- Carousel Start -->
<div id="carouselGallery" class="carousel slide" data-bs-ride="carousel">

  <!-- Indikator titik-titik di bawah carousel -->
  <div class="carousel-indicators">
    <button
      type="button"
      data-bs-target="#carouselGallery"
      data-bs-slide-to="0"
      class="active"
      aria-current="true"
      aria-label="Slide 1"
    ></button>
    <button
      type="button"
      data-bs-target="#carouselGallery"
      data-bs-slide-to="1"
      aria-label="Slide 2"
    ></button>
    <button
      type="button"
      data-bs-target="#carouselGallery"
      data-bs-slide-to="2"
      aria-label="Slide 3"
    ></button>
  </div>

  <!-- Konten slide -->
  <div class="carousel-inner">
    <div class="carousel-item active">
      <img
        src="..."
        class="d-block w-100 carousel-img"
        alt="Gallery photo 1"
      />
      <div class="carousel-caption d-none d-md-block">
        <h5>Momen Satu</h5>
        <p>Salah satu foto favorit dari koleksi saya.</p>
      </div>
    </div>
    <div class="carousel-item">
      <img
        src="..."
        class="d-block w-100 carousel-img"
        alt="Gallery photo 2"
      />
      <div class="carousel-caption d-none d-md-block">
        <h5>Momen Dua</h5>
        <p>Setiap gambar menyimpan cerita tersendiri.</p>
      </div>
    </div>
    <div class="carousel-item">
      <img
        src="..."
        class="d-block w-100 carousel-img"
        alt="Gallery photo 3"
      />
      <div class="carousel-caption d-none d-md-block">
        <h5>Momen Tiga</h5>
        <p>Kenangan yang selalu ingin diingat.</p>
      </div>
    </div>
  </div>

  <!-- Tombol Prev -->
  <button
    class="carousel-control-prev"
    type="button"
    data-bs-target="#carouselGallery"
    data-bs-slide="prev"
  >
    <span class="carousel-control-prev-icon" aria-hidden="true"></span>
    <span class="visually-hidden">Previous</span>
  </button>

  <!-- Tombol Next -->
  <button
    class="carousel-control-next"
    type="button"
    data-bs-target="#carouselGallery"
    data-bs-slide="next"
  >
    <span class="carousel-control-next-icon" aria-hidden="true"></span>
    <span class="visually-hidden">Next</span>
  </button>

</div>
<!-- Carousel End -->
```

### 7.2 Penjelasan Class Carousel

| Class / Atribut                       | Diambil dari                 | Fungsi                                                            |
| ------------------------------------- | ---------------------------- | ----------------------------------------------------------------- |
| `id="carouselGallery"`              | —                           | ID unik carousel — dipanggil oleh tombol prev/next dan indikator |
| `carousel`                          | Components → Carousel       | Class utama Bootstrap untuk carousel                              |
| `slide`                             | Components → Carousel       | Menambahkan animasi slide (geser) saat berpindah gambar           |
| `data-bs-ride="carousel"`           | Components → Carousel       | Carousel berjalan **otomatis** saat halaman dibuka          |
| `carousel-indicators`               | Components → Carousel       | Container untuk titik-titik indikator slide                       |
| `data-bs-target="#carouselGallery"` | —                           | Menghubungkan tombol indikator ke carousel yang dituju            |
| `data-bs-slide-to="0"`              | —                           | Slide ke-berapa yang dituju saat tombol ini diklik (mulai dari 0) |
| `class="active"` di indikator       | —                           | Slide/indikator yang aktif pertama kali                           |
| `carousel-inner`                    | Components → Carousel       | Container untuk semua slide                                       |
| `carousel-item`                     | Components → Carousel       | Satu slide gambar                                                 |
| `carousel-item active`              | Components → Carousel       | Slide yang **pertama ditampilkan** — wajib ada tepat satu  |
| `d-block`                           | Utilities → Display         | `display: block` — agar gambar tampil sebagai blok             |
| `w-100`                             | Utilities → Sizing          | `width: 100%` — gambar memenuhi lebar carousel                 |
| `carousel-img`                      | CSS Kustom                   | Class kita untuk mengatur tinggi gambar carousel                  |
| `carousel-caption`                  | Components → Carousel       | Teks caption di atas gambar (pojok bawah)                         |
| `d-none`                            | Utilities → Display         | `display: none` secara default (tersembunyi di HP)              |
| `d-md-block`                        | Utilities → Display         | Ditampilkan di layar medium ke atas                               |
| `carousel-control-prev`             | Components → Carousel       | Tombol panah ke kiri (slide sebelumnya)                           |
| `carousel-control-next`             | Components → Carousel       | Tombol panah ke kanan (slide berikutnya)                          |
| `data-bs-slide="prev"`              | —                           | Bootstrap JS: pindah ke slide sebelumnya                          |
| `data-bs-slide="next"`              | —                           | Bootstrap JS: pindah ke slide berikutnya                          |
| `carousel-control-prev-icon`        | Components → Carousel       | Ikon panah kiri (gambar SVG bawaan Bootstrap)                     |
| `visually-hidden`                   | Utilities → Visually hidden | Teks hanya bisa dibaca screen reader, tidak tampil di layar       |

> **Penting:** Hanya boleh ada **satu** `carousel-item active` dalam satu carousel.

---

## 8. Halaman Gallery - Photo Cards

> **Diambil dari:** Bootstrap Docs → **Components → Card** + **Layout → Grid**

Setelah carousel, tambahkan kartu foto di bawahnya:

### 8.1 Kode Photo Cards

```html
<!-- Photo Cards Start -->
<div class="container mt-5 mb-4">
  <h2 class="mb-4">🖼️ Photo Collection</h2>
  <div class="row row-cols-1 row-cols-md-2 g-4">

    <div class="col">
      <div class="card">
        <img
          src="..."
          class="card-img-top"
          alt="Photo 4"
        />
        <div class="card-body">
          <h5 class="card-title">Koleksi #4</h5>
          <p class="card-text text-muted">
            Foto ini diambil di momen yang sangat berkesan.
          </p>
        </div>
      </div>
    </div>

    <div class="col">
      <div class="card">
        <img
          src="....jpg"
          class="card-img-top"
          alt="Photo 5"
        />
        <div class="card-body">
          <h5 class="card-title">Koleksi #5</h5>
          <p class="card-text text-muted">
            Setiap sudut punya cerita yang layak untuk diabadikan.
          </p>
        </div>
      </div>
    </div>

  </div>
</div>
<!-- Photo Cards End -->
```

### 8.2 Perbedaan dari Blog Cards

| Class                                     | Perbedaan vs Blog Posts                                              |
| ----------------------------------------- | -------------------------------------------------------------------- |
| `row-cols-md-2`                         | Hanya 2 card per baris (bukan 3) karena foto butuh ruang lebih lebar |
| `mb-4`                                  | Jarak ke footer di bawahnya                                          |
| Tidak ada `h-100`                       | Tinggi card mengikuti tinggi gambar masing-masing                    |
| `card-img-top` tanpa `style="height"` | Tinggi gambar biarkan natural agar foto terlihat penuh               |

---

## 9. Halaman Contact - Page Header

> **Diambil dari:** Desain kustom dengan Bootstrap Utilities

Page header adalah banner kecil di atas halaman contact.

### 9.1 Kode Page Header

Tulis di `contact/contact.html`, setelah navbar:

```html
<!-- Page Header Start -->
<div class="page-header text-center">
  <h1>📬 Contact Me</h1>
  <p class="text-muted">Ada pertanyaan atau ingin berkolaborasi? Kirim pesan yuk!</p>
</div>
<!-- Page Header End -->
```

### 9.2 Penjelasan Class Page Header

| Class           | Diambil dari        | Fungsi                                                                       |
| --------------- | ------------------- | ---------------------------------------------------------------------------- |
| `page-header` | CSS Kustom          | Class buatan sendiri — diberi background dan padding di `<style>`         |
| `text-center` | Utilities → Text   | Rata tengah semua teks di dalamnya                                           |
| `<h1>`        | HTML Semantik       | Heading utama halaman — hanya boleh ada **satu** `<h1>` per halaman |
| `text-muted`  | Utilities → Colors | Warna teks abu-abu untuk deskripsi yang lebih soft                           |

---

## 10. Halaman Contact - Contact Form

> **Diambil dari:** Bootstrap Docs → **Forms → Form controls** + **Layout → Grid**

### 10.1 Kode Contact Form

Tulis di `contact/contact.html`, setelah page header:

```html
<!-- Contact Form Start -->
<div class="container">
  <div class="row justify-content-center">

    <!-- Kolom Form -->
    <div class="col-md-7">
      <div class="card p-4">
        <div class="card-body">
          <h4 class="card-title mb-4">Kirim Pesan</h4>
          <form>

            <!-- Input Nama -->
            <div class="mb-3">
              <label for="inputName" class="form-label">Nama Lengkap</label>
              <input
                type="text"
                class="form-control"
                id="inputName"
                placeholder="Masukkan nama kamu"
              />
            </div>

            <!-- Input Email -->
            <div class="mb-3">
              <label for="inputEmail" class="form-label">Alamat Email</label>
              <input
                type="email"
                class="form-control"
                id="inputEmail"
                placeholder="contoh@email.com"
              />
            </div>

            <!-- Input Subjek -->
            <div class="mb-3">
              <label for="inputSubject" class="form-label">Subjek</label>
              <input
                type="text"
                class="form-control"
                id="inputSubject"
                placeholder="Perihal pesan kamu"
              />
            </div>

            <!-- Textarea Pesan -->
            <div class="mb-3">
              <label for="inputMessage" class="form-label">Pesan</label>
              <textarea
                class="form-control"
                id="inputMessage"
                rows="5"
                placeholder="Tulis pesanmu di sini..."
              ></textarea>
            </div>

            <!-- Tombol Submit -->
            <div class="d-grid">
              <button type="submit" class="btn btn-custom">Kirim Pesan</button>
            </div>

          </form>
        </div>
      </div>
    </div>

    <!-- Kolom Info Kontak -->
    <div class="col-md-4 mt-4 mt-md-0">
      <div class="card p-4 h-100">
        <div class="card-body">
          <h5 class="card-title mb-3">Info Kontak</h5>
          <p>
            <strong>📧 Email:</strong><br />
            itghifari@example.com
          </p>
          <p>
            <strong>📍 Lokasi:</strong><br />
            Bandung, Jawa Barat
          </p>
          <p>
            <strong>🏫 Kampus:</strong><br />
            ULBI - Universitas Logistik dan Bisnis Internasional
          </p>
          <hr />
          <p class="mb-2"><strong>Sosial Media:</strong></p>
          <div class="d-flex flex-wrap gap-2">
            <a href="#" class="btn btn-custom btn-sm" target="_blank">LinkedIn</a>
            <a href="#" class="btn btn-custom btn-sm" target="_blank">Instagram</a>
            <a href="#" class="btn btn-custom btn-sm" target="_blank">YouTube</a>
          </div>
        </div>
      </div>
    </div>

  </div>
</div>
<!-- Contact Form End -->
```

### 10.2 Penjelasan Class Contact Form

| Class / Atribut            | Diambil dari           | Fungsi                                                                    |
| -------------------------- | ---------------------- | ------------------------------------------------------------------------- |
| `justify-content-center` | Layout → Grid         | Menempatkan kolom-kolom di tengah baris secara horizontal                 |
| `col-md-7`               | Layout → Grid         | Kolom form mengambil 7/12 lebar di layar medium                           |
| `col-md-4`               | Layout → Grid         | Kolom info mengambil 4/12 lebar (ada gap 1 kolom)                         |
| `card p-4`               | Components → Card     | Card dengan padding `1.5rem` di semua sisi                              |
| `card-body`              | Components → Card     | Area isi card                                                             |
| `card-title mb-4`        | Components → Card     | Judul card dengan jarak bawah 1.5rem                                      |
| `<form>`                 | HTML Standar           | Container untuk elemen-elemen form                                        |
| `mb-3`                   | Utilities → Spacing   | Jarak bawah `1rem` antara setiap field form                             |
| `<label>`                | HTML Forms             | Teks keterangan di atas input                                             |
| `for="inputName"`        | HTML Forms             | Harus sama dengan `id` input — agar label bisa diklik                  |
| `form-label`             | Forms → Form labels   | Style Bootstrap untuk label form                                          |
| `form-control`           | Forms → Form controls | Style Bootstrap untuk input — lebar penuh, border, padding, focus effect |
| `id="inputName"`         | HTML Forms             | ID unik input — dihubungkan ke `<label for="...">`                     |
| `type="text"`            | HTML Forms             | Input teks biasa                                                          |
| `type="email"`           | HTML Forms             | Input khusus email — browser validasi format email otomatis              |
| `placeholder="..."`      | HTML Forms             | Teks abu-abu di dalam input saat belum diisi                              |
| `<textarea>`             | HTML Forms             | Input teks multi-baris (untuk pesan panjang)                              |
| `rows="5"`               | HTML Forms             | Tinggi textarea = 5 baris teks                                            |
| `d-grid`                 | Utilities → Display   | `display: grid` — membuat tombol submit melebar penuh                  |
| `btn btn-custom`         | Components → Buttons  | Tombol dengan style tema kita                                             |
| `type="submit"`          | HTML Forms             | Tombol untuk mengirim form                                                |
| `mt-4 mt-md-0`           | Utilities → Spacing   | Kolom info: jarak atas di HP, hilang di layar medium                      |
| `h-100`                  | Utilities → Sizing    | Kolom info setinggi kolom form                                            |
| `d-flex flex-wrap gap-2` | Utilities → Flexbox   | Tombol sosmed horizontal, bisa wrap, jarak antar tombol 0.5rem            |
| `btn-sm`                 | Components → Buttons  | Tombol ukuran kecil                                                       |
| `target="_blank"`        | HTML Link              | Link terbuka di tab baru                                                  |

---

## 11. Halaman About - Copy dari CV/Biografi

Halaman About tidak perlu dibuat dari nol. Cukup isi kontennya dari data CV atau biografi yang sudah dimiliki.

### 11.1 Struktur Halaman About

Halaman ini terdiri dari empat card:

```
1. Profile Card    → Nama, jabatan, foto, bio singkat
2. Skills Card     → Daftar kemampuan
3. Education Card  → Tabel riwayat pendidikan
4. Contact Card    → Tombol ke sosial media
```

### 11.2 Bagian yang Perlu Diisi dari CV

| Bagian                           | Isi dari CV                                |
| -------------------------------- | ------------------------------------------ |
| `<h1>NAMA LENGKAP</h1>`        | Nama lengkap                               |
| `<h3>Profesi/Jurusan</h3>`     | Contoh: "Data Science Student"             |
| `<img src="...">`              | Foto profil (simpan di folder `public/`) |
| `<p class="lead">`             | Bio singkat (2-3 kalimat)                  |
| `<li>` di Skills Card          | Daftar skill atau keahlian                 |
| Baris `<tr>` di Education Card | Data pendidikan dari SD sampai sekarang    |
| Tombol di Contact Card           | Link LinkedIn, Instagram, YouTube, dll.    |

### 11.3 Path Gambar di About

Karena `about.html` ada di dalam folder `about/`, path ke gambar harus:

```html
<img src="../public/namagambar.jpg" alt="Foto profil" class="pfp" />
```

> Jangan gunakan sintaks Flask seperti `{{ url_for('static', filename='foto.jpg') }}` — itu untuk framework Python, bukan HTML statis biasa.

---

## 12. CSS di Masing-Masing Halaman

CSS kustom ditulis di dalam tag `<style>` di bagian `<head>` setiap file HTML.

### 12.1 Letak Penulisan CSS

```html
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>MyBlog - Home</title>

  <!-- 1. Bootstrap CSS (harus di atas style kita) -->
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.8/..." rel="stylesheet" ... />

  <!-- 2. CSS kustom kita (ditulis SETELAH Bootstrap agar bisa override) -->
  <style>
    /* tulis CSS kustom di sini */
  </style>
</head>
```

> **Mengapa CSS kita harus di bawah Bootstrap?**
> Browser membaca CSS dari atas ke bawah. Jika CSS kita di bawah Bootstrap, style kita akan menimpa (override) style Bootstrap jika ada nama class yang sama.

### 12.2 CSS untuk `index.html`

```css
body {
  font-family: "Arial", sans-serif;
  background-color: #f9f8f6; /* Latar krem muda */
  color: #333;               /* Warna teks default gelap */
}

.navbar {
  background-color: #ffffff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); /* Bayangan tipis di bawah navbar */
}

.hero-section {
  background-color: #fff8f3; /* Krem hangat */
  padding: 60px 0;           /* Ruang atas-bawah */
  border-bottom: 1px solid #e8ddd3;
}

.hero-section h1 {
  font-size: 2.5rem;
  font-weight: bold;
  color: #4a3728; /* Coklat tua */
}

.hero-section p {
  font-size: 1.1rem;
  color: #6c584c;
}

/* Foto profil bulat */
.hero-img {
  width: 200px;
  height: 200px;
  object-fit: cover;        /* Foto dicrop agar mengisi lingkaran */
  border-radius: 50%;       /* Membuat gambar berbentuk lingkaran */
  border: 5px solid #c9b59c;
}

.btn-custom {
  background-color: #c9b59c;
  border: none;
  color: white;
}

.btn-custom:hover {
  background-color: #bd9667; /* Lebih gelap saat hover */
  color: white;
}

.card {
  border: none;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease; /* Animasi smooth */
}

.card:hover {
  transform: translateY(-5px);                /* Naik 5px saat hover */
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}

.badge-custom {
  background-color: #c9b59c;
  color: white;
}

footer {
  background-color: #ffffff;
  padding: 20px;
  text-align: center;
  margin-top: 40px;
  border-top: 1px solid #e8ddd3;
}
```

### 12.3 CSS untuk `gallery/gallery.html`

```css
body {
  font-family: "Arial", sans-serif;
  background-color: #f9f8f6;
  color: #333;
}

.navbar {
  background-color: #ffffff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.btn-custom {
  background-color: #c9b59c;
  border: none;
  color: white;
}

.btn-custom:hover {
  background-color: #bd9667;
  color: white;
}

/* Tinggi gambar carousel seragam */
.carousel-img {
  height: 480px;
  object-fit: cover; /* Gambar dicrop agar mengisi tinggi 480px */
}

.card {
  border: none;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}

/* Tinggi gambar di photo cards */
.card-img-top {
  height: 280px;
  object-fit: cover;
}

footer {
  background-color: #ffffff;
  padding: 20px;
  text-align: center;
  margin-top: 40px;
  border-top: 1px solid #e8ddd3;
}
```

### 12.4 CSS untuk `contact/contact.html`

```css
body {
  font-family: "Arial", sans-serif;
  background-color: #f9f8f6;
  color: #333;
}

.navbar {
  background-color: #ffffff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

/* Header banner atas halaman contact */
.page-header {
  background-color: #fff8f3;
  padding: 40px 0;
  border-bottom: 1px solid #e8ddd3;
  margin-bottom: 40px; /* Jarak ke form di bawahnya */
}

.page-header h1 {
  color: #4a3728;
}

.card {
  border: none;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.btn-custom {
  background-color: #c9b59c;
  border: none;
  color: white;
}

.btn-custom:hover {
  background-color: #bd9667;
  color: white;
}

/* Override warna focus/border Bootstrap saat input diklik */
.form-control:focus {
  border-color: #c9b59c;
  box-shadow: 0 0 0 0.25rem rgba(201, 181, 156, 0.25);
}

footer {
  background-color: #ffffff;
  padding: 20px;
  text-align: center;
  margin-top: 40px;
  border-top: 1px solid #e8ddd3;
}
```

### 12.5 CSS untuk `about/about.html`

```css
body {
  font-family: "Arial", sans-serif;
  background-color: #f9f8f6;
  color: #333;
}

.navbar {
  background-color: #ffffff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.card {
  border: none;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  margin-bottom: 20px;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}

/* Foto profil bulat di halaman About */
.pfp {
  width: 150px;
  height: 150px;
  object-fit: cover;
  border-radius: 50%;       /* Membuat gambar lingkaran */
  margin-bottom: 20px;
  border: 5px solid #c9b59c;
}

.btn-custom {
  background-color: #c9b59c;
  border: none;
  color: white;
}

.btn-custom:hover {
  background-color: #bd9667;
  color: white;
}

/* Override warna header tabel */
th {
  background-color: #c9b59c;
  color: white;
}

footer {
  background-color: #ffffff;
  padding: 20px;
  text-align: center;
  margin-top: 40px;
  border-top: 1px solid #e8ddd3;
}
```

### 12.6 Penjelasan Property CSS yang Digunakan

| Property CSS                    | Nilai Contoh                  | Fungsi                                                               |
| ------------------------------- | ----------------------------- | -------------------------------------------------------------------- |
| `font-family`                 | `"Arial", sans-serif`       | Jenis huruf. `sans-serif` sebagai fallback jika Arial tidak ada    |
| `background-color`            | `#f9f8f6`                   | Warna latar belakang elemen                                          |
| `color`                       | `#333`                      | Warna teks                                                           |
| `box-shadow`                  | `0 4px 8px rgba(0,0,0,0.1)` | Bayangan — nilai: `x y blur warna`                                |
| `border-radius`               | `50%`                       | Sudut melengkung. `50%` = lingkaran penuh                          |
| `border`                      | `5px solid #c9b59c`         | Garis tepi: `tebal jenis warna`                                    |
| `object-fit`                  | `cover`                     | Cara gambar mengisi container — `cover` = crop, `contain` = fit |
| `padding`                     | `60px 0`                    | Jarak dalam: `atas-bawah kiri-kanan`                               |
| `margin-top`                  | `40px`                      | Jarak luar atas                                                      |
| `transition`                  | `transform 0.3s ease`       | Animasi perubahan properti: `properti durasi easing`               |
| `transform: translateY(-5px)` | —                            | Geser elemen ke atas 5px                                             |
| `font-size`                   | `2.5rem`                    | Ukuran huruf (1rem = 16px default, jadi 2.5rem = 40px)               |
| `font-weight`                 | `bold`                      | Ketebalan huruf                                                      |
| `text-align`                  | `center`                    | Perataan teks                                                        |

---

## Checklist Akhir Praktikum

Pastikan semua poin di bawah sudah terpenuhi sebelum mengumpulkan:

- [ ] Struktur folder sudah benar (`public/`, `gallery/`, `about/`, `contact/`)
- [ ] Semua file HTML punya boilerplate lengkap (charset, viewport, title, CDN Bootstrap)
- [ ] Navbar ada di semua halaman dengan link yang benar (path relatif)
- [ ] Footer ada di semua halaman, di dalam `<body>` sebelum `<script>`
- [ ] `index.html`: hero section + 3 blog post cards
- [ ] `gallery.html`: carousel (3 slide) + photo cards (2 card)
- [ ] `contact.html`: page header + contact form + info column
- [ ] `about.html`: data diisi dari CV/biografi sendiri
- [ ] Setiap halaman punya `<style>` CSS kustom di `<head>`
- [ ] CSS Bootstrap ditulis **sebelum** CSS kustom kita
- [ ] Tidak ada tag tidak valid seperti `<tail>`
- [ ] Semua gambar bisa tampil (path gambar benar)
- [ ] Navbar `active` sesuai halaman yang sedang dibuka

---

*Modul Praktikum Pemrograman 1 — I.T Ghifari 2026*
