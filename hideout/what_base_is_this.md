# LEVEL GOAL

To be successful on your mission, you must be able read data represented in different ways, such as hexadecimal or binary. Can you get the flag from this program to prove you are ready? Connect with nc 2018shell1.picoctf.com 15853.

# HINTS

To be successful on your mission, you must be able read data represented in different ways, such as hexadecimal or binary. Can you get the flag from this program to prove you are ready? Connect with nc 2018shell1.picoctf.com 15853.

# SOLUTION

Use any online tool to decode:

1. Binary to string - https://codebeautify.org/binary-string-converter

2. Hex to string - https://codebeautify.org/hex-string-converter

3. Octal to string - http://www.unit-conversion.info/texttools/octal/

```
nikel@pico-2018-shell-1:~$ nc 2018shell1.picoctf.com 15853
We are going to start at the very beginning and make sure you understand how data is stored.

lamppost
Please give me the 01101100 01100001 01101101 01110000 01110000 01101111 01110011 01110100 as a word.
To make things interesting, you have 30 seconds.
Input:
lamppost

Please give me the 646f63746f72 as a word.
Input:
doctor

Please give me the  162 157 142 157 164 as a word.
Input:
robot

You got it! You're super quick!
Flag: picoCTF{delusions_about_finding_values_3cc386de}
```

# FLAG

picoCTF{delusions_about_finding_values_3cc386de}
