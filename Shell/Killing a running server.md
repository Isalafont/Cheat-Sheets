Here's what to do when you want to launch a server but you can't cause the error message tells you that a server is already running even if not. 
That's probably due to a PID who did not shut down properly. 
## Kill a running server

==This example use TCP port 3000 but the process will be the same for any tcp port.==

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