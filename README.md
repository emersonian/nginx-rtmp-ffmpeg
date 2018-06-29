# Nginx with RTMP and ffmpeg

I use this container to record live video streams and convert them from FLV to MP4 once the stream is complete.

```
application encoder {
	live on;
	record_path /mnt/records;
	record_suffix -%d-%b-%y-%H-%M-%S.flv;
	recorder rec1 {
		record all;
		record_unique on;
		# Convert recorded file to mp4 format
		exec_record_done ffmpeg -i $path -codec copy $dirname/$basename.mp4;
	}
}
```

