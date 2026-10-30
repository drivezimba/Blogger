# 🎧 Floating Audio Player untuk Blogger

Floating Audio Player adalah komponen pemutar audio mengambang (Floating Action Button) yang dapat digunakan untuk memutar audio langsung dari artikel Blogger.

Komponen ini sangat cocok digunakan untuk:

- Murottal Al-Qur'an
- Podcast
- Audiobook
- Rekaman Kajian
- Materi Pembelajaran Audio
- Narasi Artikel

---

## ✨ Fitur

✅ Floating Action Button (FAB)

✅ Tampilan Modern dan Responsif

✅ Progress Bar Interaktif

✅ Play / Pause

✅ Volume Control

✅ Mute / Unmute

✅ Playback Speed

✅ Skip 10 Detik Maju & Mundur

✅ Metadata Dinamis

✅ Tanpa Library Eksternal

✅ Mobile Friendly

✅ Hanya Aktif pada Postingan yang Memiliki Audio

---

## 📷 Tampilan

Ketika postingan memiliki sumber audio, tombol pemutar akan muncul di sisi kanan bawah layar.

Pengunjung dapat membuka panel audio untuk:

- Memutar audio
- Mengubah kecepatan
- Mengatur volume
- Melihat durasi audio
- Melompat ke bagian tertentu audio

---

## 🚀 Instalasi

### Langkah 1

Buka:

```text
Tema → Edit HTML
```

Cari kode:

```html
</body>
```

Lalu tempelkan kode Floating Audio Player tepat di atas tag tersebut.

---

### Langkah 2

Simpan tema.

---

## 📄 Menambahkan Audio ke Postingan

Tambahkan kode berikut di dalam postingan HTML:

```html
<div id="post-audio-data"
     data-src="https://link.cdn/file/nama-file.mp3"
     data-title="078 - Surah An-Naba'"
     data-subtitle="Murottal Al-Qur'an">
</div>
```

---

## 📝 Penjelasan Atribut

### data-src

Berisi URL file audio.

Contoh:

```html
data-src="https://cdn.example.com/audio/an-naba.mp3"
```

---

### data-title

Judul yang ditampilkan pada pemutar.

Contoh:

```html
data-title="078 - Surah An-Naba'"
```

---

### data-subtitle

Subjudul atau keterangan tambahan.

Contoh:

```html
data-subtitle="Murottal Al-Qur'an"
```

---

## 📚 Contoh Penggunaan

### Murottal

```html
<div id="post-audio-data"
     data-src="https://cdn.example.com/an-naba.mp3"
     data-title="078 - Surah An-Naba'"
     data-subtitle="Murottal Al-Qur'an">
</div>
```

---

### Podcast

```html
<div id="post-audio-data"
     data-src="https://cdn.example.com/podcast-01.mp3"
     data-title="Episode #01"
     data-subtitle="Belajar Blogger">
</div>
```

---

### Audiobook

```html
<div id="post-audio-data"
     data-src="https://cdn.example.com/book-chapter-1.mp3"
     data-title="Bab 1"
     data-subtitle="Audiobook Sejarah">
</div>
```

---

## ⚙️ Playback Speed

Komponen mendukung beberapa kecepatan pemutaran:

| Kecepatan |
|------------|
| 0.75x |
| 1x |
| 1.25x |
| 1.5x |
| 1.75x |
| 2x |

Klik tombol kecepatan untuk mengganti mode.

---

## 💡 Tips Penggunaan

### Gunakan CDN

Sebaiknya audio disimpan pada:

- BunnyCDN
- Cloudflare R2
- GitHub Release
- Backblaze B2
- Storage pribadi

Agar pemutaran lebih cepat dan stabil.

---

### Kompres Audio

Untuk menghemat bandwidth:

- Gunakan format MP3
- Bitrate 64 kbps – 128 kbps
- Hindari file terlalu besar

---

### Gunakan Judul yang Jelas

Contoh yang baik:

```html
data-title="078 - Surah An-Naba'"
```

Hindari:

```html
data-title="Audio 1"
```

---

## ❓ Troubleshooting

### Tombol Tidak Muncul

Pastikan kode berikut ada pada postingan:

```html
<div id="post-audio-data"></div>
```

dan memiliki:

```html
data-src
```

yang valid.

---

### Audio Tidak Bisa Diputar

Periksa:

- URL audio masih aktif
- File dapat diakses publik
- Tidak ada proteksi hotlink
- Format audio didukung browser

---

### Durasi Tidak Tampil

Pastikan server mengizinkan browser membaca metadata audio.

---

## ✅ Browser Support

- Chrome
- Edge
- Firefox
- Safari
- Browser Android
- Browser iOS

---

## 🔄 Changelog

### v1.0

- Floating Audio Player
- Progress Bar
- Playback Speed
- Volume Control
- Skip Audio
- Dynamic Metadata

---

## ⭐ Dukungan

Jika panduan ini bermanfaat, jangan lupa beri ⭐ pada repository agar lebih mudah ditemukan oleh pengguna Blogger lainnya.
