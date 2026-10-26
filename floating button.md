# Panduan Memasang Floating Audio Player Dinamis di Blogger

Sistem audio melayang (Floating Action Button / FAB) ini dirancang khusus untuk Blogger. Skrip ini sangat ringan, responsif, dan hanya akan muncul jika sebuah postingan memiliki link audio yang disematkan.

## Fitur Unggulan
- **Ringan & Cepat:** CSS dan JS sudah di-*minify*.
- **Otomatis Tampil/Sembunyi:** Player hanya muncul di artikel yang memiliki tag khusus.
- **Fitur Lengkap:** Play/Pause, Progress Bar, Rewind/Forward (-10s / +10s), Playback Speed, dan Volume/Mute.
- **Desain Modern:** Menggunakan efek *glassmorphism* (blur) bergaya iOS/Modern UI.

---

## Langkah 1: Pasang CSS di Edit HTML Tema

1. Masuk ke dashboard **Blogger** > menu **Tema** > klik tanda panah ke bawah > pilih **Edit HTML**.
2. Cari kode `</head>`.
3. Salin kode CSS di bawah ini dan letakkan tepat **di atas** kode `</head>`.

```html
<style>.fab-audio-wrapper{position:fixed;bottom:90px;right:20px;z-index:999999;font-family:system-ui,-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,sans-serif;display:none}.fab-trigger-btn{width:56px;height:56px;border-radius:50%;background:#3b82f6;color:#fff;border:none;box-shadow:0 10px 25px rgba(59,130,246,.4);cursor:pointer;display:flex;align-items:center;justify-content:center;transition:transform .3s cubic-bezier(.4,0,.2,1),background .3s}.fab-trigger-btn:hover{transform:scale(1.05);background:#2563eb}.fab-panel{position:absolute;bottom:75px;right:0;width:calc(100vw - 40px);max-width:340px;background:rgba(15,23,42,.95);backdrop-filter:blur(12px);-webkit-backdrop-filter:blur(12px);border:1px solid rgba(255,255,255,.1);border-radius:16px;padding:16px;box-shadow:0 20px 40px rgba(0,0,0,.4);color:#f8fafc;display:none;flex-direction:column;gap:12px;box-sizing:border-box}.fab-panel.active{display:flex;animation:fabPop .3s cubic-bezier(.16,1,.3,1) forwards}@keyframes fabPop{0%{opacity:0;transform:translateY(20px) scale(.95)}100%{opacity:1;transform:translateY(0) scale(1)}}.fab-header{display:flex;align-items:center;justify-content:space-between}.fab-header-left{display:flex;align-items:center;gap:12px;overflow:hidden}.fab-icon-box{width:36px;height:36px;background:rgba(59,130,246,.15);color:#60a5fa;border-radius:10px;display:flex;align-items:center;justify-content:center;flex-shrink:0}.fab-text-box{display:flex;flex-direction:column;overflow:hidden}.fab-title{font-size:14px;font-weight:600;margin:0;color:#fff;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}.fab-subtitle{font-size:11px;color:#94a3b8;margin:2px 0 0}.fab-close-btn{background:0 0;border:none;color:#94a3b8;cursor:pointer;padding:6px;border-radius:50%;display:flex;align-items:center;justify-content:center;transition:.2s}.fab-close-btn:hover{background:rgba(255,255,255,.1);color:#fff}.fab-progress-section{display:flex;flex-direction:column;gap:6px}.fab-progress-track{width:100%;height:5px;background:rgba(255,255,255,.1);border-radius:4px;cursor:pointer;position:relative;overflow:hidden}.fab-progress-fill{height:100%;width:0;background:#3b82f6;border-radius:4px;pointer-events:none}.fab-time-wrap{display:flex;justify-content:space-between;font-size:10px;color:#94a3b8;font-variant-numeric:tabular-nums}.fab-controls{display:flex;align-items:center;justify-content:space-between}.fab-btn{background:0 0;border:none;color:#cbd5e1;cursor:pointer;border-radius:8px;display:flex;align-items:center;gap:4px;font-size:11px;font-weight:600;transition:.2s;padding:6px}.fab-btn:hover{color:#fff}.fab-btn-play{width:42px;height:42px;background:#3b82f6;color:#fff;border-radius:50%;justify-content:center;padding:0;box-shadow:0 4px 10px rgba(59,130,246,.3)}.fab-btn-play:hover{background:#2563eb;transform:scale(1.05)}.fab-speed-badge{background:rgba(255,255,255,.08);color:#60a5fa;font-size:11px;font-weight:700;padding:4px 10px;border-radius:12px;cursor:pointer;border:1px solid rgba(255,255,255,.05)}.fab-speed-badge:hover{background:rgba(255,255,255,.15)}.fab-vol-container{display:flex;align-items:center;gap:6px}.fab-vol-slider{width:45px;accent-color:#3b82f6;cursor:pointer;height:4px}</style>
```

---

## Langkah 2: Pasang HTML Struktur & JavaScript di Tema

1. Masih di dalam editor tema, cari kode `</body>` (biasanya berada di paling bawah kode tema).
2. Salin gabungan HTML dan script JS di bawah ini, lalu letakkan tepat **di atas** `</body>`.
3. Klik tombol **Simpan Tema**.

```html
<div class="fab-audio-wrapper" id="global-fab-player">
  <button class="fab-trigger-btn" id="fab-trigger" title="Buka Audio">
    <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor" style="stroke:none;"><path d="M8 5v14l11-7z"></path></svg>
  </button>
  <div class="fab-panel" id="fab-panel">
    <audio id="fab-audio" preload="metadata"><source id="fab-audio-src" src="" type="audio/mpeg"></audio>
    <div class="fab-header">
      <div class="fab-header-left">
        <div class="fab-icon-box">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor" style="stroke:none;"><rect x="3" y="9" width="3" height="6" rx="1"></rect><rect x="8" y="4" width="3" height="16" rx="1"></rect><rect x="13" y="7" width="3" height="10" rx="1"></rect><rect x="18" y="11" width="3" height="2" rx="1"></rect></svg>
        </div>
        <div class="fab-text-box">
          <span class="fab-title" id="fab-dyn-title">Loading...</span>
          <span class="fab-subtitle" id="fab-dyn-subtitle">Loading...</span>
        </div>
      </div>
      <button class="fab-close-btn" id="fab-close" title="Tutup Panel"><svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor" style="stroke:none;"><path d="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"></path></svg></button>
    </div>
    <div class="fab-progress-section">
      <div class="fab-progress-track" id="fab-prog-bg"><div class="fab-progress-fill" id="fab-prog-bar"></div></div>
      <div class="fab-time-wrap"><span id="fab-time-cur">00:00</span><span id="fab-time-dur">--:--</span></div>
    </div>
    <div class="fab-controls">
      <button class="fab-speed-badge" id="fab-speed">1x</button>
      <button class="fab-btn" id="fab-rewind" title="Mundur 10 Detik"><svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor" style="stroke:none;"><path d="M11 18V6l-8.5 6 8.5 6zm.5-6l8.5 6V6l-8.5 6z"></path></svg>-10s</button>
      <button class="fab-btn fab-btn-play" id="fab-play">
        <svg id="fab-icon-play" width="22" height="22" viewBox="0 0 24 24" fill="currentColor" style="stroke:none;"><path d="M8 5v14l11-7z"></path></svg>
        <svg id="fab-icon-pause" width="22" height="22" viewBox="0 0 24 24" fill="currentColor" style="display:none; stroke:none;"><path d="M6 19h4V5H6v14zm8-14v14h4V5h-4z"></path></svg>
      </button>
      <button class="fab-btn" id="fab-forward" title="Maju 10 Detik">+10s<svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor" style="stroke:none;"><path d="M4 18l8.5-6L4 6v12zm9-12v12l8.5-6L13 6z"></path></svg></button>
      <div class="fab-vol-container">
        <button class="fab-btn" id="fab-mute" style="padding:4px;"><svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor" style="stroke:none;"><path d="M3 9v6h4l5 5V4L7 9H3zm13.5 3c0-1.77-1.02-3.29-2.5-4.03v8.05c1.48-.73 2.5-2.25 2.5-4.02zM14 3.23v2.06c2.89.86 5 3.54 5 6.71s-2.11 5.85-5 6.71v2.06c4.01-.91 7-4.49 7-8.77s-2.99-7.86-7-8.77z"></path></svg></button>
        <input type="range" class="fab-vol-slider" id="fab-vol" min="0" max="1" step="0.05" value="1">
      </div>
    </div>
  </div>
</div>
<script>document.addEventListener("DOMContentLoaded",()=>{let e=document.querySelector(".has-audio-player");if(e){let t=document.getElementById("global-fab-player"),d=document.getElementById("fab-audio"),a=document.getElementById("fab-audio-src"),n=document.getElementById("fab-dyn-title"),o=document.getElementById("fab-dyn-subtitle");if(!t||!d)return;a.src=e.getAttribute("data-audio"),n.textContent=e.getAttribute("data-title")||"Audio",o.textContent=e.getAttribute("data-subtitle")||"",d.load(),t.style.display="block";let l=document.getElementById("fab-trigger"),i=document.getElementById("fab-panel"),s=document.getElementById("fab-close"),c=document.getElementById("fab-play"),r=document.getElementById("fab-icon-play"),u=document.getElementById("fab-icon-pause"),m=document.getElementById("fab-prog-bg"),y=document.getElementById("fab-prog-bar"),f=document.getElementById("fab-time-cur"),b=document.getElementById("fab-time-dur"),p=document.getElementById("fab-speed"),v=document.getElementById("fab-rewind"),g=document.getElementById("fab-forward"),E=document.getElementById("fab-vol"),h=document.getElementById("fab-mute"),B=[1,1.25,1.5,1.75,2,.75],w=0;l.addEventListener("click",()=>i.classList.toggle("active")),s.addEventListener("click",()=>i.classList.remove("active"));let L=e=>{if(isNaN(e)||!isFinite(e))return"00:00";let t=Math.floor(e/60),d=Math.floor(e%60);return(t<10?"0":"")+t+":"+(d<10?"0":"")+d},T=e=>{e?(r.style.display="none",u.style.display="block"):(r.style.display="block",u.style.display="none")};c.addEventListener("click",()=>{d.paused?d.play().then(()=>T(!0)).catch(()=>alert("Gagal memutar audio. Pastikan koneksi internet Anda stabil.")):(d.pause(),T(!1))}),d.addEventListener("ended",()=>{T(!1),y.style.width="0%",f.textContent="00:00"});let M=()=>{d.duration&&!isNaN(d.duration)&&(b.textContent=L(d.duration))};d.addEventListener("loadedmetadata",M),d.addEventListener("durationchange",M),d.addEventListener("timeupdate",()=>{if(!isNaN(d.duration)&&d.duration>0){f.textContent=L(d.currentTime);let e=d.currentTime/d.duration*100;y.style.width=e+"%"}}),m.addEventListener("click",e=>{if(!d.duration||isNaN(d.duration))return;let t=m.getBoundingClientRect(),a=(e.clientX-t.left)/t.width;d.currentTime=a*d.duration}),p.addEventListener("click",()=>{w=(w+1)%B.length,d.playbackRate=B[w],p.textContent=B[w]+"x"}),v.addEventListener("click",()=>{isNaN(d.currentTime)||(d.currentTime=Math.max(0,d.currentTime-10))}),g.addEventListener("click",()=>{isNaN(d.duration)||(d.currentTime=Math.min(d.duration,d.currentTime+10))}),E.addEventListener("input",e=>{d.volume=e.target.value,d.muted=0===d.volume,h.style.opacity=d.muted?"0.5":"1"}),h.addEventListener("click",()=>{d.muted=!d.muted,h.style.opacity=d.muted?"0.5":"1",!d.muted&&0===d.volume&&(d.volume=1,E.value=1)})}});</script>
```

---

## Langkah 3: Cara Menerapkan di Postingan (Artikel)

Setiap kali Anda membuat atau mengedit postingan yang ingin dipasangi audio, ubah mode editor Blogger ke **Tampilan HTML** (HTML View). 

Letakkan kode pendek berikut ini di bagian paling atas atau paling bawah artikel Anda:

```html
<div class="has-audio-player" 
     data-audio="[https://islamdownload.net/r/123855/078-An-Naba.mp3](https://islamdownload.net/r/123855/078-An-Naba.mp3)" 
     data-title="078 - Surah An-Naba'" 
     data-subtitle="Murottal Al-Qur'an">
</div>
```

**Keterangan Atribut:**
- `data-audio`: Masukkan URL langsung menuju file audio (misal: `.mp3`).
- `data-title`: Masukkan judul utama yang ingin ditampilkan di dalam player.
- `data-subtitle`: Masukkan deskripsi singkat (misal: nama qari, jenis murrotal, atau kategori).

### Bagaimana Sistem Ini Bekerja?
JavaScript di tema secara otomatis memindai halaman untuk menemukan elemen dengan class `has-audio-player`. Jika elemen ini ditemukan, skrip akan menarik URL, Judul, dan Sub-judul untuk ditampilkan pada tombol pemutar melayang. Jika elemen ini tidak ada di artikel, tombol melayang akan disembunyikan agar blog tetap rapi.
