# lsof
* https://unix.stackexchange.com/questions/28464/lsof-age-of-file
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

### Descriptor list & datetime

lsof -p $(pidof filebeat)
```
COMMAND    PID USER   FD      TYPE             DEVICE  SIZE/OFF     NODE NAME
filebeat 32301 root  cwd       DIR              253,0       224       64 /
filebeat 32301 root  rtd       DIR              253,0       224       64 /
filebeat 32301 root  txt       REG              253,0 101869024  1666473 /usr/share/filebeat/bin/filebeat
filebeat 32301 root  mem       REG              253,0     61560    15688 /usr/lib64/libnss_files-2.17.so
filebeat 32301 root  mem       REG              253,0   2156344    15664 /usr/lib64/libc-2.17.so
filebeat 32301 root  mem       REG              253,0     19248    15671 /usr/lib64/libdl-2.17.so
filebeat 32301 root  mem       REG              253,0    142144    15698 /usr/lib64/libpthread-2.17.so
filebeat 32301 root  mem       REG              253,0    163312  1362423 /usr/lib64/ld-2.17.so
filebeat 32301 root    0r      CHR                1,3       0t0     6382 /dev/null
filebeat 32301 root    1u     unix 0xffff9a9bf0ae7b80       0t0  1186174 socket
filebeat 32301 root    2u     unix 0xffff9a9bf0ae7b80       0t0  1186174 socket
filebeat 32301 root    3u  a_inode               0,10         0     6378 [eventpoll]
filebeat 32301 root    4r     FIFO                0,9       0t0  1185128 pipe
filebeat 32301 root    5w     FIFO                0,9       0t0  1185128 pipe
filebeat 32301 root    6u     unix 0xffff9a9b7b3aea80       0t0  1185132 socket
filebeat 32301 root    7r      REG              253,0       216 13118340 /home/centos/test4.txt
filebeat 32301 root    8rW     REG              253,0         0  1668706 /var/lib/filebeat/filebeat.lock
filebeat 32301 root    9u     sock                0,7       0t0  1185700 protocol: TCPv6
filebeat 32301 root   12u      REG              253,0     52295  8795693 /var/lib/filebeat/registry/filebeat/log.json
```

for file in /proc/$(pidof filebeat)/fd/*; do ls -lahtr $file; done
```
lr-x------. 1 root root 64 18 mars  15:47 /proc/32301/fd/0 -> /dev/null
lrwx------. 1 root root 64 18 mars  15:47 /proc/32301/fd/1 -> socket:[1186174]
lrwx------. 1 root root 64 18 mars  15:47 /proc/32301/fd/12 -> /var/lib/filebeat/registry/filebeat/log.json
lrwx------. 1 root root 64 18 mars  15:47 /proc/32301/fd/2 -> socket:[1186174]
lrwx------. 1 root root 64 18 mars  15:47 /proc/32301/fd/3 -> anon_inode:[eventpoll]
lr-x------. 1 root root 64 18 mars  15:47 /proc/32301/fd/4 -> pipe:[1185128]
l-wx------. 1 root root 64 18 mars  15:47 /proc/32301/fd/5 -> pipe:[1185128]
lrwx------. 1 root root 64 18 mars  15:47 /proc/32301/fd/6 -> socket:[1185132]
lr-x------. 1 root root 64 18 mars  16:19 /proc/32301/fd/7 -> /home/centos/test4.txt
lr-x------. 1 root root 64 18 mars  15:47 /proc/32301/fd/8 -> /var/lib/filebeat/filebeat.lock
lrwx------. 1 root root 64 18 mars  15:47 /proc/32301/fd/9 -> socket:[1185700]
```
