# Panduan Membuat Halaman Blank Canvas (Polos Total) di Blogger (Median UI & Template Lain)

Panduan ini berisi cara mengubah **Halaman (Page)** atau **Postingan (Post)** di Blogger menjadi **100% Polos (Blank Canvas)** tanpa *header*, *navbar*, *sidebar*, *box postingan*, maupun *footer* bawaan tema.

Metode ini sangat cocok untuk membuat **Landing Page**, **CV/Resume HTML**, **Halaman Portofolio**, atau halaman khusus dengan desain sendiri (*custom layout*).

---

## 💡 Cara Kerja

Metode ini menggunakan skrip JavaScript sederhana untuk merekayasa *Document Object Model* (DOM) pada browser. Saat halaman selesai dimuat (`DOMContentLoaded`), JavaScript akan:
1. Mengambil seluruh isi kode HTML yang Anda tulis di dalam kontainer khusus.
2. Mengosongkan dan mengganti seluruh isi tag `<body>` blog dengan kode Anda.
3. Menghapus (*reset*) seluruh gaya (*style*) dan kelas (*class*) bawaan tema Blogger.

---

## 🚀 Langkah Pemasangan

### Langkah 1: Buat Halaman / Postingan Baru
1. Masuk ke **Dashboard Blogger**.
2. Pilih menu **Halaman (Pages)** atau **Postingan (Posts)**, lalu klik **+ Halaman Baru** atau **+ Postingan Baru**.

### Langkah 2: Ubah Mode ke Tampilan HTML
1. Di editor Blogger, klik ikon **Pensil** di pojok kiri atas.
2. Ubah moda penulisan dari **Tampilan Menulis (Compose view)** menjadi **Tampilan HTML (HTML view)**.

### Langkah 3: Tempel Kode Skrip & HTML Anda
Hapus semua isi draft jika ada, lalu tempelkan struktur kode berikut:

```html
<script>
  document.addEventListener('DOMContentLoaded', function() {
    // 1. Ambil seluruh konten di dalam ID 'my-custom-landing'
    var myContent = document.getElementById('my-custom-landing').innerHTML;
    
    // 2. Kosongkan seluruh body halaman dan ganti dengan konten Anda
    document.body.innerHTML = myContent;
    
    // 3. Reset atribut margin, padding, dan background body
    document.body.removeAttribute('class');
    document.body.removeAttribute('style');
    document.body.style.margin = '0';
    document.body.style.padding = '0';
    document.body.style.background = '#ffffff';
  });
</script>

<!-- WADAH KONTEN KUSTOM ANDA -->
<div id="my-custom-landing">

  <!-- =================================================== -->
  <!-- TEMPELKAN KODE HTML / CSS / JS KUSTOM ANDA DI SINI  -->
  <!-- =================================================== -->

</div>
```

---

## 📝 Contoh Penggunaan (Halaman CV/Resume Simple)

Berikut adalah contoh lengkap penerapan halaman polos untuk membuat CV interaktif sederhana:

```html
<script>
  document.addEventListener('DOMContentLoaded', function() {
    var myContent = document.getElementById('my-custom-landing').innerHTML;
    document.body.innerHTML = myContent;
    document.body.removeAttribute('class');
    document.body.removeAttribute('style');
    document.body.style.margin = '0';
    document.body.style.padding = '0';
    document.body.style.background = '#f4f6f8';
  });
</script>

<div id="my-custom-landing">
  <style>
    .cv-container {
      max-width: 800px;
      margin: 40px auto;
      background: #ffffff;
      padding: 40px;
      border-radius: 12px;
      box-shadow: 0 4px 20px rgba(0,0,0,0.08);
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      color: #333333;
    }
    .cv-header {
      border-bottom: 2px solid #eef2f5;
      padding-bottom: 20px;
      margin-bottom: 20px;
    }
    .cv-header h1 {
      margin: 0;
      color: #1a202c;
      font-size: 28px;
    }
    .cv-header p {
      margin: 5px 0 0;
      color: #4a5568;
    }
    .cv-section {
      margin-bottom: 24px;
    }
    .cv-section h2 {
      font-size: 18px;
      color: #2b6cb0;
      margin-bottom: 10px;
    }
  </style>

  <div class="cv-container">
    <div class="cv-header">
      <h1>Nama Anda</h1>
      <p>Web Developer & UI/UX Designer</p>
    </div>

    <div class="cv-section">
      <h2>Tentang Saya</h2>
      <p>Halo! Saya seorang pengembang web yang berfokus pada pembuatan antarmuka modern, responsif, dan ramah pengguna.</p>
    </div>

    <div class="cv-section">
      <h2>Pengalaman Kerja</h2>
      <ul>
        <li><strong>Frontend Developer</strong> - Perusahaan ABC (2022 - Sekarang)</li>
        <li><strong>Web Designer</strong> - Agensi XYZ (2020 - 2022)</li>
      </ul>
    </div>
  </div>
</div>
```

---

## 📌 Catatan Tambahan

- **Responsif:** Pastikan Anda menyertakan meta tag viewport jika menggunakan framework seperti Tailwind atau Bootstrap di dalam kustom HTML Anda.
- **Library Eksternal:** Anda dapat menyertakan CDN CSS/JS (seperti FontAwesome, Tailwind CSS, Google Fonts) langsung di dalam `<div id="my-custom-landing">`.
- **Kompatibilitas:** Metode ini bekerja di semua template Blogger (Median UI, Plus UI, F visual, Vesper, dsb.) karena memanipulasi DOM secara langsung di sisi *client*.

---

  Dibuat untuk kebutuhan kustomisasi halaman statis Blogger.
