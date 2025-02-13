# Kids Channel

Streams local videos like a "tv channel".  Can be viewed in a web browser or on jellyfin.

## Components

### ffmpeg rtmp server

check out `rtmp_stream` file.

### Nginx with the rtmp module

`rtmp_stream` will stream contents to nginx, which will then serve contents via hls stream.

I ran nginx with the following options:
```
docker run --name nginx-rtmp \
  -p 1935:1935 -p 8080:8080 \
  -v ./nginx.conf:/etc/nginx/nginx.conf:ro \
  -v ./hls:/mnt/hls \
  tiangolo/nginx-rtmp
```

### stream.m3u

stream.m3u file is what jellyfin will use to play the stream.  It is a playlist file that points to the hls stream.

### important note

videos from youtube must be normalized to prevent playback errors and stuttering.  See `normalize_videos` for more information.
