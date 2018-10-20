# LEVEL GOAL

We salvaged a ruined Ext SuperMagic II-class mech recently and pulled the filesystem out of the black box. It looks a bit corrupted, but maybe there's something interesting in there. You can also find it in /problems/ext-super-magic_0_621bc2a94057a3e5a0aa0816da3fe8fb on the shell server. 

# HINTS

1. Are there any tools for diagnosing corrupted filesystems? What do they say if you run them on this one?

2. How does a linux machine know what type of file a file is?

3. You might find this doc helpful.

4. Be careful with endianness when making edits.

5. Once you've fixed the corruption, you can use /sbin/debugfs to pull the flag file out.

# SOLUTION

Since we know that the filesystem is corrupt, the first thing to run is the file system checker, `e2fsck`. Maybe we'll get an idea of what is wrong.

```
nikhilh@ubuntu:~/Downloads$ e2fsck -f ext-super-magic.img
e2fsck 1.44.1 (24-Mar-2018)
ext2fs_open2: Bad magic number in super-block
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open ext-super-magic.img
The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>
The supermagic number of EXT2 filesystem is 0xef53
```

Okay, so the superblock is corrupted and contains a bad magic number. This magic number allows tools like `e2fsck` to understand what kind of file system it is dealing with. This is an `ext2` file system which should have a magic number of 0xef53. Now, we need to find the location where we're required to insert this magic number. In other words, we need to find the filesystem superblock. Let's see if `dumpe2fs` works (it wouldn't).

```
nikhilh@ubuntu:~/Downloads$ dumpe2fs ext-super-magic.img 
dumpe2fs 1.44.1 (24-Mar-2018)
dumpe2fs: Bad magic number in super-block while trying to open ext-super-magic.img
Couldn't find valid filesystem superblock.
```

===================================================================================

nikhilh@ubuntu:~/Downloads$ xxd ext-super-magic.img > hexdump`

`nikhilh@ubuntu:~/Downloads$ cat hexdump`

`...`

`00000430: d8da ad5b 0100 ffff 0000 0100 0100 0000  ...[............`

`...`

changed to

`...`

`00000430: d8da ad5b 0100 ffff 53ef 0100 0100 0000  ...[............`

`...`

`nikhilh@ubuntu:~/Downloads$ xxd -r hexdump > ext_test.img`

`nikhilh@ubuntu:~/Downloads$ /sbin/debugfs ext_test.img `

`debugfs 1.44.1 (24-Mar-2018)`

`debugfs:  dump_inode flag.jpg flag_test.jpg`

`debugfs:  q`

`nikhilh@ubuntu:~/Downloads$ ls`

`ext-super-magic.img  ext_test.img  flag_test.jpg  hexdump`

The flag_test.jpg contains the flag

# FLAG

picoCTF{FDBfbC6141e7F4b8c90C9aE78b963aEf}
