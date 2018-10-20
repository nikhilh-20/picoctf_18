# LEVEL GOAL

We captured some traffic [1]  logging into the admin panel, can you find the password?

# HINTS

(1) Tools like wireshark are pretty good for analyzing pcap files.

# SOLUTION

Pretty straightforward.

```
nikhilh@ubuntu:~/Downloads$ strings data.pcap | grep picoCTF{
user=admin&password=picoCTF{n0ts3cur3_894a6546}
```

# FLAG

picoCTF{n0ts3cur3_894a6546}
