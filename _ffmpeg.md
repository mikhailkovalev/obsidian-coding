#ffmpeg 
### Popular Ffmpeg Programming Tips
https://coderwall.com/t/ffmpeg/popular

### `flac` to `mp3`
```bash
ffmpeg -i input.flac -ab 320k -map_metadata 0 -id3v2_version 3 output.mp3
```

Все файлы в папке:
```bash
find . -name "*.flac" -exec ffmpeg -i {} -ab 320k -map_metadata 0 -id3v2_version 3 mp3/{}.mp3 \;
```

### `m4a` to `mp3`
```bash
ffmpeg -i foo.m4a -acodec libmp3lame -aq 2 bar.mp3
```

### Extract audio from video
```bash
ffmpeg -i <path-to-video> -map 0:2 -ss <start second> -to <last second> -f mp3 -ab 192000 -vn <destination-path> -y
```

### Compress `mkv`
```bash
ffmpeg -i "input.mkv" -vf "scale=trunc(3*iw/8)*2:trunc(3*ih/8)*2" -c:v libx265 -crf 28 "output.mkv"
```

### Add audio to video
[Source](https://stackoverflow.com/a/11783474)
```bash
ffmpeg -i video.mkv -i audio.mp3 -map 0 -map 1:a -c:v copy -shortest output.mkv
```

```bash
ffmpeg -ss hh:mm:ss -i original_video.mp4 -c copy -t 00:00:04 cut_1_test.mp4
```

### Cut video
```bash
ffmpeg -ss 00:01:30 -to 00:02:15 -i /path/to/input-video -c copy /path/to/output-video
```

### Compress video
```bash
ffmpeg -i input.mp4 -vcodec libx265 -crf 28 output.mp4
```