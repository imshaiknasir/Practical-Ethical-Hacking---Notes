#### 1. Ping an IP
```
ping 172.217.163.164

```

Output:
```
PING 172.217.163.164 (172.217.163.164) 56(84) bytes of data.
64 bytes from 172.217.163.164: icmp_seq=1 ttl=51 time=338 ms
64 bytes from 172.217.163.164: icmp_seq=3 ttl=51 time=238 ms
64 bytes from 172.217.163.164: icmp_seq=4 ttl=51 time=228 ms
64 bytes from 172.217.163.164: icmp_seq=5 ttl=51 time=447 ms
^C
--- 172.217.163.164 ping statistics ---
6 packets transmitted, 4 received, 33.3333% packet loss, time 5107ms
rtt min/avg/max/mdev = 228.086/312.689/446.856/88.568 ms
```

#### 2. Sending only one packet to check the IP is present or not
```
ping 172.217.163.164 -c 1
```

Output:
```
PING 172.217.163.164 (172.217.163.164) 56(84) bytes of data.
64 bytes from 172.217.163.164: icmp_seq=1 ttl=51 time=500 ms

--- 172.217.163.164 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 500.087/500.087/500.087/0.000 ms
```

#### 3. Let us save the output in a test file:
```
# ping 172.217.163.164 -c 1 > pingResult.txt
# cat pingResult.txt  
```

Output:

```
PING 172.217.163.164 (172.217.163.164) 56(84) bytes of data.
64 bytes from 172.217.163.164: icmp_seq=1 ttl=51 time=500 ms

--- 172.217.163.164 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 500.087/500.087/500.087/0.000 ms
```

#### 4. Grabbing the one IP line from the whole text file:
```
# cat pingResult.txt | grep "64 bytes"
```


Output:
```
64 bytes from 172.217.163.164: icmp_seq=1 ttl=51 time=551 ms
```

#### 5. Now, we need to extract only the ip
```
# cat pingResult.txt | grep "64 bytes" | cut -d " " -f 4
```

Output:
```
172.217.163.164:
```


#### 6. Filter the IP by omiting all un-required characters
```
cat pingResult.txt | grep "64 bytes" | cut -d " " -f 4 | tr -d ":" 
```

Output:
```
172.217.163.164
```


