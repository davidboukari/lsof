# lsof

```
lsof -p `pidof filebeat`
COMMAND    PID USER   FD      TYPE             DEVICE  SIZE/OFF    NODE NAME
filebeat 27751 root  cwd       DIR              253,0       224      64 /
filebeat 27751 root  rtd       DIR              253,0       224      64 /
filebeat 27751 root  txt       REG              253,0 101869024 1666473 /usr/share/filebeat/bin/filebeat
filebeat 27751 root  mem       REG              253,0     61560   15688 /usr/lib64/libnss_files-2.17.so
filebeat 27751 root  mem       REG              253,0   2156344   15664 /usr/lib64/libc-2.17.so
filebeat 27751 root  mem       REG              253,0     19248   15671 /usr/lib64/libdl-2.17.so
filebeat 27751 root  mem       REG              253,0    142144   15698 /usr/lib64/libpthread-2.17.so
filebeat 27751 root  mem       REG              253,0    163312 1362423 /usr/lib64/ld-2.17.so
filebeat 27751 root    0r      CHR                1,3       0t0    6382 /dev/null
filebeat 27751 root    1u     unix 0xffff9a9bf0ae7300       0t0 1086307 socket
filebeat 27751 root    2u     unix 0xffff9a9bf0ae7300       0t0 1086307 socket
filebeat 27751 root    3u  a_inode               0,10         0    6378 [eventpoll]
filebeat 27751 root    4r     FIFO                0,9       0t0 1086841 pipe
filebeat 27751 root    5w     FIFO                0,9       0t0 1086841 pipe
filebeat 27751 root    6u     unix 0xffff9a9b79174000       0t0 1086845 socket
filebeat 27751 root    9rW     REG              253,0         0 1668706 /var/lib/filebeat/filebeat.lock
filebeat 27751 root   14u      REG              253,0     34633 8795693 /var/lib/filebeat/registry/filebeat/log.json
```
