#youtube #youtube-dl #dl

### Скачать `m4a`-аудиодорожку:
```bash
youtube-dl -f m4a -o "%(upload_date)s-%(title)s.%(ext)s" <paste link or -a file here>

```

### Скачать `m4a`-аудиодорожку и конвертировать в `mp3`
```bash
youtube-dl -f m4a -o "%(upload_date)s-%(title)s.%(ext)s" -x --audio-format mp3 <paste link or -a file here>


youtube-dl -f m4a -o "%(upload_date)s-%(title)s.%(ext)s" --ffmpeg-location "C:\Program Files\ffmpeg-20191016-29dac29-win64-static\bin\ffmpeg.exe" -x --audio-format mp3 <paste link or -a file here>
```

### Скачать видео и субтитры
```bash
youtube-dl --write-sub --sub-lang en <paste link or -a file here>
```