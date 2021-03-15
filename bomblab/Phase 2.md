## Analyse

### phase_2

```assembly
   0x0000000000400efc <+0>:	push   %rbp
   0x0000000000400efd <+1>:	push   %rbx
   0x0000000000400efe <+2>:	sub    $0x28,%rsp
   0x0000000000400f02 <+6>:	mov    %rsp,%rsi
   0x0000000000400f05 <+9>:	callq  0x40145c <read_six_numbers> # rdi = &input, rsi = phase2_rsp
   0x0000000000400f0a <+14>:	cmpl   $0x1,(%rsp) # number0 == 1
   0x0000000000400f0e <+18>:	je     0x400f30 <phase_2+52>
   0x0000000000400f10 <+20>:	callq  0x40143a <explode_bomb>
   0x0000000000400f15 <+25>:	jmp    0x400f30 <phase_2+52>
   0x0000000000400f17 <+27>:	mov    -0x4(%rbx),%eax # eax = number[i-1]
   0x0000000000400f1a <+30>:	add    %eax,%eax # eax = 2 * number[i-1]
   0x0000000000400f1c <+32>:	cmp    %eax,(%rbx) # number[i] == 2 * number[i-1]
   0x0000000000400f1e <+34>:	je     0x400f25 <phase_2+41>
   0x0000000000400f20 <+36>:	callq  0x40143a <explode_bomb>
   0x0000000000400f25 <+41>:	add    $0x4,%rbx 
   0x0000000000400f29 <+45>:	cmp    %rbp,%rbx 
   0x0000000000400f2c <+48>:	jne    0x400f17 <phase_2+27> # loop 6 numbers, number[i] = 2 * number [i-1], number[0] = 1; the answer is "1 2 4 8 16 32"
   0x0000000000400f2e <+50>:	jmp    0x400f3c <phase_2+64>
   0x0000000000400f30 <+52>:	lea    0x4(%rsp),%rbx # rbx = 0x4 + rsp
   0x0000000000400f35 <+57>:	lea    0x18(%rsp),%rbp # rbp = 0x18 + rsp
   0x0000000000400f3a <+62>:	jmp    0x400f17 <phase_2+27>
   0x0000000000400f3c <+64>:	add    $0x28,%rsp
   0x0000000000400f40 <+68>:	pop    %rbx
   0x0000000000400f41 <+69>:	pop    %rbp
   0x0000000000400f42 <+70>:	retq
```

### read_six_numbers

#### read 6 numbers, separate by " "

```assembly
   0x000000000040145c <+0>:	sub    $0x18,%rsp
   0x0000000000401460 <+4>:	mov    %rsi,%rdx # rdx = phase2_rsp;
   0x0000000000401463 <+7>:	lea    0x4(%rsi),%rcx # rcx = phase2_rsp + 0x4;
   0x0000000000401467 <+11>:	lea    0x14(%rsi),%rax # rax = phase2_rsp + 0x14;
   0x000000000040146b <+15>:	mov    %rax,0x8(%rsp) # 0x8(rsp) = phase2_rsp + 0x14;
   0x0000000000401470 <+20>:	lea    0x10(%rsi),%rax # rax = phase2_rsp + 0x10;
   0x0000000000401474 <+24>:	mov    %rax,(%rsp) # (rsp) = phase2_rsp + 0x10;
   0x0000000000401478 <+28>:	lea    0xc(%rsi),%r9 # r9 = phase2_rsp + 0xc;
   0x000000000040147c <+32>:	lea    0x8(%rsi),%r8 # r8 = phase2_rsp + 0x8;
   0x0000000000401480 <+36>:	mov    $0x4025c3,%esi #"%d %d %d %d %d %d"
   0x0000000000401485 <+41>:	mov    $0x0,%eax
   0x000000000040148a <+46>:	callq  0x400bf0 <__isoc99_sscanf@plt> # sscanf(%rdi, %rsi, %rdx, %rcx, %r8, %r9, (rsp), 0x8(rsp));
   0x000000000040148f <+51>:	cmp    $0x5,%eax
   0x0000000000401492 <+54>:	jg     0x401499 <read_six_numbers+61> # return value > 5, continue, else bomb.
   0x0000000000401494 <+56>:	callq  0x40143a <explode_bomb>
   0x0000000000401499 <+61>:	add    $0x18,%rsp
   0x000000000040149d <+65>:	retq
```

