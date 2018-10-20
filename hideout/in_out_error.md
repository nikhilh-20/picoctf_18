# LEVEL GOAL

Can you utlize stdin, stdout, and stderr to get the flag from this program [1] ? You can also find it in /problems/in-out-error_2_c33e2a987fbd0f75e78481b14bfd15f4 on the shell server

# HINTS

(1) Maybe you can split the stdout and stderr output?

# SOLUTION

In Linux, STDOUT and STDERROR can be redirected in three ways:

1. `1>` - When we write ./executable > some_file, we basically mean `1>`. This redirects the output of the `executable` to `some_file`.

2. '2>' - This redirects errors from the `executable` to a stream (ex: a file) that we specify

3. `&>` - This redirects output and errors from the `executable` to a stream (ex: a file) that we specify

```
nikel@pico-2018-shell-1:~$ cd /problems/in-out-error_2_c33e2a987fbd0f75e78481b14bfd15f4

nikel@pico-2018-shell-1:/problems/in-out-error_2_c33e2a987fbd0f75e78481b14bfd15f4$ ls
flag.txt  in-out-error

nikel@pico-2018-shell-1:/problems/in-out-error_2_c33e2a987fbd0f75e78481b14bfd15f4$ ./in-out-error 2> ~/err
Hey There!
If you want the flag you have to ask nicely for it.
Enter the phrase "Please may I have the flag?" into stdin and you shall receive.
Please may I have the flag?
Thank you for asking so nicely!
...
...

nikel@pico-2018-shell-1:/problems/in-out-error_2_c33e2a987fbd0f75e78481b14bfd15f4$ cat ~/err | grep picoCTF{
picoCTF{p1p1ng_1S_4_7h1ng_b6f5a788}... ... ...
```

# FLAG

picoCTF{p1p1ng_1S_4_7h1ng_b6f5a788}
