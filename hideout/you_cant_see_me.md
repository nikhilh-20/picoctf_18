# LEVEL GOAL

'...reading transmission... Y.O.U. .C.A.N.'.T. .S.E.E. .M.E.  ...transmission ended...' Maybe something lies in /problems/you-can-t-see-me_3_1a39ec6c80b3f3a18610074f68acfe69.

# HINTS

(1) What command can see/read files? (2) What's in the manual page of ls?

# SOLUTION

```
nikel@pico-2018-shell-1:~$ cd /problems/you-can-t-see-me_3_1a39ec6c80b3f3a18610074f68acfe69

nikel@pico-2018-shell-1:/problems/you-can-t-see-me_3_1a39ec6c80b3f3a18610074f68acfe69$ ls -la
total 60
drwxr-xr-x   2 root       root        4096 Sep 28 08:29 .
-rw-rw-r--   1 hacksports hacksports    57 Sep 28 08:29 .
drwxr-x--x 576 root       root       53248 Sep 30 03:45 ..
```

So, we know that one `.` is a file. We can't however open it directly using `cat`

```
nikel@pico-2018-shell-1:/problems/you-can-t-see-me_3_1a39ec6c80b3f3a18610074f68acfe69$ cat \.
cat: .: Is a directory
```

Heard of `xargs` before? http://man7.org/linux/man-pages/man1/xargs.1.html

```
nikel@pico-2018-shell-1:/problems/you-can-t-see-me_3_1a39ec6c80b3f3a18610074f68acfe69$ ls -a | xargs -I % cat \%
cat: .: Is a directory
picoCTF{j0hn_c3na_paparapaaaaaaa_paparapaaaaaa_cf5156ef}
cat: ..: Permission denied
```

# FLAG

picoCTF{j0hn_c3na_paparapaaaaaaa_paparapaaaaaa_cf5156ef}
