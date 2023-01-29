FFmpeg Note
===========

ffmpeg -i input.avi output.mp4

ffmpeg -i input.avi -c:v libx264 output.mp4
ffmpeg -i input.avi -c:v h264_nvenc output.mp4

ffmpeg -i input.avi -c:v libx264 -preset slow output.mp4
ffmpeg -i input.avi -c:v libx264 -crf 20 output.mp4 # 0-51

ffmpeg -i sound.wav sound.mp3

```
ffmpeg -hide_banner -devices


# Linux camera
ffmpeg -f v4l2 -framerate 25 -s 640x480 -i /dev/video0 output.mkv

ffmpeg -f alsa -i hw:0 out.wav
```

```
ffmpeg -listen 1 -f flv -i rtmp://localhost:1935/live/app -c copy rtsp://YOUR_RTSP_HOST

ffmpeg -re -i /usr/VIDEO/my_video.mp4 -i /usr/VIDEO/x_audio.mp3 \
  -map 0:v -c:v libx264 -vf format=yuv420p -b:v 2000k -bufsize 3000k -maxrate 2000k -s 1024X576 -g 60 -map 0:a -c:a aac -b:a 192k -ar 44100 -f flv rtmp://my_ip/live/pass \
  -map 0:v -c:v libx264 -vf format=yuv420p -b:v 2000k -bufsize 3000k -maxrate 2000k -s 1024X576 -g 60 -map 1:a -streamloop -shortest -f flv rtmp://my_ip/noaudio/pass \
  -map 0:a aac -b:a 192k -ar 44100 -f flv rtmp://my_ip/only_audio/pass
```

``` bash
ffmpeg -i input.mp4 -vf "scale=1024:-1" output.mp4
ffmpeg -i input.mp4 -vf "scale=-1:720" output.mp4
ffmpeg -i input.mp4 -vf "transpose=2" output.mp4
ffmpeg -i input.mp4 -vf "crop=w/2:h/2:$x:$y" output.mp4

ffmpeg -i input.mp4 -ss 00:00:02 -t 5 output.mp4
ffmpeg -i input.mp4 -ss 00:00:02 -to 00:00:05 output.mp4
```


```bash
# join some video into one with a file list
cat > filelist.txt <<EOF
file 'file1.mp4'
file 'file2.mp4'
file 'file3.mp4'
EOF

ffmpeg -f concat -i filelist.txt -c copy output.mp4

ffmpeg -i input0.mp4 -i input1.mp4 -i input2.mp4 -filter_complex "[0:v] [0:a] [1:v] [1:a] [2:v] [2:a] concat=n=3:v=1:a=1 [v] [a]" -map "[v]" -map "[a]" output.mp4
  # concat   Indicates the concat filter name
  # n        Indicates the number of segments or input files
  # v        Indicates the number of output video streams
  # a        Indicates the number of output audio streams
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
# converter
ffmpeg -i input.webm output.mp4
ffmpeg -i input.flv -vcodec libx264 output.mp4
ffmpeg -i input.avi -c:v libx264 output.mp4
ffmpeg -i input.mkv -map 0:v -map 0:a:1 output.mp4
ffmpeg -i input.mov output.mp4

```


```bash
# add a mask or waterprint
ffmpeg -i input.mp4 -i logo.jpg -filter_complex "overlay=100:100" output.mp4
```

```bash
# replace the audio on a video
ffmpeg -i input.mp4 -i input.mp3 -c copy -map 0:v:0 -map 1:a:0 output.mp4
```

```bash
# convert a slice of mp4 to gif
ffmpeg -i input.mp4 -ss 0 -t 3 -filter_complex \
      [0:v]fps=15,scale=-1:256,split[a][b];[a]palettegen[p];[b][p]paletteuse \
      output.gif
```


```bash
# filter_complex
# filter syntax:
#   filter_name=arg1=value1:arg2=value2
#   filter_name=arg1:arg2
#   [0:v]filter0_name=arg1:arg2;[1:v]filter1_name=arg1=value1:arg2=value2;

ffmpeg -i input.mp4 -i logo.jpg -filter_complex "overlay=100:100" output.mp4
ffmpeg -i input.mp4 -filter_complex \
      "[0:v]fps=15,scale=-1:256,split[a][b];[a]palettegen[p];[b][p]paletteuse" \
      output.gif

ffmpeg -f avfoundation -r 30 -s 1280x720 -i "1:1" -vf "hue=H=2*PI*t:s=cos(2*PI*t)+10" output.mkv
ffmpeg -i input.mp4 -vf "vignette=angle=PI/6" output.mp4
  # vignette   Indicates the vignette filter name
  # angle, a   Indicates the angle in radians (PI/2 to 0 with default PI/5)
  # x0, y0     Indicates the center coordinates
  # mode       Indicates the forward or backward mode (forward or backward)

ffmpeg -i input.mp4 -vf "colorhold=color=00FFFF:similarity=1" -pix_fmt yuv420p output.mp4
  # colorhold  Indicates the colorhold filter name
  # color      Indicates the color which isn’t replaced with the color gray
  # similarity Indicates the similar color percentage based on color. The larger the number the larger the similarity (1.0 to 0.1 default 0)
  # blend      Indicates the blend percent of gray (1.0 to 0.0 default 0.0)

ffmpeg -i input.mp4 -vf "rgbashift=rh=-10" -pix_fmt yuv420p output.mp4
ffmpeg -i input.mp4 -vf "rgbashift=bh=10" -pix_fmt yuv420p output.mp4
ffmpeg -i input.mp4 -vf "rgbashift=gv=10" -pix_fmt yuv420p output.mp4

ffmpeg -i input.mp4 -vf "negate" output.mp4

ffmpeg -i input.mp4 -vf "crop=885:1165:0:280" output.mp4

ffmpeg -i input.mp4 -filter_complex "vibrance=intensity=-2:gbal=10" -pix_fmt yuv420p output.mp4
  # intensity  Indicates the strength of the SATURATION boost. Positive value boosts while negative value alters (2 to -2 with default 0)
  # rbal       Indicates the red balance (10 to -10 with default 1)
  # gbal       Indicates the green balance (10 to -10 with default 1)
  # bbal       Indicates the blue balance (10 to -10 with default 1)
  # rlum       Indicates the red luma coefficient (1 to 0 default 0)
  # glum       Indicates the green luma coefficient (1 to 0 default 0)
  # blum       Indicates the blue luma coefficient (1 to 0 default 0)

ffmpeg -i input.mp4 -vf "hue=H=2*PI*t:s=cos(2*PI*t)+10" output.mp4
  # hue        Indicates the hue filter name
  # h          Indicates the hue angle as a number of degrees (default 0)
  # s          Indicates the saturation (10 to -10 with default 1)
  # H          Indicates hue angle as a number of radians (default 0)
  # b          Indicates the brightness (10 to -10 with default 0)
  # n          Indicates frame count of the input frame (starts at 0)
  # t          Indicates the timestamp (HH:MM:SS)

ffmpeg -i input.mp4 -vf "colorbalance=gs=.5:bh=1" -pix_fmt yuv420p output.mp4
  # colorbalance  Indicates the color balance filter name
  # rs, gs, bs    Indicates adjustments to red, green and blue shadows or darkest pixels (1.0 to -1.0 with default 0.0)
  # rm, gm, bm    Indicates adjustments to red, green and blue midtones or medium pixels (1.0 to -1.0 with default 0.0)
  # rh, gh, bh    Indicates adjustments to red, green and blue highlights or brightest pixels (1.0 to -1.0 with default 0.0)
  # pl            Indicates preserve lightness when changing color balance (1.0 to -1.0 with default 0.0)

ffmpeg -i input.mp4 -vf "normalize=strength=1" output.mp4
  # normalize     Indicates the normalization filter name
  # strength      Indicates the strength of the normalization, large the value higher the strength (1.0 to 0.0 with default 1.0)
  # smoothing     Indicates setting a temporal smoothing based on the previous frame (1 or 0 with a default 0 - no smoothing)

ffmpeg -i input1.mp4 -i input2.mp4 -filter_complex "blend=difference" output.mp4
  # blend mode could be one of the following choices:
  #    addition grainmerge and average burn darken difference
  #    grainextract divide dodge freeze exclusion extremity glow
  #    hardlight hardmix heat lighten linearlight multiply
  #    multiply128 negation normal or overlay phoenix pinlight
  #    reflect screen softlight subtract vividlight xor

ffmpeg -loop 1 -i input.png -I -c:v libx264 -pix_fmt yuv420p output.mp4
ffmpeg -i input.mp4 -i greenscreen.mp4 -filter_complex '[1:v]colorkey=color=00FF00:similarity=0.85:blend=0.0[ckout];[0:v][ckout]overlay[out]' -map '[out]' output.mp4
```

```bash
# convert between video and image sequence

ffmpeg -framerate 10 -i picture-%03d.jpg output.mp4

ffmpeg -i input.mp4 picture-%03d.jpg

ffmpeg -i RPReplay.MP4 -vf "crop=885:1165:0:280" imgs/picture-%04d.png
```


```bash
xdpyinfo | grep 'dimensions:'
# capture the screen to video
## on windows
ffmpeg -hide_banner -loglevel error -stats -f gdigrab -framerate 30 -video_size 1920_1080 \
      -offset_x 0 -offset_y 0 -draw_mouse 1 -i desktop -c:v libx264 -r 60 -preset ultrafast \
      -pix_fmt yuv420o -y screen_record.mp4

## on ubuntu
ffmpeg -hide_banner -loglevel error -stats -f x11grab -framerate 30  -video_size 1920x1080 \
       -draw_mouse 1 -i :0.0+0,0 -c:v libx264 -r 60 -crf 0 -preset ultrafast \
       -y screen_record.mkv

# -i :0.0+x,y   set display 0.0 and offsets x, y


## on Mac OS
ffmpeg -f avfoundation -list_devices true -i ""
ffmpeg -f avfoundation -i "<screen device index>:<audio device index>" output.mkv
ffmpeg -f avfoundation -r 30 -s 1280x720 -i "1:1"  output.mkv
ffmpeg -f avfoundation -r 30 -s 1280x720 -i "1:1" -vf "hue=H=2*PI*t:s=cos(2*PI*t)+10" output.mkv
```
