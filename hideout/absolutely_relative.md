# LEVEL GOAL

In a filesystem, everything is relative ¯\_(ツ)_/¯. Can you find a way to get a flag from this program [1] ? You can find it in /problems/absolutely-relative_4_bef88c36784b44d2585bb4d2dbe074bd on the shell server. Source [2] .

# HINTS

(1) Do you have to run the program in the same directory? (⊙.☉)7 (2) Ever used a text editor? Check out the program 'nano'

# SOLUTION

Let's look at `absolutely_relative.c` file:

```
nikel@pico-2018-shell-1:/problems/absolutely-relative_4_bef88c36784b44d2585bb4d2dbe074bd$ cat absolutely-relati
ve.c
...
    file = fopen("/problems/absolutely-relative_4_bef88c36784b44d2585bb4d2dbe074bd/flag.txt" , "r");
    if (file) {
        while (fscanf(file, "%s", flag)!=EOF)
        fclose(file);
    }
...
    file = fopen( "./permission.txt" , "r");
...

    if (!strncmp(permission, yes, yes_len)) {                                                                  
        printf("You have the write permissions.\n%s\n", flag);                                                 
    } else {                                                                                                   
        printf("You do not have sufficient permissions to view the flag.\n");                                  
    }                                                                                                          
```

So, `flag.txt` is accessed as an absolute path but `permission.txt` is a relative path. All we need to do is run from another directory where we can create a local `permission.txt` file having `yes` as its contents.

```
nikel@pico-2018-shell-1:~$ echo "yes" > permission.txt

nikel@pico-2018-shell-1:~$ ls
permission.txt

nikel@pico-2018-shell-1:~$ /problems/absolutely-relative_4_bef88c36784b44d2585bb4d2dbe074bd/absolutely-relative
You have the write permissions.
picoCTF{3v3r1ng_1$_r3l3t1v3_3b69633f}
```

It is very important to understand that you must not copy the executable to another location. This causes the owner and group of that executable to change from the original user:group to your user:group. Even if `You have the write permissions`, you won't be able to read `flag.txt` because it belongs to a different user:group.

`-r--r-----   1 hacksports absolutely-relative_4    37 Sep 28 07:36 flag.txt`

# FLAG

picoCTF{3v3r1ng_1$_r3l3t1v3_3b69633f}
