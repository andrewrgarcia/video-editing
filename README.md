# video-editing

````ruby
#to cut video
ffmpeg -i input.mp4 -ss 00:00:01 -t 00:10:00 -async 1 out.mp4

#to make video faster
ffmpeg -i input.mp4 -filter_complex "[0:v]setpts=0.5*PTS[v];[0:a]atempo=2[a]" -map "[v]" -map "[a]" -c:v libx264 -c:a aac out.mp4

#to crop video (size wise)
ffmpeg -i input.mp4 -filter:v "crop=1280:720:10:10" out.mp4

ffmpeg -i input.mp4 -vf scale=1200:1000,setsar=1:1 out.mp4

#to compress video
ffmpeg -i input.mp4 -vcodec libx265 -crf 28 out.mp4

ffmpeg -i input.mp4 -vf "scale=iw/2:ih/2" -c:v libx265 -crf 28 half_the_frame_size.mp4

#mov to mp4
ffmpeg -i input.mov -vcodec h264 -acodec mp2 input.mp4

#mp4 to gif
ffmpeg -i input.mp4 output.gif

