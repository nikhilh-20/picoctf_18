# LEVEL GOAL

Our network administrator is having some trouble handling the tickets for all of of our incidents. Can you help him out by answering all the questions? Connect with nc 2018shell1.picoctf.com 40952. incidents.json [1] 

# HINTS

(1) If you need to code, python has some good libraries for it.

# SOLUTION

This is more of a data analysis thing. There's nothing serious to explain here.

`nikel@pico-2018-shell-1:~$ nc 2018shell1.picoctf.com 40952`

`You'll need to consult the file `incidents.json` to answer the following questions.`

`What is the most common source IP address? If there is more than one IP address that is the most common, you may give any of the most common ones.`

`99.32.28.173`

`Correct!`

`How many unique destination IP addresses were targeted by the source IP address 99.175.56.242?`

`2`

`Correct!`

`What is the average number of unique destination IP addresses that were sent a file with the same hash? Your answer needs to be correct to 2 decimal places.`

`1.66`

`Correct!`

`Great job. You've earned the flag: picoCTF{J4y_s0n_d3rUUUULo_b6cacd6c}`

# FLAG

picoCTF{J4y_s0n_d3rUUUULo_b6cacd6c}
