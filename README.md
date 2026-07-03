<div align="center">

# 📷 Gesture Blur Cam

**Kamera berbasis gestur tangan yang memicu efek blur secara live — terinspirasi tren TikTok dengan lagu "Foto Kita Blur" oleh Sal Priadi.**

Angkat kedua tangan, bentuk isyarat ✌️ angka 2, dan kamera otomatis blur. Tekan shutter, audio dan video terekam bersamaan — tanpa delay, tanpa editor tambahan.

**🔗 Coba langsung:** [foto-kita-blur-delta.vercel.app](https://foto-kita-blur-delta.vercel.app/)

[![Made with HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)](#)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)](#)
[![MediaPipe Hands](https://img.shields.io/badge/MediaPipe-Hands-4285F4?style=flat&logo=google&logoColor=white)](#)
[![License](https://img.shields.io/badge/license-MIT-8CA084?style=flat)](#lisensi)
[![Live Demo](https://img.shields.io/badge/Live%20Demo-vercel.app-black?style=flat&logo=vercel&logoColor=white)](https://foto-kita-blur-delta.vercel.app/)

</div>

---

## 📖 Tentang Project

**Gesture Blur Cam** adalah web app satu-file yang mereplikasi sebuah tren TikTok: efek blur kamera yang hanya aktif saat kedua tangan membentuk isyarat **angka 2** (jari telunjuk + tengah terangkat) secara bersamaan. Project ini menggabungkan:

- **Deteksi gestur tangan real-time** langsung di browser (tanpa server, tanpa upload data ke mana pun)
- **Efek blur dinamis** yang menyala/mati secara halus mengikuti gestur
- **Audio dengan timing terkunci** — trek diputar otomatis dari detik tertentu sampai detik tertentu, tidak bisa diubah dari tampilan pengunjung
- **Perekaman video + audio menyatu** — hasil akhir langsung berupa satu file `.webm` yang siap diunduh dan dibagikan

Dibangun sebagai **HTML tunggal**, tanpa framework, tanpa proses build — cukup buka di browser atau deploy ke hosting statis mana pun.

---

## ✨ Fitur Utama

| Fitur | Deskripsi |
|---|---|
| 🖐️ **Deteksi gestur dua tangan** | Menggunakan [MediaPipe Hands](https://developers.google.com/mediapipe) untuk melacak 21 titik landmark per tangan secara real-time |
| 🌫️ **Blur otomatis & halus** | Efek blur menyala hanya saat kedua tangan membentuk isyarat angka 2 secara bersamaan, dengan transisi smooth |
| 🎵 **Timing audio terkunci** | Pemilik halaman mengatur detik mulai & selesai di kode — pengunjung tidak bisa mengedit dari UI |
| ⏺️ **Rekam tanpa delay** | Audio & video mulai terekam serentak begitu tombol shutter ditekan, langsung menyatu di satu file |
| 📱 **Siap pakai di Android/mobile** | Sticky action bar, target sentuh besar, dukungan safe-area, haptic feedback ringan |
| 🎨 **Desain kohesif** | Tema visual kamera analog/darkroom — bukan template generik |
| 🔗 **Tombol sosial terintegrasi** | Instagram & GitHub pemilik project tampil sebagai tombol di footer halaman |
| 🔒 **Privasi penuh** | Semua pemrosesan (kamera, deteksi tangan, rekaman) berjalan 100% di browser pengguna, tidak ada data yang dikirim ke server mana pun |

---

## 📱 Cara Menggunakan

1. **Aktifkan izin** untuk mengakses kamera pada browser yang digunakan.
2. **Lakukan postur tangan angka 2** pada kedua tangan (jari telunjuk + tengah terangkat) untuk memastikan efek blur aktif.
3. **Klik Record** jika ingin memulai tren tersebut — audio & video akan mulai terekam bersamaan.
4. **Download hasil record** tersebut untuk memastikan hasilnya, lalu bagikan ke media sosial favoritmu.

---

## 🚀 Live Demo

<div align="center">

### 👉 [foto-kita-blur-delta.vercel.app](https://foto-kita-blur-delta.vercel.app/)

</div>

---

## 🛠️ Instalasi & Menjalankan Secara Lokal

### Prasyarat
- Browser modern (Chrome, Edge, atau Firefox terbaru) dengan akses kamera & mikrofon
- Koneksi internet (untuk memuat library MediaPipe dari CDN saat pertama kali dibuka)
- File audio yang **legal untuk kamu distribusikan** (rekaman sendiri, lisensi resmi, atau royalty-free)

### Langkah-langkah

```bash
# 1. Clone repository ini
git clone https://github.com/username-kamu/gesture-blur-cam.git
cd gesture-blur-cam

# 2. Taruh file audio kamu di folder audio/, beri nama persis "track.mp3"
#    (folder ini perlu kamu buat sendiri jika belum ada)
mkdir -p audio
cp /path/ke/audio-kamu.mp3 audio/track.mp3

# 3. Jalankan lewat server lokal (WAJIB — jangan dobel-klik file HTML langsung,
#    karena browser membatasi akses kamera & file lokal dari protokol file://)
python3 -m http.server 8000
# atau kalau punya Node.js:
npx serve .

# 4. Buka di browser
# http://localhost:8000
```

### Kunci Timing Audio

Timing diatur langsung di dalam kode (`index.html`), dalam blok `<script>`:

```js
const LOCKED_AUDIO_SRC = 'audio/track.mp3';
const LOCKED_START = 38.5;   // detik mulai
const LOCKED_END   = 53;     // detik selesai
```

Ubah dua nilai ini sesuai bagian lagu yang kamu inginkan. Nilai ini **tidak muncul sebagai kolom yang bisa diedit** di tampilan pengunjung — hanya pemilik project yang bisa mengubahnya lewat kode.

---

## 📂 Struktur Project

```
gesture-blur-cam/
├── index.html          # Seluruh aplikasi (HTML + CSS + JS) dalam satu file
└── audio/
    └── track.mp3        # Audio milikmu — TIDAK disertakan di repo ini (lihat Lisensi & Hak Cipta)
```

---

## ☁️ Deploy ke Hosting

Project ini adalah situs statis murni — bisa langsung di-deploy tanpa proses build ke:

- **Vercel** — drag & drop folder project ke [vercel.com/new](https://vercel.com/new), atau `vercel --prod` lewat CLI
- **Netlify** — drag & drop folder ke [app.netlify.com/drop](https://app.netlify.com/drop)
- **GitHub Pages** — aktifkan di `Settings → Pages`, pilih branch `main` dan folder root

> ⚠️ Pastikan nama file utama persis **`index.html`** dan folder `audio/` ikut ter-upload sejajar dengannya, atau situs akan menampilkan error `404 NOT_FOUND`.

---

## 🧠 Cara Kerja Deteksi Gestur

1. Kamera menangkap video secara live lewat `getUserMedia()`
2. Setiap frame dikirim ke model **MediaPipe Hands**, yang mengembalikan 21 titik koordinat per tangan
3. Sistem mengecek posisi jari telunjuk & tengah (terentang) serta jari manis & kelingking (terlipat) untuk mengenali isyarat "angka 2"
4. Jika **kedua tangan** menunjukkan isyarat ini secara bersamaan, filter blur pada `<canvas>` dinaikkan secara bertahap (bukan on/off mendadak) untuk transisi yang halus
5. Saat tombol shutter ditekan, stream video dari `<canvas>` digabung dengan audio lewat `AudioContext` + `MediaRecorder`, menghasilkan satu file `.webm`

---

## ⚖️ Lisensi & Hak Cipta

- **Kode** pada repository ini bebas digunakan, dimodifikasi, dan didistribusikan di bawah [Lisensi MIT](#).
- **Audio tidak disertakan** dalam repository ini. Lagu *"Foto Kita Blur"* oleh **Sal Priadi** (album *Markers and Such Pens Flashdisks*) adalah karya berhak cipta — pengguna project ini bertanggung jawab penuh untuk hanya memakai audio yang memang legal untuk didistribusikan (rekaman/cover milik sendiri, lisensi resmi, atau musik royalty-free).
- Project ini dibuat sebagai **replika independen dari sebuah tren kreatif** di TikTok, bukan produk resmi/afiliasi dari Sal Priadi maupun TikTok.

---

## 🙏 Kredit

- Terinspirasi dari tren kreator TikTok yang menggunakan lagu **["Foto Kita Blur" — Sal Priadi](https://open.spotify.com)**
- Deteksi tangan menggunakan [MediaPipe Hands](https://developers.google.com/mediapipe/solutions/vision/hand_landmarker) oleh Google
- Tipografi: [Fraunces](https://fonts.google.com/specimen/Fraunces), [Instrument Sans](https://fonts.google.com/specimen/Instrument+Sans), [IBM Plex Mono](https://fonts.google.com/specimen/IBM+Plex+Mono)

---

## 🔗 Terhubung dengan Saya

<p>
  <a href="https://www.instagram.com/m_hbib03">
    <img src="https://img.shields.io/badge/Instagram-@m__hbib03-E4405F?style=for-the-badge&logo=instagram&logoColor=white" alt="Instagram">
  </a>
  <a href="https://github.com/mh1803031-ai">
    <img src="https://img.shields.io/badge/GitHub-Follow-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub">
  </a>
</p>


---

<div align="center">

Dibuat dengan 🎞️ untuk komunitas kreator Indonesia.

</div>
