# rtmp

To get the master server started

```bash
boot2docker ssh

cd master
docker build -t rtmp .
docker run -d -p 1935:1935 --name rtmp rtmp
```

