#!/bin/bash

# ====================================================================
# SKRIP INSTALASI OTOMATIS CLIPPER VIDEO LOKAL (FFMPEG & YT-DLP 2026)
# ====================================================================

echo "=============================="
echo "⚙️ Memulai konfigurasi sistem"
echo "=============================="

# 1. Perbarui daftar paket repositori Ubuntu
echo "🔄 Memperbarui package list Ubuntu..."
```bash
sudo apt update -y
```

# 2. Instal FFmpeg (Alat pemotong video lokal)
echo "🎬 Menginstal FFmpeg..."
```bash
sudo apt install ffmpeg -y
```

# 3. Instal Python3-pip (Diperlukan untuk memasang yt-dlp versi terbaru)
echo "🐍 Menginstal Python3 PIP..."
```bash
sudo apt install python3-pip -y
```

# 4. Bersihkan sisa-sisa berkas yt-dlp jadul/rusak yang berpotensi bentrok
echo "🧹 Membersihkan sisa file yt-dlp lama yang rusak..."
```bash
sudo apt remove yt-dlp -y
sudo rm -f /usr/local/bin/yt-dlp
sudo rm -f /usr/bin/yt-dlp
```

# 5. Instal yt-dlp versi terbaru (2026) langsung dari PIP dengan bypass pengunci sistem
echo "🚀 Menginstal yt-dlp versi terbaru via PIP..."
```bash
sudo pip install --upgrade yt-dlp --break-system-packages
```

# 6. Segarkan memori jalur eksekusi terminal
```bash
hash -r
```

echo "==========================================="
echo "✅ KONFIGURASI SELESAI! Memeriksa versi alat:"
echo "==========================================="

# Menampilkan verifikasi hasil instalasi akhir
```bash
echo -n "FFmpeg Version: " && ffmpeg -version | head -n 1
echo -n "yt-dlp Version: " && yt-dlp --version
```

echo "========================="
echo "👑 Sistem siap digunakan!"
echo "========================="



# Panduan Clipping Video Lokal WSL (FFmpeg + yt-dlp)

### 1. Perintah Unduh Video Mentah (720p)
```bash
yt-dlp --cookies ~/cookies.txt -f "bestvideo[height<=720][ext=mp4]+bestaudio[ext=m4a]/best[height<=720][ext=mp4]" "LINK_YOUTUBE" -o "~/video_mentah_720p.mp4"
```

### 2. Perintah Potong Durasi (FFmpeg)
```bash
ffmpeg -ss 00:01:30 -to 00:05:00 -i ~/video_mentah_720p.mp4 -c copy ~/final_video_720p.mp4
```

### 3. Perintah Buka Folder Visual ke Windows
```bash
explorer.exe .
```
