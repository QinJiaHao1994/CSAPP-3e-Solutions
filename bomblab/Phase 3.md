## Analyse

### phase_3

```assembly
   0x0000000000400f43 <+0>:	sub    $0x18,%rsp
   0x0000000000400f47 <+4>:	lea    0xc(%rsp),%rcx
   0x0000000000400f4c <+9>:	lea    0x8(%rsp),%rdx
   0x0000000000400f51 <+14>:	mov    $0x4025cf,%esi # "%d %d"
   0x0000000000400f56 <+19>:	mov    $0x0,%eax
   0x0000000000400f5b <+24>:	callq  0x400bf0 <__isoc99_sscanf@plt> # sscanf(%rdi, %rsi, %rdx, %rcx);
   0x0000000000400f60 <+29>:	cmp    $0x1,%eax
   0x0000000000400f63 <+32>:	jg     0x400f6a <phase_3+39>
   0x0000000000400f65 <+34>:	callq  0x40143a <explode_bomb>
   0x0000000000400f6a <+39>:	cmpl   $0x7,0x8(%rsp) 
   0x0000000000400f6f <+44>:	ja     0x400fad <phase_3+106> # 0 <= number[0] <= 7
   0x0000000000400f71 <+46>:	mov    0x8(%rsp),%eax # eax = number[0]
   0x0000000000400f75 <+50>:	jmpq   *0x402470(,%rax,8)
   0x0000000000400f7c <+57>:	mov    $0xcf,%eax # number[0] = 0, number[1] = 0xcf = 207
   0x0000000000400f81 <+62>:	jmp    0x400fbe <phase_3+123>
   0x0000000000400f83 <+64>:	mov    $0x2c3,%eax # number[0] = 2, number[1] = 0x2c3 = 707
   0x0000000000400f88 <+69>:	jmp    0x400fbe <phase_3+123>
   0x0000000000400f8a <+71>:	mov    $0x100,%eax # number[0] = 3, number[1] = 0x100 = 256
   0x0000000000400f8f <+76>:	jmp    0x400fbe <phase_3+123>
   0x0000000000400f91 <+78>:	mov    $0x185,%eax # number[0] = 4, number[1] = 0x185 = 389
   0x0000000000400f96 <+83>:	jmp    0x400fbe <phase_3+123>
   0x0000000000400f98 <+85>:	mov    $0xce,%eax # number[0] = 5, number[1] = 0xce = 206
   0x0000000000400f9d <+90>:	jmp    0x400fbe <phase_3+123>
   0x0000000000400f9f <+92>:	mov    $0x2aa,%eax # number[0] = 6, number[1] = 0x2aa = 682
   0x0000000000400fa4 <+97>:	jmp    0x400fbe <phase_3+123>
   0x0000000000400fa6 <+99>:	mov    $0x147,%eax # number[0] = 7, number[1] = 0x147 = 327
   0x0000000000400fab <+104>:	jmp    0x400fbe <phase_3+123>
   0x0000000000400fad <+106>:	callq  0x40143a <explode_bomb>
   0x0000000000400fb2 <+111>:	mov    $0x0,%eax
   0x0000000000400fb7 <+116>:	jmp    0x400fbe <phase_3+123>
   0x0000000000400fb9 <+118>:	mov    $0x137,%eax # number[0] = 1, number[1] = 0x137 = 311
   0x0000000000400fbe <+123>:	cmp    0xc(%rsp),%eax
   0x0000000000400fc2 <+127>:	je     0x400fc9 <phase_3+134>
   0x0000000000400fc4 <+129>:	callq  0x40143a <explode_bomb>
   0x0000000000400fc9 <+134>:	add    $0x18,%rsp
   0x0000000000400fcd <+138>:	retq
   
   # Anser is "0 207" or "1 311" or "2 707" or "3 256" or "4 389" or "5 206" or "6 682" or "7 327" 
```

### *0x402470(,%rax,8)

```assembly
0x402470: 0x400f7c
0x402478: 0x400fb9
0x402480: 0x400f83
0x402488: 0x400f8a
0x402490: 0x400f91
0x402498: 0x400f98
0x4024a0: 0x400f9f
0x4024a8: 0x400fa6
```

