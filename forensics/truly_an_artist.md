# LEVEL GOAL

Can you help us find the flag in this Meta-Material [1] ? You can also find the file in /problems/truly-an-artist_2_61a3ed7216130ab1c2b2872eeda81348.

# HINTS

(1) Try looking beyond the image. (2) Who created this?

# SOLUTION

I used the ExifTool tool to view the image's metadata

```
nikhilh@ubuntu:~/Downloads/Image-ExifTool-11.10$ ./exiftool ../2018.png
ExifTool Version Number         : 11.10
File Name                       : 2018.png
Directory                       : ..
File Size                       : 13 kB
File Modification Date/Time     : 2018:09:28 17:42:00-07:00
File Access Date/Time           : 2018:09:28 17:42:22-07:00
File Inode Change Date/Time     : 2018:09:28 17:42:03-07:00
File Permissions                : rw-rw-r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 1200
Image Height                    : 630
Bit Depth                       : 8
Color Type                      : RGB
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Artist                          : picoCTF{look_in_image_7e31505f}
Image Size                      : 1200x630
Megapixels                      : 0.756
```

# FLAG

picoCTF{look_in_image_7e31505f}
