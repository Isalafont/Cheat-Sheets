### Kill a running server

tcp:3000 is port 3000

```shell
lsof -wni tcp:3000
```

```
COMMAND  PID  USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
    ruby    3366 dummy    8u  IPv4  16901      0t0  TCP 127.0.0.1:3000 (LISTEN)
```

then kill the PID
```shell
kill -9 #PID