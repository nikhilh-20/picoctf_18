# LEVEL GOAL

It's never a bad idea to brush up on those linux skills or even learn some new ones before you set off on this adventure! Connect with nc 2018shell1.picoctf.com 6903.

# HINTS

None

# SOLUTION

```
nikel@pico-2018-shell-1:~$ nc 2018shell1.picoctf.com 6903
Sweet! We have gotten access into the system but we aren't root.
It's some sort of restricted shell! I can't see what you are typing but I can see your output. I'll be here to help you along.
If you need help, type "echo 'Help Me!'" and I'll see what I can do
There is not much time left!

~/$ ls
blackmail
executables
passwords
photos
secret

~/$ cd secret
Now we are cookin'! Take a look around there and tell me what you find!

~/secret$ ls
intel_1
intel_2
intel_3
intel_4
intel_5
profile_AipieG5Ua9aewei5ieSoh7aph
profile_Xei2uu5suwangohceedaifohs
profile_ahShaighaxahMooshuP1johgo
profile_ahqueith5aekongieP4ahzugi
profile_aik4hah9ilie9foru0Phoaph0
profile_bah9Ech9oa4xaicohphahfaiG
profile_ie7sheiP7su2At2ahw6iRikoe
profile_of0Nee4laith8odaeLachoonu
profile_poh9eij4Choophaweiwev6eev
profile_poo3ipohGohThi9Cohverai7e
Sabatoge them! Get rid of all their intel files!

~/secret$ rm intel*
Nice! Once they are all gone, I think I can drop you a file of an exploit!
Just type "echo 'Drop it in!' " and we can give it a whirl!

~/secret$ echo 'Drop it in!'
Drop it in!
I placed a file in the executables folder as it looks like the only place we can execute from!
Run the script I wrote to have a little more impact on the system!

~/secret$ cd ..

~/$ cd executables

~/executables$ ls
dontLookHere

~/executables$ ./dontLookHere
1e68 bffb b93b 5496 5a08 c305 03af 9305 d095 5c7f 9608 4d07 8fd1 866f 6f62 2eea 70e9 749e a9f3 6e78 cd91 13f4 408d b4c3 9b7a
7fc1 a325 48f6 4819 f8e9 c4dd 56b6 d807 876d 2b4d 2184 790b 885c 159c 4665 4719 c909 efe9 439a 6d27 502a 87ea 41c6 b58e ddee 
87b8 675e be3d f24c e014 1ec5 cee2 3dce c6c0 691b 2e37 2b51 a34e 87a6 7d05 8cdc af99 497d 05d2 1a94 126f e3a9 f507 e930 c6a0
...
...
43a0 68cf 7d83 f9bb d631 0b69 345d edbb bb21 083f f769 0132 8613 836c b219 45e5 766c 33c6 d259 0899 ff6e beae 344c d6d0 c4c9
c3ec a5c6 bf98 249d 3990 f2a6 bc40 9b18 0b44 0daf 7622 a92b c753 3a7c 7c26 5983 14b5 3eb3 6729 a84f 7b29 181c 98e5 94c3 5f38
b9c2 3dd4 9a09 f76b 5fa2 ab3c 858c 97ea 02b9 4edd ce67 22c8 3771 5bf6 c4d8 5a5a e810 e9e7 c799 0470 eaa5 d0f1 bd05 f19c 8cca
Looking through the text above, I think I have found the password. I am just having trouble with a username.
Oh drats! They are onto us! We could get kicked out soon!
Quick! Print the username to the screen so we can close are backdoor and log into the account directly!
You have to find another way other than echo!

~/executables$ whoami
l33th4x0r
Perfect! One second!
Okay, I think I have got what we are looking for. I just need to to copy the file to a place we can read.
Try copying the file called TopSecret in tmp directory into the passwords folder.

~/executables$ cd ..

~/$ cp /tmp/TopSecret passwords
Server shutdown in 10 seconds...
Quick! go read the file before we lose our connection!

~/$ cd passwords

~/passwords$ cat TopSecret
Major General John M. Schofield's graduation address to the graduating class of 1879 at West Point is as follows: The discipline which makes the soldiers of a free country reliable in battle is not to be gained by harsh or tyrannical treatment.On the contrary, such treatment is far more likely to destroy than to make an army.It is possible to impart instruction and give commands in such a manner and such a tone of voice as to inspire in the soldier no feeling butan intense desire to obey, while the opposite manner and tone of voice cannot fail to excite strong resentment and a desire to disobey.The one mode or other of dealing with subordinates springs from a corresponding spirit in the breast of the commander.He who feels the respect which is due to others, cannot fail to inspire in them respect for himself, while he who feels,and hence manifests disrespect towards others, especially his subordinates, cannot fail to inspire hatred against himself. picoCTF{CrUsHeD_It_dddcec58}
```

# FLAG

picoCTF{CrUsHeD_It_dddcec58}
