# YouTube Video & Playlist Downloader

This repository provides a collection of **yt-dlp** commands and useful scripts for downloading YouTube videos and playlists efficiently. It also includes aliases for quick usage and a script to add index numbers to videos downloaded without them.

## Features
- Download YouTube videos with different quality options
- Download entire playlists with custom start and end points
- Save videos with specific formats and metadata
- Extract audio-only formats
- Use custom output templates for better organization
- Support for subtitles, cookies, and indexing

---

## 📥 Downloading Videos & Playlists

### 🎥 Download a Single Video with Audio
```sh
yt-dlp -f 251 https://youtu.be/n86cMw_SyWU -o - | mpv - --volume=50 --loop=3
```

### 📺 Download Video in 480p Quality with Best Audio
```sh
yt-dlp -f "bestvideo[height<=480]+bestaudio/best" https://youtu.be/n86cMw_SyWU -o - | mpv - --volume=50 --loop=3
```

### 🔁 Loop Video Playback via mpv
```sh
mpv --ytdl-format=139 --cache=yes --cache-secs=10 https://youtu.be/sPa9ZDyWwEI --loop
```

### 🎞️ Download Video with Chapters
```sh
yt-dlp -f "bv[height<=720]+ba" --add-chapters
```

### 📂 Download Playlist with Custom Range
```sh
yt-dlp -f "bv[height<=720]+ba" --add-chapters --playlist-start 4 --playlist-end 10 <yt_url>
```

### 📌 Download Playlist with Custom Naming
```sh
yt-dlp --playlist-start 8 -o "#%(playlist_index)s - %(title)s.%(ext)s" <playlist_url>
```

### 🏷️ Download with Custom Directory & Naming Format
```sh
yt-dlp -f 18 -o './Desktop/%(title)s.%(ext)s' https://youtu.be/rQqGdeZtY4Y
```
```sh
yt-dlp -f 18 -o './Desktop/%(title)s by %(uploader)s on %(upload_date)s in %(playlist)s.%(ext)s' https://youtu.be/rQqGdeZtY4Y
```

### 📝 Save Playlist Index + Title + ID
```sh
yt-dlp --skip-download --print-to-file "%(playlist_index)s %(title)s %(id)s" playlist_order.txt "https://youtube.com/playlist?list=PLinedj3B30sDP2CHN5P0lDD64yYZ0Nn4J"
```

---

## 🚀 Aliases for Quick Commands

### 🎵 Audio-Only Downloads
```sh
alias yt0="yt-dlp -c -f ba --add-chapters"
```

### 🎞️ Different Video Resolutions
```sh
alias yt1="yt-dlp -c -f 'bv[height<=144]+ba' --add-chapters"
alias yt2="yt-dlp -c -f 'bv[height<=240]+ba' --add-chapters"
alias yt3="yt-dlp -c -f 'bv[height<=360]+ba' --add-chapters"
alias yt4="yt-dlp -c -f 'bv[height<=480]+ba' --add-chapters"
alias yt7="yt-dlp -c -f 'bv[height<=720]+ba' --add-chapters"
alias yt10="yt-dlp -c -f 'bv[height<=1080]+ba' --add-chapters"
```

### 📜 Playlist Downloads with Index Numbers
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

## 🛠️ Add Playlist Index to Video Names

If you downloaded a playlist **without** index numbers, you can use the following script to rename them by adding their index at the beginning of the file names.

### 📜 Bash Script: Add Index to Playlist Video Names
```bash
#!/bin/bash

# Path to the playlist_order.txt file
ORDER_FILE="../yt/playlist_order.txt"

# Read each line from playlist_order.txt
while IFS= read -r line; do
    # Extract index, title, and ID using awk
    index=$(echo "$line" | awk '{print $1}')
    id=$(echo "$line" | awk '{print $NF}')
    
    # Find the matching video file
    for file in *"[${id}].webm"; do
        if [[ -f "$file" ]]; then
            # Generate new filename with index prefix
            new_name="${index} ${file}"
            
            # Rename the file
            mv "$file" "$new_name"
            echo "Renamed: $file -> $new_name"
        fi
    done
done < "$ORDER_FILE"
```

📌 **Usage:**
1. Save the script as `rename_playlist.sh`
2. Make it executable: `chmod +x rename_playlist.sh`
3. Run it inside the folder containing your downloaded videos: `./rename_playlist.sh`

---

## 🌟 Future Plans
🔹 I plan to develop a **GUI-based software** that will internally use these yt-dlp commands for easier video downloading. Stay tuned! 🚀

---

### 💡 Contributions & Support
Feel free to contribute or suggest improvements via **Pull Requests** or **Issues**!

📩 **Contact:** Lavkush Singh

