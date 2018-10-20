# LEVEL GOAL

Okay, so we found some important looking files on a linux computer. Maybe they can be used to get a password to the process. Connect with nc 2018shell1.picoctf.com 35225. Files can be found here: passwd [1]  shadow [2] .

# HINTS

(1) If at first you don't succeed, try, try again. And again. And again. (2) If you're not careful these kind of problems can really "rockyou".

#SOLUTION

`nikhilh@ubuntu:~/Downloads/john-1.8.0/run$./john../../shadow`

`Loaded1passwordhash(crypt,genericcrypt(3)[?/64])`

`Press'q'orCtrl-Ctoabort,almostanyotherkeyforstatus`

`password1(root)`

`1g0:00:00:18100%2/30.05543g/s166.5p/s166.5c/s166.5C/s123456..pepper`

`Usethe"--show"optiontodisplayallofthecrackedpasswordsreliably`

`Sessioncompleted`

`nikhilh@ubuntu:~/Downloads/john-1.8.0/run$./john--show../../shadow`

`root:password1:17770:0:99999:7:::`

`1passwordhashcracked,0left`

`nikel@pico-2018-shell-1:~$nc2018shell1.picoctf.com35225`

`Username:root`

`Password:password1`

`picoCTF{J0hn_1$_R1pp3d_99c35524}`

# FLAG

picoCTF{J0hn_1$_R1pp3d_99c35524}
