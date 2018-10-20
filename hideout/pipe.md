# LEVEL GOAL

During your adventure, you will likely encounter a situation where you need to process data that you receive over the network rather than through a file. Can you find a way to save the output from this program and search for the flag? Connect with 2018shell1.picoctf.com 48696.

# HINTS

(1) Remember the flag format is picoCTF{XXXX} (2) Ever heard of a pipe? No not that kind of pipe... This kind [1] 

# SOLUTION

```
nikel@pico-2018-shell-1:~$ nc 2018shell1.picoctf.com 48696 | grep picoCTF{
picoCTF{almost_like_mario_f617d1d7}
```

# FLAG

picoCTF{almost_like_mario_f617d1d7}
