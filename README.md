# 👑 Dokumentasi & Skrip Clipper Video Lokal Anjay Kelas King

Repositori ini berisi skrip otomatisasi Bash dan dokumentasi perintah teroptimasi untuk mengunduh serta memotong (clipping) video YouTube secara lokal di lingkungan WSL/Ubuntu. Memanfaatkan kombinasi yt-dlp (Versi 2026 Terbaru) untuk menembus proteksi enkripsi YouTube dan FFmpeg untuk pemotongan instan tanpa kompresi ulang (lossless). 100% Gratis, aman, dan berjalan sepenuhnya di komputer Anda tanpa memerlukan API Key pihak ketiga.

Fitur Utama Repositori Ini:

➤ Anti-Blokir YouTube 2026: Menggunakan integrasi file cookies manual dan instalasi pip terbaru untuk menghindari error 403 Forbidden.

➤ Kualitas HD Terkunci: Formula perintah khusus untuk mengunduh video siaran langsung (Live) tepat di resolusi 720p MP4.

➤ Lossless Clipping: Proses pemotongan durasi video menggunakan FFmpeg hanya memakan waktu 1-2 detik tanpa merusak kualitas visual asli.

➤ Integrasi Windows-WSL: Akses file hasil render secara instan menggunakan perintah visual langsung ke File Explorer Windows.

Berikut adalah skrip instalasi otomatis dan daftar perintah pengeditan video gratis secara lokal menggunakan **FFmpeg** dan **yt-dlp** di WSL.

---

## 🛠️ 1. Skrip Instalasi Otomatis (`install_tools.sh`)

Salin seluruh kode di bawah ini, simpan menjadi file bernama `install_tools.sh` di folder Linux Anda, lalu jalankan untuk memasang semua alat secara otomatis:

```bash
#!/bin/bash

# ====================================================================
# SKRIP INSTALASI OTOMATIS CLIPPER VIDEO LOKAL (FFMPEG & YT-DLP 2026)
# ====================================================================

clear
echo "==========================================="
echo "⚙️ Memulai konfigurasi sistem Kelas King..."
echo "==========================================="

# 1. Perbarui daftar paket repositori Ubuntu
echo "🔄 Memperbarui package list Ubuntu..."
sudo apt update -y

# 2. Instal FFmpeg (Alat pemotong video lokal)
echo "🎬 Menginstal FFmpeg..."
sudo apt install ffmpeg -y

# 3. Instal Python3-pip (Diperlukan untuk memasang yt-dlp versi terbaru)
echo "🐍 Menginstal Python3 PIP..."
sudo apt install python3-pip -y

# 4. Bersihkan sisa-sisa berkas yt-dlp jadul/rusak yang berpotensi bentrok
echo "🧹 Membersihkan sisa file yt-dlp lama yang rusak..."
sudo apt remove yt-dlp -y
sudo rm -f /usr/local/bin/yt-dlp
sudo rm -f /usr/bin/yt-dlp

# 5. Instal yt-dlp versi terbaru (2026) langsung dari PIP dengan bypass pengunci sistem
echo "🚀 Menginstal yt-dlp versi terbaru via PIP..."
sudo pip install --upgrade yt-dlp --break-system-packages

# 6. Segarkan memori jalur eksekusi terminal
hash -r

echo "==========================================="
echo "✅ KONFIGURASI SELESAI! Memeriksa versi alat:"
echo "==========================================="

# Menampilkan verifikasi hasil instalasi akhir
echo -n "FFmpeg Version: " && ffmpeg -version | head -n 1
echo -n "yt-dlp Version: " && yt-dlp --version

echo "==========================================="
echo "👑 Sistem siap digunakan untuk mengklip video!"
echo "==========================================="
```

---

## 📥 2. Perintah Unduh Video Mentah (Format 720p HD)

Gunakan perintah ini di terminal untuk mengunduh video siaran langsung (Live) atau video panjang secara utuh menggunakan file kuki:

```bash
yt-dlp --cookies ~/cookies.txt -f "bestvideo[height<=720][ext=mp4]+bestaudio[ext=m4a]/best[height<=720][ext=mp4]" "LINK_YOUTUBE" -o "~/video_mentah_720p.mp4"
```

---

## ✂️ 3. Perintah Potong Durasi Video (FFmpeg Instan)

Gunakan perintah ini untuk memotong rentang waktu menit spesifik secara lokal tanpa mengunduh ulang:

```bash
ffmpeg -ss 00:01:30 -to 00:05:00 -i ~/video_mentah_720p.mp4 -c copy ~/final_video_720p.mp4
```

---

## 📂 4. Perintah Buka Folder Visual ke Windows

Gunakan perintah ini untuk memunculkan folder Linux Anda langsung ke dalam File Explorer Windows:

```bash
explorer.exe .
```

