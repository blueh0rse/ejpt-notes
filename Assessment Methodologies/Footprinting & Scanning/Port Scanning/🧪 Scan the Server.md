---
up: "[[Port Scanning]]"
---

# 🧪 Scan the Server

This lab covers the process of performing port scanning and service detection with Nmap.

Let's look at our IP address:

```bash
root@attackdefense:~# ip ad
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: ip_vti0@NONE: <NOARP> mtu 1480 qdisc noop state DOWN group default qlen 1000
    link/ipip 0.0.0.0 brd 0.0.0.0
162965: eth0@if162966: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:0a:01:00:1b brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet 10.1.0.27/16 brd 10.1.255.255 scope global eth0
       valid_lft forever preferred_lft forever
162968: eth1@if162969: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:c0:1c:c1:02 brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet 192.28.193.2/24 brd 192.28.193.255 scope global eth1
       valid_lft forever preferred_lft forever
```

> [!info] IP
> Our IP is 192.28.193.2

Let's scan the network to discover hosts:

```bash
# nmap -sn 192.28.193.0/24
Starting Nmap 7.70 ( https://nmap.org ) at 2024-01-25 14:44 UTC
Nmap scan report for linux (192.28.193.1)
Host is up (0.000070s latency).
MAC Address: 02:42:39:77:49:5E (Unknown)
Nmap scan report for target-1 (192.28.193.3)
Host is up (0.000020s latency).
MAC Address: 02:42:C0:1C:C1:03 (Unknown)
Nmap scan report for attackdefense.com (192.28.193.2)
Host is up.
Nmap done: 256 IP addresses (3 hosts up) scanned in 2.02 seconds
```

> [!NOTE] Title
> Target seems to be 192.28.193.3

Now let's scan for open ports:

```bash
# nmap -sS -p- -T5 $TRG
Starting Nmap 7.70 ( https://nmap.org ) at 2024-01-25 14:49 UTC
Nmap scan report for target-1 (192.28.193.3)
Host is up (0.000012s latency).
Not shown: 65532 closed ports
PORT      STATE SERVICE
6421/tcp  open  nim-wan
41288/tcp open  unknown
55413/tcp open  unknown
MAC Address: 02:42:C0:1C:C1:03 (Unknown)

Nmap done: 1 IP address (1 host up) scanned in 1.62 seconds
```

Now add OS and Service Version detection:

```bash
# nmap -O -sV -p- $TRG
Starting Nmap 7.70 ( https://nmap.org ) at 2024-01-25 14:47 UTC
Nmap scan report for target-1 (192.28.193.3)
Host is up (0.000052s latency).
Not shown: 65532 closed ports
PORT      STATE SERVICE VERSION
6421/tcp  open  mongodb MongoDB 2.6.10
41288/tcp open  achat   AChat chat system
55413/tcp open  ftp     vsftpd 3.0.3
MAC Address: 02:42:C0:1C:C1:03 (Unknown)
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.70%E=4%D=1/25%OT=6421%CT=1%CU=30199%PV=N%DS=1%DC=D%G=Y%M=0242C0
OS:%TM=65B27496%P=x86_64-pc-linux-gnu)SEQ(SP=F9%GCD=1%ISR=10C%TI=Z%CI=Z%II=
OS:I%TS=A)OPS(O1=M5B4ST11NW7%O2=M5B4ST11NW7%O3=M5B4NNT11NW7%O4=M5B4ST11NW7%
OS:O5=M5B4ST11NW7%O6=M5B4ST11)WIN(W1=FE88%W2=FE88%W3=FE88%W4=FE88%W5=FE88%W
OS:6=FE88)ECN(R=Y%DF=Y%T=40%W=FAF0%O=M5B4NNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=
OS:O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD
OS:=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0
OS:%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1
OS:(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI
OS:=N%T=40%CD=S)

Network Distance: 1 hop
Service Info: OS: Unix

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 24.86 seconds
```

Now let's test the basic scripts against the discovered ports:

```bash
# nmap -sC -sV -p 6421,41288,55413 $TRG
Starting Nmap 7.70 ( https://nmap.org ) at 2024-01-25 14:54 UTC
Nmap scan report for target-1 (192.28.193.3)
Host is up (0.000038s latency).

PORT      STATE SERVICE VERSION
6421/tcp  open  mongodb MongoDB 2.6.10 2.6.10
| mongodb-databases: 
|   databases
|     0
|       empty = false
|       sizeOnDisk = 83886080.0
|       name = local
|     1
|       empty = true
|       sizeOnDisk = 1.0
|       name = admin
|   ok = 1.0
|_  totalSize = 83886080.0
| mongodb-info: 
|   MongoDB Build info
|     allocator = tcmalloc
|     OpenSSLVersion = OpenSSL 1.0.2g  1 Mar 2016
|     gitVersion = nogitversion
|     bits = 64
|     debug = false
|     compilerFlags = -Wnon-virtual-dtor -Woverloaded-virtual -fPIC -fno-strict-aliasing -ggdb -pthread -Wall -Wsign-compare -Wno-unused-function -Wno-unused-variable -Wno-maybe-uninitialized -Wno-unknown-pragmas -Winvalid-pch -pipe -Werror -O3 -Wno-unused-local-typedefs -Wno-unused-function -Wno-deprecated-declarations -fno-builtin-memcmp
|     versionArray
|       2 = 10
|       3 = 0
|       0 = 2
|       1 = 6
|     javascriptEngine = V8
|     maxBsonObjectSize = 16777216
|     version = 2.6.10
|     ok = 1.0
|     loaderFlags = -fPIC -pthread -Wl,-z,now -rdynamic
|     sysInfo = Linux lgw01-12 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:16:20 UTC 2015 x86_64 BOOST_LIB_VERSION=1_58
|   Server status
|     host = victim-1:6421
|     connections
|       totalCreated = 11
|       current = 2
|       available = 838858
|     opcountersRepl
|       getmore = 0
|       insert = 0
|       delete = 0
|       query = 0
|       command = 0
|       update = 0
|     metrics
|       record
|         moves = 0
|       queryExecutor
|         scanned = 0
|         scannedObjects = 0
|       getLastError
|         wtimeouts = 0
|         wtime
|           totalMillis = 0
|           num = 0
|       operation
|         scanAndOrder = 0
|         fastmod = 0
|         idhack = 0
|       ttl
|         deletedDocuments = 0
|         passes = 15
|       cursor
|         timedOut = 0
|         open
|           pinned = 0
|           noTimeout = 0
|           total = 0
|       storage
|         freelist
|           search
|             bucketExhausted = 0
|             requests = 6
|             scanned = 11
|       document
|         deleted = 0
|         updated = 0
|         returned = 0
|         inserted = 1
|       repl
|         apply
|           ops = 0
|           batches
|             totalMillis = 0
|             num = 0
|         buffer
|           maxSizeBytes = 268435456
|           sizeBytes = 0
|           count = 0
|         preload
|           docs
|             totalMillis = 0
|             num = 0
|           indexes
|             totalMillis = 0
|             num = 0
|         network
|           ops = 0
|           readersCreated = 0
|           bytes = 0
|           getmores
|             totalMillis = 0
|             num = 0
|     uptimeEstimate = 910.0
|     recordStats
|       admin
|         pageFaultExceptionsThrown = 0
|         accessesNotInMemory = 0
|       local
|         pageFaultExceptionsThrown = 0
|         accessesNotInMemory = 0
|       pageFaultExceptionsThrown = 0
|       accessesNotInMemory = 0
|     uptimeMillis = 920474
|     network
|       numRequests = 3
|       bytesOut = 8997
|       bytesIn = 195
|     version = 2.6.10
|     dur
|       journaledMB = 0.0
|       earlyCommits = 0
|       timeMs
|         writeToJournal = 0
|         remapPrivateView = 0
|         dt = 3070
|         prepLogBuffer = 0
|         writeToDataFiles = 0
|       commitsInWriteLock = 0
|       writeToDataFilesMB = 0.0
|       compression = 0.0
|       commits = 30
|     globalLock
|       totalTime = 920474000
|       currentQueue
|         writers = 0
|         readers = 0
|         total = 0
|       activeClients
|         writers = 0
|         readers = 0
|         total = 0
|       lockTime = 42006
|     ok = 1.0
|     asserts
|       msg = 0
|       user = 0
|       regular = 0
|       rollovers = 0
|       warning = 0
|     cursors
|       totalOpen = 0
|       pinned = 0
|       note = deprecated, use server status metrics
|       timedOut = 0
|       totalNoTimeout = 0
|       clientCursors_size = 0
|     extra_info
|       page_faults = 3
|       heap_usage_bytes = 62664048
|       note = fields vary by platform
|     writeBacksQueued = false
|     mem
|       supported = true
|       resident = 43
|       bits = 64
|       mappedWithJournal = 160
|       mapped = 80
|       virtual = 382
|     uptime = 921.0
|     indexCounters
|       misses = 0
|       hits = 2
|       accesses = 2
|       missRatio = 0.0
|       resets = 0
|     localTime = 1706194507431
|     locks
|       admin
|         timeLockedMicros
|           r = 566
|           w = 0
|         timeAcquiringMicros
|           r = 28
|           w = 0
|       local
|         timeLockedMicros
|           r = 3624
|           w = 0
|         timeAcquiringMicros
|           r = 1305
|           w = 0
|       .
|         timeLockedMicros
|           R = 18984
|           W = 42006
|         timeAcquiringMicros
|           R = 8004
|           W = 1887
|     backgroundFlushing
|       last_finished = 1706194486977
|       flushes = 15
|       total_ms = 5
|       average_ms = 0.33333333333333
|       last_ms = 0
|     pid = 26
|     process = mongod
|     opcounters
|       getmore = 0
|       insert = 1
|       delete = 0
|       query = 31
|       command = 6
|_      update = 0
41288/tcp open  achat   AChat chat system
55413/tcp open  ftp     vsftpd 3.0.3
MAC Address: 02:42:C0:1C:C1:03 (Unknown)
Service Info: OS: Unix

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 14.33 seconds
```

Let's search for specific scripts:

```bash
# ls -la /usr/share/nmap/scripts/ | grep mongo
-rw-r--r-- 1 root root  2578 Jan  9  2019 mongodb-brute.nse
-rw-r--r-- 1 root root  2583 Jan  9  2019 mongodb-databases.nse
-rw-r--r-- 1 root root  3663 Jan  9  2019 mongodb-info.nse

# ls -la /usr/share/nmap/scripts/ | grep ftp  
-rw-r--r-- 1 root root  4530 Jan  9  2019 ftp-anon.nse
-rw-r--r-- 1 root root  3253 Jan  9  2019 ftp-bounce.nse
-rw-r--r-- 1 root root  3108 Jan  9  2019 ftp-brute.nse
-rw-r--r-- 1 root root  3258 Jan  9  2019 ftp-libopie.nse
-rw-r--r-- 1 root root  3295 Jan  9  2019 ftp-proftpd-backdoor.nse
-rw-r--r-- 1 root root  3748 Jan  9  2019 ftp-syst.nse
-rw-r--r-- 1 root root  6007 Jan  9  2019 ftp-vsftpd-backdoor.nse
-rw-r--r-- 1 root root  5943 Jan  9  2019 ftp-vuln-cve2010-4221.nse
-rw-r--r-- 1 root root  5678 Jan  9  2019 tftp-enum.nse

# ls -la /usr/share/nmap/scripts/ | grep memcached
-rw-r--r-- 1 root root  5655 Jan  9  2019 memcached-info.nse
```

Let's try some:

```bash
# nmap --script=memcached-info -p 41288 -sV $TRG
Starting Nmap 7.70 ( https://nmap.org ) at 2024-01-25 15:01 UTC
Nmap scan report for target-1 (192.28.193.3)
Host is up (0.000051s latency).

PORT      STATE SERVICE   VERSION
41288/tcp open  memcached Memcached
| memcached-info: 
|   Process ID: 27
|   Uptime: 1328 seconds
|   Server time: 2024-01-25T15:01:52
|   Architecture: 64 bit
|   Used CPU (user): 0.102443
|   Used CPU (system): 0.073445
|   Current connections: 2
|   Total connections: 7
|   Maximum connections: 1024
|   TCP Port: 41288
|   UDP Port: 0
|_  Authentication: no
MAC Address: 02:42:C0:1C:C1:03 (Unknown)

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 6.61 seconds
```
