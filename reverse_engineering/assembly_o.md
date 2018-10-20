# LEVEL GOAL

What does asm0(0xaa,0xf2) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. Source [1]  located in the directory at /problems/assembly-0_2_485b2d48345b19addbeb06a36aabdc74.

# HINTS

None

# SOLUTION

`nikel@pico-2018-shell-1:~$ cd /problems/assembly-0_2_485b2d48345b19addbeb06a36aabdc74`
`nikel@pico-2018-shell-1:/problems/assembly-0_2_485b2d48345b19addbeb06a36aabdc74$ ls`
`intro_asm_rev.S`

Open the program and study it. You'll notice that the second argument is being pushed into %eax which always holds the function's return value

# FLAG

0xf2
