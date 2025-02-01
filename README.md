# 📥 YouTube Download & Playback Commands using yt-dlp

This repository contains various **yt-dlp** commands for downloading and playing YouTube videos and playlists efficiently. These commands include different formats, resolutions, subtitle handling, cookies, and playlist indexing.

## 📌 Table of Contents
- [Basic Commands](#basic-commands)
- [Downloading Playlists](#downloading-playlists)
- [Extracting Playlist Metadata](#extracting-playlist-metadata)
- [Downloading with Custom Names](#downloading-with-custom-names)
- [Aliases for Quick Downloads](#aliases-for-quick-downloads)

---
## 🎬 Basic Commands

### Play a YouTube video with `mpv` at 50% volume, looping 3 times:
```sh
yt-dlp -f 251 https://youtu.be/n86cMw_SyWU -o - | mpv - --volume=50 --loop=3
```

### Play video at 480p or best available format:
```sh
yt-dlp -f "bestvideo[height<=480]+bestaudio/best" https://youtu.be/n86cMw_SyWU -o - | mpv - --volume=50 --loop=3
```

### Enable chapter markers in downloaded videos:
```sh
yt-dlp --add-chapters
```

### Play YouTube video with cache enabled:
```sh
mpv --ytdl-format=139 --cache=yes --cache-secs=10 https://youtu.be/sPa9ZDyWwEI --loop
```

### Download a video in 480p:
```sh
yt-dlp -f "bestvideo[height<=480]+bestaudio/best" https://youtu.be/w3dvdG6sVCM
```

---
## 📜 Downloading Playlists

### Download a specific range of videos from a playlist (e.g., videos 4 to 10):
```sh
yt-dlp -f "bv[height<=720]+ba" --add-chapters --playlist-start 4 --playlist-end 10 <playlist_url>
```

### Download playlist in MP4 format:
```sh
yt-dlp -f "bestvideo[ext=mp4]+bestaudio[ext=m4a]/best[ext=mp4]/best" "PLAYLIST_URL"
```

### Download subtitles along with videos:
```sh
yt-dlp --write-subs --sub-langs en "PLAYLIST_URL"
```

### Download videos using cookies (for private playlists or accounts):
```sh
yt-dlp --cookies cookies.txt "PLAYLIST_URL"
```

### Download only first 10 videos of a playlist:
```sh
yt-dlp --playlist-items 1-10 "PLAYLIST_URL"
```

---
## 📊 Extracting Playlist Metadata

### Extract index number, title, and ID of videos in a playlist:
```sh
yt-dlp --skip-download --print-to-file "%(playlist_index)s %(title)s %(id)s" playlist_order.txt "https://youtube.com/playlist?list=PLinedj3B30sDP2CHN5P0lDD64yYZ0Nn4J"
```

---
## 📁 Downloading with Custom Names

### Save videos with a custom directory and naming format:
```sh
yt-dlp -f 18 -o './Desktop/%(title)s.%(ext)s' https://youtu.be/rQqGdeZtY4Y
```

### Save videos with additional metadata in the filename:
```sh
yt-dlp -f 18 -o './Desktop/%(title)s by %(uploader)s on %(upload_date)s in %(playlist)s.%(ext)s' https://youtu.be/rQqGdeZtY4Y
```

---
## 🚀 Aliases for Quick Downloads

### Set up convenient aliases for different video qualities:
```sh
alias yt0="yt-dlp -c -f ba --add-chapters"
alias yt1="yt-dlp -c -f 'bv[height<=144]+ba' --add-chapters"
alias yt2="yt-dlp -c -f 'bv[height<=240]+ba' --add-chapters"
alias yt3="yt-dlp -c -f 'bv[height<=360]+ba' --add-chapters"
alias yt4="yt-dlp -c -f 'bv[height<=480]+ba' --add-chapters"
alias yt7="yt-dlp -c -f 'bv[height<=720]+ba' --add-chapters"
alias yt10="yt-dlp -c -f 'bv[height<=1080]+ba' --add-chapters"
```

### Aliases for downloading playlists with index numbering:
```sh
alias yt0p="yt-dlp -c -f ba --add-chapters -o \"#%(playlist_index)s - %(title)s.%(ext)s\""
alias yt1p="yt-dlp -c -f 'bv[height<=144]+ba' --add-chapters -o \"#%(playlist_index)s - %(title)s.%(ext)s\""
alias yt2p="yt-dlp -c -f 'bv[height<=240]+ba' --add-chapters -o \"#%(playlist_index)s - %(title)s.%(ext)s\""
alias yt3p="yt-dlp -c -f 'bv[height<=360]+ba' --add-chapters -o \"#%(playlist_index)s - %(title)s.%(ext)s\""
alias yt4p="yt-dlp -c -f 'bv[height<=480]+ba' --add-chapters -o \"#%(playlist_index)s - %(title)s.%(ext)s\""
alias yt7p="yt-dlp -c -f 'bv[height<=720]+ba' --add-chapters -o \"#%(playlist_index)s - %(title)s.%(ext)s\""
alias yt10p="yt-dlp -c -f 'bv[height<=1080]+ba' --add-chapters -o \"#%(playlist_index)s - %(title)s.%(ext)s\""
```

---




📌 **Want to contribute?** Feel free to fork and improve this documentation! 🚀

