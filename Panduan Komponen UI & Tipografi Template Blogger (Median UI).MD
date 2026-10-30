# Panduan Komponen UI & Tipografi Template Blogger (Median UI)

Dokumentasi ini berisi panduan penggunaan 26 komponen UI dan pemformatan tipografi yang dapat disisipkan ke dalam artikel Blogger (terutama untuk template lini **Median UI / Jagodesain**).

## Daftar Isi

1. [Media & Gambar](#1-media--gambar)

   * [Image with Caption](#11-image-with-caption)

   * [Lightbox Image](#12-lightbox-image)

   * [Grid Images](#13-grid-images)

   * [Scroll Images](#14-scroll-images)

   * [Show/Hide Images](#15-showhide-images)

   * [Lazy Load Image](#16-lazy-load-image)

   * [Lazy Youtube](#17-lazy-youtube)

2. [Tipografi & Teks](#2-tipografi--teks)

   * [Text Indent](#21-text-indent)

   * [Drop Cap](#22-drop-cap)

   * [Blockquote](#23-blockquote)

   * [Note Block](#24-note-block)

   * [Post Break](#25-post-break)

   * [Post Reference](#26-post-reference)

3. [Daftar & Tabel](#3-daftar--tabel)

   * [Guide List](#31-guide-list)

   * [Pros & Cons List](#32-pros--cons-list)

   * [Tables](#33-tables)

4. [Elemen Interaktif](#4-elemen-interaktif)

   * [Tabs](#41-tabs)

   * [Table of Content (TOC)](#42-table-of-content-toc)

   * [Toggle Show/Hide (Spoiler)](#43-toggle-showhide-spoiler)

   * [Accordion](#44-accordion)

5. [Kode Program (Developer)](#5-kode-program-developer)

   * [Pros & Cons List](https://gemini.google.com/#32-pros--cons-list)

   * [Multitabs Syntax](#52-multitabs-syntax)

6. [Navigasi & Tombol](#6-navigasi--tombol)

   * [Related Posts (Manual)](#61-related-posts-manual)

   * [Links](#62-links)

   * [Download Card](#63-download-card)

   * [Button](#64-button)

## 1. Media & Gambar

### 1.1 Image with Caption

Menampilkan gambar disertai teks keterangan di bagian bawahnya.

```
<table class='tr-caption-container'>
  <tbody>
    <tr>
      <td>
        <img class='lazy full' alt='Judul Gambar' data-src='URL_GAMBAR' src='data:image/png;base64,R0lGODlhAQABAAD/ACwAAAAAAQABAAACADs='/>
      </td>
    </tr>
    <tr>
      <td class='tr-caption'>Teks keterangan gambar di sini</td>
    </tr>
  </tbody>
</table>

```

### 1.2 Lightbox Image

Menampilkan gambar yang dapat diklik untuk diperbesar/pop-up modal.

```
<div class='lightBox'>
  <details>
    <summary class='n'><span class='c flex center'></span></summary>
  </details>
  <img class='lazy' alt='Judul Gambar' data-src='URL_GAMBAR' src='data:image/png;base64,R0lGODlhAQABAAD/ACwAAAAAAQABAAACADs='/>
  <noscript><img alt='Judul Gambar' src='URL_GAMBAR'/></noscript>
</div>

```

### 1.3 Grid Images

Menata beberapa gambar dalam bentuk tata letak kisi (grid).

```
<div class='psImg grImg'>
  <div>
    <img class='lazy' alt='Gambar 1' data-src='URL_GAMBAR_1' src='data:image/png;base64,R0lGODlhAQABAAD/ACwAAAAAAQABAAACADs='/>
    <noscript><img alt='Gambar 1' src='URL_GAMBAR_1'/></noscript>
  </div>
  <div>
    <img class='lazy' alt='Gambar 2' data-src='URL_GAMBAR_2' src='data:image/png;base64,R0lGODlhAQABAAD/ACwAAAAAAQABAAACADs='/>
    <noscript><img alt='Gambar 2' src='URL_GAMBAR_2'/></noscript>
  </div>
</div>

```

### 1.4 Scroll Images

Galeri gambar berseri yang dapat di-scroll secara horizontal (terutama pada tampilan mobile).

```
<div class='psImg scImg scrlH'>
  <div>
    <img class='lazy' alt='Gambar 1' data-src='URL_GAMBAR_1' src='data:image/png;base64,R0lGODlhAQABAAD/ACwAAAAAAQABAAACADs='/>
    <noscript><img alt='Gambar 1' src='URL_GAMBAR_1'/></noscript>
  </div>
  <div>
    <img class='lazy' alt='Gambar 2' data-src='URL_GAMBAR_2' src='data:image/png;base64,R0lGODlhAQABAAD/ACwAAAAAAQABAAACADs='/>
    <noscript><img alt='Gambar 2' src='URL_GAMBAR_2'/></noscript>
  </div>
</div>

```

### 1.5 Show/Hide Images

Menyembunyikan sebagian galeri gambar dan memunculkan sisanya ketika tombol diklik.

> ⚠️ **Catatan:** Pastikan atribut `id` pada `<input>` sama dengan nilai atribut `for` pada `<label>`.

```
<input class='inImg hidden' id='for-hideImage' type='checkbox'>
<div class='psImg hdImg'>
  <div>
    <img class='lazy' alt='Gambar' data-src='URL_GAMBAR_1' src='data:image/png;base64,R0lGODlhAQABAAD/ACwAAAAAAQABAAACADs='/>
    <noscript><img alt='Gambar' src='URL_GAMBAR_1'/></noscript>
  </div>
  
  <div class='btImg'>
    <div>
      <img class='lazy' alt='Gambar' data-src='URL_GAMBAR_2' src='data:image/png;base64,R0lGODlhAQABAAD/ACwAAAAAAQABAAACADs='/>
      <noscript><img alt='Gambar' src='URL_GAMBAR_2'/></noscript>
    </div>
    
    <!-- Tombol Pemicu -->
    <label for='for-hideImage'>Show all</label>
  </div>

  <!-- Gambar Tersembunyi -->
  <div class='psImg shImg'>
    <div>
      <img class='lazy' alt='Gambar' data-src='URL_GAMBAR_3' src='data:image/png;base64,R0lGODlhAQABAAD/ACwAAAAAAQABAAACADs='/>
      <noscript><img alt='Gambar' src='URL_GAMBAR_3'/></noscript>
    </div>
  </div>
</div>

```

### 1.6 Lazy Load Image

Format penulisan gambar standar yang menunda pemuatan gambar (*lazy load*) demi mempercepat waktu muat halaman.

```
<div class='separator'>
  <img class='lazy' alt='Judul Gambar' data-src='URL_GAMBAR' src='data:image/png;base64,R0lGODlhAQABAAD/ACwAAAAAAQABAAACADs='/>
  <noscript><img alt='Judul Gambar' src='URL_GAMBAR'/></noscript>
</div>

```

### 1.7 Lazy Youtube

Format penundaan pemuatan video YouTube (*defer video*) agar tidak memberatkan kecepatan situs.

**Opsi 1: Custom Player**

```
<div class='lazyYt' data-embed='YOUTUBE_VIDEO_ID' style='z-index: 1;'>
  <div class='play'>
    <svg viewbox='0 0 213.7 213.7'><polygon class='t' points='73.5,62.5 148.5,105.8 73.5,149.1'></polygon><circle class='c' cx='106.8' cy='106.8' r='103.3'></circle></svg>
  </div>
</div>

```

**Opsi 2: Iframe Defer**

```
<div class='videoYt'>
  <iframe title='Lazy video iframe' class='lazy' data-src='//www.youtube.com/embed/YOUTUBE_VIDEO_ID' allow='accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture' allowfullscreen></iframe>
</div>

```

## 2. Tipografi & Teks

### 2.1 Text Indent

Membuat baris pertama dalam paragraf menjorok ke dalam.

```
<p class='pIndent'>Tuliskan paragraf teks Anda di sini...</p>

```

### 2.2 Drop Cap

Memperbesar huruf pertama pada paragraf.

```
<p><span class='dropCap'>T</span>eks paragraf dimulai dengan huruf pertama yang berukuran lebih besar...</p>

```

### 2.3 Blockquote

Elemen penanda kutipan teks.

**Model Standar:**

```
<blockquote>Teks kutipan di sini...</blockquote>

```

**Model Alternatif (S-1):**

```
<blockquote class='s-1'>
  <div>Teks kutipan alternatif di sini...</div>
</blockquote>

```

### 2.4 Note Block

Tampilan blok khusus untuk catatan atau peringatan.

**1. Catatan Standar (Warna Netral/Tema):**

```
<p class='note'>Teks catatan penting di sini...</p>

```

**2. Catatan Peringatan (Warning/Warna Merah):**

```
<p class='note wr'>Teks peringatan di sini...</p>

```

### 2.5 Post Break

Garis pembatas vertikal antar paragraf.

```
<!-- Garis Standar -->
<hr>

<!-- Garis Putus-putus (Dot) -->
<hr class='dot'>

<!-- Garis Lurus Tipis (Line) -->
<hr class='line'>

```

### 2.6 Post Reference

Gunakan komponen ini untuk menyajikan daftar sumber/referensi/catatan kaki di akhir tulisan.

**Referensi Tunggal:**

```
<p class='pRef'>Sumber: Nama Sumber, https://example.com/</p>

```

**Referensi Jamak (List):**

```
<div class='pRef'>
  <ol>
    <li>Referensi 1</li>
    <li>Referensi 2</li>
  </ol>
</div>

```

## 3. Daftar & Tabel

### 3.1 Guide List

Tampilan penomoran kustom untuk panduan atau langkah-langkah *tutorial*.

```
<ol class='step noList'>
  <li>Langkah pertama...</li>
  <li>Langkah kedua...</li>
  <li>Langkah ketiga...</li>
</ol>

```

### 3.2 Pros & Cons List

Tampilan khusus untuk membuat daftar kelebihan (pros) dan kekurangan (cons).

```
<b>Keunggulan:</b>
<ul class='pros noList'>
  <li>Poin kelebihan 1</li>
  <li>Poin kelebihan 2</li>
</ul>

<b>Kekurangan:</b>
<ul class='cons noList'>
  <li>Poin kekurangan 1</li>
  <li>Poin kekurangan 2</li>
</ul>

```

### 3.3 Tables

Menampilkan data tabel secara rapi dan responsif.

**Pilihan Class pada `<div>` Pembungkus:**

* `table` : Class utama tabel.

* `noWrap` : Mencegah pemotongan baris (*line-break*) pada teks sel.

* `w100` : Lebar tabel 100%.

* `noLine` : Menghilangkan garis baris vertikal.

* `withBg` : Memberikan warna latar pada baris.

* `hoverBg` : Efek perubahan warna baris ketika sorot kursor (*hover*).

```
<div class='table noWrap w100 hoverBg'>
  <table>
    <thead>
      <tr>
        <th>Header 1</th>
        <th>Header 2</th>
        <th>Header 3</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Data 1</td>
        <td>Data 2</td>
        <td>Data 3</td>
      </tr>
    </tbody>
  </table>
</div>

```

## 4. Elemen Interaktif

### 4.1 Tabs

Menampilkan beberapa konten yang terpisah dalam tab (maksimal 4 tab).

```
<!-- Pemicu Tab (Radio Input) -->
<input class='tbIn hidden' id='fTabs-1' type='radio' name='postTabs' checked>
<input class='tbIn hidden' id='fTabs-2' type='radio' name='postTabs'>

<!-- Tombol / Header Tab -->
<div class='tbHd scrlH'>
  <label for='fTabs-1' data-text='Tab 1'></label>
  <label for='fTabs-2' data-text='Tab 2'></label>
</div>

<!-- Isi Konten Tab -->
<div class='tbCn'>
  <div class='tbText-1'>
    Konten untuk Tab 1...
  </div>
  <div class='tbText-2'>
    Konten untuk Tab 2...
  </div>
</div>

```

### 4.2 Table of Content (TOC)

Membuat daftar isi artikel interaktif.

```
<details class='sp toc' open=''>
  <summary>Daftar Isi</summary>
  <div class='toC'>
    <ol>
      <li><a href='#heading_1'>Judul Bab 1</a></li>
      <li>
        <a href='#heading_2'>Judul Bab 2</a>
        <ol>
          <li><a href='#subheading_2a'>Sub-bab 2A</a></li>
        </ol>
      </li>
    </ol>
  </div>
</details>

```

> **Cara Menghubungkan TOC:**
> Tambahkan atribut `id` pada Tag Judul/Subjudul Anda:
> `<h2 id='heading_1'>Judul Bab 1</h2>`

### 4.3 Toggle Show/Hide (Spoiler)

Penyembunyi konten sederhana berbasis `<details>` native HTML.

```
<details class='sp notranslate'>
  <summary>Buka Spoiler</summary>
  <p>Isi teks tersembunyi yang akan terbuka saat diklik.</p>
</details>

```

### 4.4 Accordion

Komponen accordion yang cocok untuk daftar FAQ / Tanya Jawab interaktif.

```
<div class='showH'>
  <!-- Item 1 -->
  <details class='ac alt'>
    <summary>Pertanyaan 1?</summary>
    <div class='aC'>
      <p>Jawaban pertanyaan 1...</p>
    </div>
  </details>

  <!-- Item 2 -->
  <details class='ac alt'>
    <summary>Pertanyaan 2?</summary>
    <div class='aC'>
      <p>Jawaban pertanyaan 2...</p>
    </div>
  </details>
</div>

```

## 5. Kode Program (Developer)

### 5.1 Syntax Highlighter

Menampilkan blok kode program dengan latar belakang khusus.

```
<!-- Opsi class: pre html / pre css / pre js -->
<div class='pre html notranslate'>
  <pre>
&lt;div class="contoh"&gt;Kode HTML di sini&lt;/div&gt;
  </pre>
</div>

```

> 💡 **Warna Teks Manual:** Gunakan `<i class='red'>teks</i>`, `<i class='blue'>teks</i>`, atau `<i class='gray'>teks</i>` di dalam tag `<pre>`.

### 5.2 Multitabs Syntax

Menampilkan beberapa ragam kode bahasa pemrograman sekaligus dalam 1 wadah bertab.

```
<div class='pre tb'>
  <!-- Pemicu Tab -->
  <input class='prei hidden' id='preT-1' type='radio' name='preTab' checked>
  <input class='prei hidden' id='preT-2' type='radio' name='preTab'>

  <!-- Header Tab -->
  <div class='preH tbHd scrlH'>
    <label for='preT-1' data-text='HTML'></label>
    <label for='preT-2' data-text='CSS'></label>
  </div>

  <!-- Konten Kode -->
  <div class='preC-1'>
    <pre>Kode HTML di sini...</pre>
  </div>
  <div class='preC-2'>
    <pre>Kode CSS di sini...</pre>
  </div>
</div>

```

## 6. Navigasi & Tombol

### 6.1 Related Posts (Manual)

Rekomendasi tautan artikel terkait yang dapat ditempatkan di tengah paragraf.

```
<div class='pRelate notranslate'>
  <b>Artikel Terkait:</b>
  <ul>
    <li><a href='URL_ARTIKEL_1'>Judul Artikel 1</a></li>
    <li><a href='URL_ARTIKEL_2'>Judul Artikel 2</a></li>
  </ul>
</div>

```

### 6.2 Links

Tautan interaktif dengan tanda kustom di depannya.

```
<!-- 1. Tautan Update/Baru -->
<a class='new' href='URL_TAUTAN'>Tautan Baru</a>

<!-- 2. Tautan Gratis/Free -->
<a class='free' href='URL_TAUTAN'>Download Gratis</a>

<!-- 3. Tautan Eksternal -->
<a class='extL' href='URL_TAUTAN'>Situs Luar</a>

```

### 6.3 Download Card

Kartu informasi file unduhan yang rapi beserta ukuran dan tombol aksi.

```
<div class='dlBox'>
  <span class='fT' data-text='zip'></span>
  <div class='fN'>
    <span>nama_file.zip</span>
    <span class='fS'>200kb</span>
  </div>
  
  <a class='button' aria-label='Download' href='URL_DOWNLOAD'>
    <svg class='line' viewBox='0 0 24 24' stroke-miterlimit='10'><path d='M9.31995 11.6799L11.8799 14.2399L14.4399 11.6799'/><path d='M11.88 4V14.17'/><path d='M20 12.1799C20 16.5999 17 20.1799 12 20.1799C7 20.1799 4 16.5999 4 12.1799'/></svg>
  </a>
</div>

```

### 6.4 Button

Gaya tombol aksi (*Call to Action*).

```
<!-- 1. Tombol Standar -->
<a class='button' href='URL_TAUTAN'>Tombol</a>

<!-- 2. Tombol Garis Tepi (Outline) -->
<a class='button ln' href='URL_TAUTAN'>Tombol</a>

<!-- 3. Tombol Tanpa Latar (Flat) -->
<a class='button sc' href='URL_TAUTAN'>Tombol</a>

<!-- 4. Dua Tombol Berdampingan -->
<div class='btnF'>
  <a class='button ln' href='URL_1'><span>Info</span></a>
  <a class='button' href='URL_2'><span>Download</span></a>
</div>

```
