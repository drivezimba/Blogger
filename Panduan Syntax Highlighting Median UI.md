# Panduan Otomatisasi Syntax Highlighting Median UI (Highlight.js)

Dokumentasi ini berisi langkah-langkah mengaktifkan pewarnaan kode otomatis (*syntax highlighting*) pada template **Median UI** (Jagodesain) tanpa perlu menambahkan class khusus seperti `language-*` atau tagging manual (`<i>`).

---

## 1. Pemasangan Skrip di Template Blogger

Tambahkan kode JavaScript berikut sebelum tag penutup `</body>` atau `</head>` pada tema/template Blogger Anda.

```html
<!-- Highlight.js Auto-Color untuk Median UI -->
<script src='https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.9.0/highlight.min.js'></script>
<script>
  document.addEventListener('DOMContentLoaded', () => {
    document.querySelectorAll('.pre pre').forEach((el) => {
      hljs.highlightElement(el);
    });
  });
</script>
```

> **Catatan:** Skrip di atas memanfaatkan aturan CSS bawaan Median UI (`.hljs-comment`, `.hljs-name`, `.hljs-keyword`, `.hljs-string`, dll.) sehingga tidak membutuhkan file CSS eksternal tambahan.

---

## 2. Struktur Kode HTML untuk Postingan Artikel

Gunakan class bawaan standar Median UI (`.html`, `.css`, `.js`) pada pembungkus `<div class='pre'>`. Karakter khusus seperti `<` dan `>` di dalam `<pre>` wajib di-*escape* menjadi `&lt;` dan `&gt;`.

### A. Kode HTML
```html
<div class='pre html'>
  <pre>&lt;!-- Contoh Tombol Standar Median UI --&gt;
&lt;a class='button' href='https://example.com'&gt;Download Now&lt;/a&gt;

&lt;!-- Contoh Note Block --&gt;
&lt;p class='note wr'&gt;Ini adalah pesan peringatan penting!&lt;/p&gt;</pre>
</div>
```

### B. Kode CSS
```html
<div class='pre css'>
  <pre>/* Kustomisasi Kotak Pesan */
.custom-box {
  background-color: #f8f9fa;
  border-left: 4px solid #007bff;
  padding: 15px;
  border-radius: 6px;
  font-size: 14px;
}</pre>
</div>
```

### C. Kode JavaScript
```html
<div class='pre js'>
  <pre>// Fungsi untuk menampilkan pesan salam
function sapaPengunjung(nama) {
  if (nama) {
    console.log("Halo, " + nama + "! Selamat datang di blog kami.");
  } else {
    alert("Selamat datang, Pengunjung!");
  }
}

// Memanggil fungsi
sapaPengunjung("Admin");</pre>
</div>
```

### D. Multitabs Syntax
```html
<div class='pre tb'>
  <input class='prei hidden' id='preT-1' type='radio' name='preTab' checked=''/>
  <input class='prei hidden' id='preT-2' type='radio' name='preTab'/>
  <input class='prei hidden' id='preT-3' type='radio' name='preTab'/>
  
  <div class='preHd scrlH'>
    <label for='preT-1' data-text='HTML'></label>
    <label for='preT-2' data-text='CSS'></label>
    <label for='preT-3' data-text='JavaScript'></label>
  </div>
  
  <div class='preCn'>
    <div class='preC html'>
      <pre>&lt;button id='btnAksi' class='button'&gt;Klik Saya&lt;/button&gt;</pre>
    </div>
    <div class='preC css'>
      <pre>#btnAksi {
  background-color: #28a745;
  color: #ffffff;
}</pre>
    </div>
    <div class='preC js'>
      <pre>document.getElementById('btnAksi').addEventListener('click', function() {
  alert('Tombol berhasil diklik!');
});</pre>
    </div>
  </div>
</div>
```

---

## 3. Contoh Lengkap Postingan Uji Coba

Berikut adalah draf lengkap satu postingan artikel yang menggabungkan elemen gambar, tipografi, daftar isi, dan skrip syntax highlighting bawaan Median UI:

```html
<!-- Gambar Utama Postingan (Lazy Load Image) -->
<div class='separator'>
  <img class='lazy' alt='Pemandangan Alam Bebas Hak Cipta' data-src='https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=1200&q=80' src='data:image/png;base64,R0lGODlhAQABAAD/ACwAAAAAAQABAAACADs='/>
  <noscript><img alt='Pemandangan Alam Bebas Hak Cipta' src='https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=1200&q=80'/></noscript>
</div>

<!-- Deskripsi & Drop Cap -->
<p><span class='dropCap'>A</span>rtikel ini dibuat khusus untuk menguji dan menampilkan implementasi dari berbagai komponen bawaan template Median UI, khususnya pada penulisan kode program (Syntax Highlighter), elemen tipografi, dan gaya gambar yang interaktif.</p>

<!-- Table of Contents (Daftar Isi) -->
<details class='sp toc' open=''>
  <summary>Daftar Isi</summary>
  <div class='toC'>
    <ol>
      <li><a href='#heading_1'>1. Pengujian Kode HTML</a></li>
      <li><a href='#heading_2'>2. Pengujian Kode CSS</a></li>
      <li><a href='#heading_3'>3. Pengujian Kode JavaScript</a></li>
      <li><a href='#heading_4'>4. Pengujian Multitabs Syntax</a></li>
    </ol>
  </div>
</details>

<hr class='dot'/>

<!-- Section 1: Kode HTML -->
<h2 id='heading_1'>1. Pengujian Kode HTML</h2>
<p>Berikut adalah contoh struktur pemanggilan tombol bawaan Median UI menggunakan kode HTML. Elemen karakter telah di-escape agar tampil sempurna sebagai sintaksis kode.</p>

<div class='pre html'>
  <pre>&lt;!-- Contoh Tombol Standar Median UI --&gt;
&lt;a class='button' href='https://example.com'&gt;Download Now&lt;/a&gt;

&lt;!-- Contoh Note Block --&gt;
&lt;p class='note wr'&gt;Ini adalah pesan peringatan penting!&lt;/p&gt;</pre>
</div>

<p class='note'><strong>Catatan:</strong> Kode di atas dapat Anda gunakan langsung untuk menambahkan elemen pemicu atau aksentuasi pada artikel Anda.</p>

<!-- Section 2: Kode CSS -->
<h2 id='heading_2'>2. Pengujian Kode CSS</h2>
<p>Dibawah ini adalah contoh sintaksis CSS yang digunakan untuk mengatur kustomisasi tampilan kartu atau kotak latar belakang.</p>

<div class='pre css'>
  <pre>/* Kustomisasi Kotak Pesan */
.custom-box {
  background-color: #f8f9fa;
  border-left: 4px solid #007bff;
  padding: 15px;
  border-radius: 6px;
  font-size: 14px;
}</pre>
</div>

<!-- Section 3: Kode JavaScript -->
<h2 id='heading_3'>3. Pengujian Kode JavaScript</h2>
<p>Berikut adalah skrip sederhana dalam JavaScript untuk menampilkan notifikasi dialog saat pengguna mengeklik sebuah tombol di halaman web.</p>

<div class='pre js'>
  <pre>// Fungsi untuk menampilkan pesan salam
function sapaPengunjung(nama) {
  if (nama) {
    console.log("Halo, " + nama + "! Selamat datang di blog kami.");
  } else {
    alert("Selamat datang, Pengunjung!");
  }
}

// Memanggil fungsi
sapaPengunjung("Admin");</pre>
</div>

<!-- Section 4: Multitabs Syntax -->
<h2 id='heading_4'>4. Pengujian Multitabs Syntax</h2>
<p>Anda juga dapat menggabungkan kode HTML, CSS, dan JavaScript ke dalam satu kotak multitab interaktif seperti berikut:</p>

<div class='pre tb'>
  <input class='prei hidden' id='preT-1' type='radio' name='preTab' checked=''/>
  <input class='prei hidden' id='preT-2' type='radio' name='preTab'/>
  <input class='prei hidden' id='preT-3' type='radio' name='preTab'/>
  
  <div class='preHd scrlH'>
    <label for='preT-1' data-text='HTML'></label>
    <label for='preT-2' data-text='CSS'></label>
    <label for='preT-3' data-text='JavaScript'></label>
  </div>
  
  <div class='preCn'>
    <div class='preC html'>
      <pre>&lt;button id='btnAksi' class='button'&gt;Klik Saya&lt;/button&gt;</pre>
    </div>
    <div class='preC css'>
      <pre>#btnAksi {
  background-color: #28a745;
  color: #ffffff;
}</pre>
    </div>
    <div class='preC js'>
      <pre>document.getElementById('btnAksi').addEventListener('click', function() {
  alert('Tombol berhasil diklik!');
});</pre>
    </div>
  </div>
</div>

<blockquote class='s-1'>
  <div>Semua komponen di atas sudah terstruktur sesuai standar CSS dan JavaScript dari Median UI agar dapat dirender dengan optimal dan responsif di seluruh perangkat.</div>
</blockquote>

<p class='pRef'>Sumber: Dokumentasi Komponen Median UI (Jagodesain)</p>
```
