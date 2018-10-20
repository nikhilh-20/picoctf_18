# LEVEL GOAL

Can you find the flag in file? This would be really obnoxious to look through by hand, see if you can find a faster way. You can also find the file in /problems/grep-1_4_0431431e36a950543a85426d0299343e on the shell server.

# HINTS

None

# SOLUTION

```
nikel@pico-2018-shell-1:~$ cd /problems/grep-1_4_0431431e36a950543a85426d0299343e

nikel@pico-2018-shell-1:/problems/grep-1_4_0431431e36a950543a85426d0299343e$ ls
file

nikel@pico-2018-shell-1:/problems/grep-1_4_0431431e36a950543a85426d0299343e$ cat file | grep picoCTF{
picoCTF{grep_and_you_will_find_d66382d8}
```

# FLAG

picoCTF{grep_and_you_will_find_d66382d8}
