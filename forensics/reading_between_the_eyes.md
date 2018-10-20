# LEVEL GOAL

Stego-Saurus hid a message for you in this image [1] , can you retreive it?

# HINTS

(1) Maybe you can find an online decoder?

# SOLUTION

This challenge is based on steganography. How do I know this? Because there's a compressed file inside the image.

```
nikhilh@ubuntu:~/Downloads$ binwalk husky.png 

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 2140 x 2232, 8-bit/color RGBA, non-interlaced
41            0x29            Zlib compressed data, compressed
```

I used an online steganography tool stylesuxx.github.io/steganography. Just upload the image into the decoder and the tool will do the rest.

# FLAG

picoCTF{r34d1ng_b37w33n_7h3_by73s}
