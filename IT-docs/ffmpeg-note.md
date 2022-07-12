FFmpeg Note
===========

ffmpeg -i input.avi output.mp4

ffmpeg -i input.avi -c:v libx264 output.mp4
ffmpeg -i input.avi -c:v h264_nvenc output.mp4

ffmpeg -i input.avi -c:v libx264 -preset slow output.mp4
ffmpeg -i input.avi -c:v libx264 -crf 20 output.mp4 # 0-51

ffmpeg -i sound.wav sound.mp3


ffmpeg -i input.mp4 -vf "scale=1024:-1" output.mp4
ffmpeg -i input.mp4 -vf "scale=-1:720" output.mp4
ffmpeg -i input.mp4 -vf "transpose=2" output.mp4
ffmpeg -i input.mp4 -vf "crop=w/2:h/2:$x:$y" output.mp4

ffmpeg -i input.mp4 -ss 00:00:02 -t 5 output.mp4
ffmpeg -i input.mp4 -ss 00:00:02 -to 00:00:05 output.mp4


```bash
# join some video into one with a file list
cat > filelist.txt <<EOF
file 'file1.mp4'
file 'file2.mp4'
file 'file3.mp4'
EOF

ffmpeg -f concat -i filelist.txt -c copy output.mp4
```

ffmpeg -i input.mp4 -vf "fps=1/10,scale=-2:720" thumbnail-%03d.jpg
ffmpeg -i input.mp4 -an output.mp4

-an  remove audio
-vn  remove video
-sn  remove lyric
-dn  remote data

```bash
# some audio filter examples
ffmpeg -i sound.wav -af "volume=1.5" sound.mp3
ffmpeg -i input.mp4 -af "loudnorm=I=-5:LRA=1" output.mp4
ffmpeg -i input.mp4 -af "equalizer=f=1000:width_type=h:width=200:g=-10" output.mp4
```


```bash
ffmpeg -i input.mp4 -i logo.jpg -filter_complex "overlay=100:100" output.mp4
```

```bash
ffmpeg -i input.mp4 -i input.mp3 -c copy -map 0:v:0 -map 1:a:0 output.mp4
```

```bash
# convert a slice of mp4 to gif
ffmpeg -i input.mp4 -ss 0 -t 3 -filter_complex \
      [0:v]fps=15,scale=-1:256,split[a][b];[a]palettegen[p];[b][p]paletteuse \
      output.gif
```


```bash

ffmpeg -framerate 10 -i picture-%03d.jpg output.mp4

ffmpeg -i input.mp4 picture-%03d.jpg
```


```bash
# capture the screen to video
ffmpeg -hide_banner -loglevel error -stats -f gdigrab -framerate 60 -offset_x 0 -offset_y 0 \
      -video_size 1920_1080 -draw_mouse 1 -i desktop -c:v libx264 -r 60 -preset ultrafast \
      -pix_fmt yuv420o -y screen_record.mp4
```
