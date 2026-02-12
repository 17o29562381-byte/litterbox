This is simple bash code to reduce the size of some media files.  No big deal.  They run okay on my old Dell Chromebook 3100 under the new format.
uses HandBrakeCLI, tar,  
recommended using on a seedbox to pack the files.

thanks
-roy
2-4-26
* 2-12-26 The Code...
  It is actually a nice little BASH script.  I am going to try to beef it up and it works will crunching down media to play on my old Dell Chromebook 3120.
  I am surprised it sometimes does 3 passes to re-encode the media file.  I translated the encoding commands from an old ffmpeg one.
  -> find -iregex ".*\.\(mp4\|wmv\|mov\flv\|mkv\rm\|m4v\|ts\|mpg\|mpeg\|avi\)" -exec ffmpeg -hide_banner -loglevel error -hwaccel auto -i {} -vf scale=-2:288 -g 52 -c:v libx264 -maxrate:v 1024k -bufsize 1024k -c:a libopus -maxrate:a 128k -ar 48000 -ac 2 -f mp4 -movflags faststart -map 0:v:0 -map 0:a:0 {}.avi \; -exec rm {} \; -exec tar zcvf {}.avi.tar.gz {}.avi \; -exec rm {}.avi \;
  I had to modify the original source to make it work. 

  
❓ - Find original source to reference

❓ - Do something with script to make it cooler.  Hand editing is fine.
