## Analyse

### secret_phase

```assembly
   0x0000000000401242 <+0>:	push   %rbx
   0x0000000000401243 <+1>:	callq  0x40149e <read_line>
   0x0000000000401248 <+6>:	mov    $0xa,%edx # rdx = 10
   0x000000000040124d <+11>:	mov    $0x0,%esi
   0x0000000000401252 <+16>:	mov    %rax,%rdi
   0x0000000000401255 <+19>:	callq  0x400bd0 <strtol@plt> strtol(&input, 0x0, 10)
   0x000000000040125a <+24>:	mov    %rax,%rbx
   0x000000000040125d <+27>:	lea    -0x1(%rax),%eax
   0x0000000000401260 <+30>:	cmp    $0x3e8,%eax
   0x0000000000401265 <+35>:	jbe    0x40126c <secret_phase+42> # input <= 1001
   0x0000000000401267 <+37>:	callq  0x40143a <explode_bomb>
   0x000000000040126c <+42>:	mov    %ebx,%esi # rsi = input
   0x000000000040126e <+44>:	mov    $0x6030f0,%edi # rdi = 0x6030f0
   0x0000000000401273 <+49>:	callq  0x401204 <fun7> # fun7(0x6030f0, input)
   0x0000000000401278 <+54>:	cmp    $0x2,%eax
   0x000000000040127b <+57>:	je     0x401282 <secret_phase+64>
   0x000000000040127d <+59>:	callq  0x40143a <explode_bomb>
   0x0000000000401282 <+64>:	mov    $0x402438,%edi
   0x0000000000401287 <+69>:	callq  0x400b10 <puts@plt>
   0x000000000040128c <+74>:	callq  0x4015c4 <phase_defused>
   0x0000000000401291 <+79>:	pop    %rbx
   0x0000000000401292 <+80>:	retq
```

### fun7

```assembly
   0x0000000000401204 <+0>:	sub    $0x8,%rsp
   0x0000000000401208 <+4>:	test   %rdi,%rdi 
   0x000000000040120b <+7>:	je     0x401238 <fun7+52>
   0x000000000040120d <+9>:	mov    (%rdi),%edx # rdx = node
   0x000000000040120f <+11>:	cmp    %esi,%edx 
   0x0000000000401211 <+13>:	jle    0x401220 <fun7+28> # if input >= node, jmp
   0x0000000000401213 <+15>:	mov    0x8(%rdi),%rdi # rdi = rdi.prev
   0x0000000000401217 <+19>:	callq  0x401204 <fun7>
   0x000000000040121c <+24>:	add    %eax,%eax # rax *= 2
   0x000000000040121e <+26>:	jmp    0x40123d <fun7+57>
   0x0000000000401220 <+28>:	mov    $0x0,%eax # rax = 0
   0x0000000000401225 <+33>:	cmp    %esi,%edx
   0x0000000000401227 <+35>:	je     0x40123d <fun7+57> # if input = node, return 0
   0x0000000000401229 <+37>:	mov    0x10(%rdi),%rdi # rdi = rdi.next
   0x000000000040122d <+41>:	callq  0x401204 <fun7>
   0x0000000000401232 <+46>:	lea    0x1(%rax,%rax,1),%eax # rax = 2 rax + 1
   0x0000000000401236 <+50>:	jmp    0x40123d <fun7+57>
   0x0000000000401238 <+52>:	mov    $0xffffffff,%eax
   0x000000000040123d <+57>:	add    $0x8,%rsp
   0x0000000000401241 <+61>:	retq
   
#          0x24
#    0x08       0x32
# 0x06  0x16 0x2d  0x6b
# Answer is 0x16
```

