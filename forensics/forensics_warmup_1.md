# LEVEL GOAL

Can you unzip this file for me and retreive the flag?

# HINTS

(1) Make sure to submit the flag as picoCTF{XXXXX}

# SOLUTION

The `unzip` utility can be used to unzip `.zip` files.

`nikhilh@ubuntu:~/Downloads$ unzip flag.zip`

`Archive:  flag.zip`

`  inflating: flag.jpg`

`nikhilh@ubuntu:~/Downloads$ ls`

`flag.jpg  flag.zip`

Open the .jpg file from file explorer and the flag is right there.

# FLAG

picoCTF{welcome_to_forensics}
