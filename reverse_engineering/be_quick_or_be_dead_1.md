# LEVEL GOAL

You find this [1]  when searching for some music, which leads you to be-quick-or-be-dead-1 [2] . Can you run it fast enough? You can also find the executable in /problems/be-quick-or-be-dead-1_3_aeb48854203a88fb1da963f41ae06a1c.

# HINTS

(1) What will the key finally be?

# SOLUTION

```
nikhilh@ubuntu:~/Downloads$ gdb -q be-quick-or-be-dead-1
Reading symbols from be-quick-or-be-dead-1...(no debugging symbols found)...done.

(gdb) disas main
Dump of assembler code for function main:
   0x0000000000400827 <+0>:	push   %rbp
   0x0000000000400828 <+1>:	mov    %rsp,%rbp
   0x000000000040082b <+4>:	sub    $0x10,%rsp
   0x000000000040082f <+8>:	mov    %edi,-0x4(%rbp)
   0x0000000000400832 <+11>:	mov    %rsi,-0x10(%rbp)
   0x0000000000400836 <+15>:	mov    $0x0,%eax
   0x000000000040083b <+20>:	callq  0x4007e9 <header>
   0x0000000000400840 <+25>:	mov    $0x0,%eax
   0x0000000000400845 <+30>:	callq  0x400742 <set_timer>
   0x000000000040084a <+35>:	mov    $0x0,%eax
   0x000000000040084f <+40>:	callq  0x400796 <get_key>
   0x0000000000400854 <+45>:	mov    $0x0,%eax
   0x0000000000400859 <+50>:	callq  0x4007c1 <print_flag>
   0x000000000040085e <+55>:	mov    $0x0,%eax
   0x0000000000400863 <+60>:	leaveq 
   0x0000000000400864 <+61>:	retq   
End of assembler dump.

(gdb) b * 0x0000000000400845
Breakpoint 1 at 0x400845

(gdb) r
Starting program: /home/nikhilh/Downloads/be-quick-or-be-dead-1 
Be Quick Or Be Dead 1
=====================


Breakpoint 1, 0x0000000000400845 in main ()

(gdb) set *(int *)0x0000000000400845=0x90909090

(gdb) disas main
Dump of assembler code for function main:
   0x0000000000400827 <+0>:	push   %rbp
   0x0000000000400828 <+1>:	mov    %rsp,%rbp
   0x000000000040082b <+4>:	sub    $0x10,%rsp
   0x000000000040082f <+8>:	mov    %edi,-0x4(%rbp)
   0x0000000000400832 <+11>:	mov    %rsi,-0x10(%rbp)
   0x0000000000400836 <+15>:	mov    $0x0,%eax
   0x000000000040083b <+20>:	callq  0x4007e9 <header>
   0x0000000000400840 <+25>:	mov    $0x0,%eax
=> 0x0000000000400845 <+30>:	nop
   0x0000000000400846 <+31>:	nop
   0x0000000000400847 <+32>:	nop
   0x0000000000400848 <+33>:	nop
   0x0000000000400849 <+34>:	(bad)  
   0x000000000040084a <+35>:	mov    $0x0,%eax
   0x000000000040084f <+40>:	callq  0x400796 <get_key>
   0x0000000000400854 <+45>:	mov    $0x0,%eax
   0x0000000000400859 <+50>:	callq  0x4007c1 <print_flag>
   0x000000000040085e <+55>:	mov    $0x0,%eax
   0x0000000000400863 <+60>:	leaveq 
   0x0000000000400864 <+61>:	retq   
End of assembler dump.

(gdb) set *(char *)0x0000000000400849=0x90

(gdb) disas main
Dump of assembler code for function main:
   0x0000000000400827 <+0>:	push   %rbp
   0x0000000000400828 <+1>:	mov    %rsp,%rbp
   0x000000000040082b <+4>:	sub    $0x10,%rsp
   0x000000000040082f <+8>:	mov    %edi,-0x4(%rbp)
   0x0000000000400832 <+11>:	mov    %rsi,-0x10(%rbp)
   0x0000000000400836 <+15>:	mov    $0x0,%eax
   0x000000000040083b <+20>:	callq  0x4007e9 <header>
   0x0000000000400840 <+25>:	mov    $0x0,%eax
=> 0x0000000000400845 <+30>:	nop
   0x0000000000400846 <+31>:	nop
   0x0000000000400847 <+32>:	nop
   0x0000000000400848 <+33>:	nop
   0x0000000000400849 <+34>:	nop
   0x000000000040084a <+35>:	mov    $0x0,%eax
   0x000000000040084f <+40>:	callq  0x400796 <get_key>
   0x0000000000400854 <+45>:	mov    $0x0,%eax
   0x0000000000400859 <+50>:	callq  0x4007c1 <print_flag>
   0x000000000040085e <+55>:	mov    $0x0,%eax
   0x0000000000400863 <+60>:	leaveq 
   0x0000000000400864 <+61>:	retq   
End of assembler dump.

(gdb) c
Continuing.
Calculating key...
Done calculating key
Printing flag:
picoCTF{why_bother_doing_unnecessary_computation_27f28e71}
[Inferior 1 (process 9209) exited normally]
(gdb) 
```
# FLAG

picoCTF{why_bother_doing_unnecessary_computation_27f28e71}
