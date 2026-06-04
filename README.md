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
