# LEVEL GOAL

Can you deal with the Duck Web? Get us the flag from this program. You can also find the program in /problems/quackme_3_9a15a74731538ce2076cd6590cf9e6ca.

# HINTS

Objdump or something similar is probably a good place to start.

# SOLUTION

```
nikel@pico-2018-shell-1:/problems/quackme_3_9a15a74731538ce2076cd6590cf9e6ca$ ls
main

nikel@pico-2018-shell-1:/problems/quackme_3_9a15a74731538ce2076cd6590cf9e6ca$ ./main
You have now entered the Duck Web, and you're in for a honkin' good time.
Can you figure out my trick?
sdadadfnasd
That's all folks.
```

On studying the `do_magic()`, I came up with the following pseudo-code:

```
input = read_input()
len = strlen(input)
len = len+1

ptr = malloc(len)
if (!ptr)
exit();

memset(ptr, 0, len)

// ebp-0x1c = var1
// ebp-0x18 = var2
// ebp-0x1d = var3
var1 = var2 = 0
var3

while (var2 != len) {
eax = var2 + secret_buffer_mem_address
ecx = [al]

eax = var2 + input_mem_address
eax = [al]

eax = eax ^ ecx (secret_buffer ^ input)
var3 = [al]

edx = "You have now entered the Duck Web, and you're in for a honkin' good time.\nCan you figure out my trick?" (<- mem address of string)
eax = var2 + edx
eax = [al]

if (al == var3) {
var1 += 1
} else if (var1 == 0x19) {
printf ("You are winner!")
return
}

var2 += 1
}
```

We can see that the code is trying to compare the string, "You have now entered the Duck Web, and you're in for a honkin' good time.\nCan you figure out my trick?" with the result of input ^ secret_buffer. The next step is to find the value of input such that the printf("You are winner!") statement is executed.

25 bytes of secret_buffer are as follows:

```
(gdb) x/25xb 0x8048858
0x8048858 : 0x29 0x06 0x16 0x4f 0x2b 0x35 0x30 0x1e
0x8048860 <sekrutBuffer+8>: 0x51 0x1b 0x5b 0x14 0x4b 0x08 0x5d 0x2b
0x8048868 <sekrutBuffer+16>: 0x52 0x17 0x01 0x57 0x16 0x11 0x5c 0x07
0x8048870 <sekrutBuffer+24>: 0x5d
```

I was lucky xor was used in this operation because it is very easy to write decryption code. I wrote one such in Python:

```
output = [0x59, 0x6f, 0x75, 0x20, 0x68, 0x61, 0x76, 0x65, 0x20, 0x6e, 0x6f, 0x77, 0x20, 0x65, 0x6e, 0x74, 0x65, 0x72, 0x65, 0x64, 0x20, 0x74, 0x68, 0x65, 0x20]

secret_buffer = [0x29, 0x06, 0x16, 0x4f, 0x2b, 0x35, 0x30, 0x1e, 0x51, 0x1b, 0x5b, 0x14, 0x4b, 0x08, 0x5d, 0x2b, 0x52, 0x17, 0x01, 0x57, 0x16, 0x11, 0x5c, 0x07, 0x5d]

for index in range(len(output)):
print(format((output[index] ^ secret_buffer[index]), '02x'), end="", flush=True)
```

The output was `7069636f4354467b717534636b6d335f37656433366534627d` which in ASCII is `picoCTF{qu4ckm3_7ed36e4b}`

# FLAG

picoCTF{qu4ckm3_7ed36e4b}
