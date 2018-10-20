# LEVEL GOAL

This one is a little bit harder. Can you find the flag in /problems/grep-2_3_826f886f547acb8a9c3fccb030e8168d/files on the shell server? Remember, grep is your friend.

# HINTS

None

# SOLUTION

```
nikel@pico-2018-shell-1:~$ cd /problems/grep-2_3_826f886f547acb8a9c3fccb030e8168d/files
nikel@pico-2018-shell-1:/problems/grep-2_3_826f886f547acb8a9c3fccb030e8168d/files$ grep -r "picoCTF{" .
./files3/file6:picoCTF{grep_r_and_you_will_find_556620f7}
```

# FLAG

picoCTF{grep_r_and_you_will_find_556620f7}
