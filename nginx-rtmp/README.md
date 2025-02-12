# Kids Channel

Streams local videos like a "tv channel".  Can be viewed in a web browser or on jellyfin.

## Components

### ffmpeg rtmp server

check out `rtmp_stream` file.

### Nginx with the rtmp module

`rtmp_stream` will stream contents to nginx, which will then serve contents via hls stream.

### stream.m3u

stream.m3u file is what jellyfin will use to play the stream.  It is a playlist file that points to the hls stream.
