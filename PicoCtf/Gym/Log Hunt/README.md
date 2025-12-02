**General Skills**
```

Our server seems to be leaking pieces of a secret flag in its logs. The parts are scattered and sometimes repeated. Can you reconstruct the original flag? Download the logs and figure out the full flag from the fragments.

```
[logs](server.log)

---
# Solve

#### S 1
> cat server.log

```

[1990-08-09 10:00:10] INFO FLAGPART: picoCTF{us3_
[1990-08-09 10:00:16] WARN Disk space low
[1990-08-09 10:00:19] DEBUG Cache cleared
[1990-08-09 10:00:23] WARN Disk space low
[1990-08-09 10:00:25] INFO Service restarted
[1990-08-09 10:00:33] WARN Disk space low
[1990-08-09 10:00:38] ERROR Connection lost
[1990-08-09 10:00:46] ERROR Failed login attempt
[1990-08-09 10:00:48] INFO User logged in
[1990-08-09 10:00:50] INFO User logged in
...

```

> [1990-08-09 10:00:10] INFO FLAGPART: picoCTF{us3_

#### S 2 
> cat server.log | grep -ohP "INFO FLAGPART:(.+)" | sed "s/INFO FLAGPART: //g"  | awk '!x[$0]++' | tr -d '\n' 

``` 
picoCTF{<Flag>}
```
# Finish