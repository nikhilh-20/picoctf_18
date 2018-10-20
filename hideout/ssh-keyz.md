# LEVEL GOAL

As nice as it is to use our webshell, sometimes its helpful to connect directly to our machine. To do so, please add your own public key to ~/.ssh/authorized_keys, using the webshell. The flag is in the ssh banner which will be displayed when you login remotely with ssh to  with your username.

# HINTS

None

# SOLUTION

Adding our local system's public key (generated through `ssh-keygen` utility) to the web shell's `authorized_keys` list enables us to connect directly to the web shell from our local system's command line.

Local system:

```
nikhilh@ubuntu:~/picoctf_2018/hideout$ cat ~/.ssh/id_rsa.pub
ssh-rsa AAA.../.../.../.../... nikhilh@ubuntu
```

Web shell:

```
nikel@pico-2018-shell-1:~$ mkdir .ssh; cd .ssh

nikel@pico-2018-shell-1:~/.ssh$ echo "ssh-rsa AAA.../.../.../.../... nikhilh@ubuntu" > authorized_keys

nikel@pico-2018-shell-1:~/.ssh$ ssh nikel@2018shell1.picoctf.com
The authenticity of host '2018shell1.picoctf.com (18.223.208.176)' can't be established.
ECDSA key fingerprint is SHA256:zCX5ip3tx1RMbsJBc70jEazd+gAFzlbC1Q2iDI8LA/k.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '2018shell1.picoctf.com,18.223.208.176' (ECDSA) to the list of known hosts.
picoCTF{who_n33ds_p4ssw0rds_38dj21}
```

# FLAG

picoCTF{who_n33ds_p4ssw0rds_38dj21}
