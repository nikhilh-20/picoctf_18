# LEVEL GOAL

This cat [1]  has a secret to teach you. You can also find the file in /problems/hex-editor_3_086632ac634f394afd301fb6a8dbadc6 on the shell server.

# HINTS

(1) What is a hex editor? (2) Maybe google knows

# SOLUTION

The `xxd` tool can be used to hex dump the specified file.

```
nikel@pico-2018-shell-1:~$ cd /problems/hex-editor_3_086632ac634f394afd301fb6a8dbadc6

nikel@pico-2018-shell-1:/problems/hex-editor_3_086632ac634f394afd301fb6a8dbadc6$ ls
hex_editor.jpg

nikel@pico-2018-shell-1:/problems/hex-editor_3_086632ac634f394afd301fb6a8dbadc6$ xxd hex_editor.jpg > ~/hexdump

nikhilh@ubuntu:~/picoctf_2018/forensics$ grep pico dump
00012940: 3a20 2270 6963 6f43 5446 7b61 6e64 5f74  : "picoCTF{and_t

nikhilh@ubuntu:~/picoctf_2018/forensics$ tail -5 dump
00012930: 8a00 ffd9 596f 7572 2066 6c61 6720 6973  ....Your flag is
00012940: 3a20 2270 6963 6f43 5446 7b61 6e64 5f74  : "picoCTF{and_t
00012950: 6861 7473 5f68 6f77 5f75 5f65 6469 745f  hats_how_u_edit_
00012960: 6865 785f 6b69 7474 6f73 5f38 4263 4136  hex_kittos_8BcA6
00012970: 3761 327d 220a                           7a2}".
```

# FLAG 

picoCTF{and_thats_how_u_edit_hex_kittos_8BcA67a2}
