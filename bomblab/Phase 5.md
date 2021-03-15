## Analyse

### phase_5

```assembly
   0x0000000000401062 <+0>:	push   %rbx
   0x0000000000401063 <+1>:	sub    $0x20,%rsp
   0x0000000000401067 <+5>:	mov    %rdi,%rbx
   0x000000000040106a <+8>:	mov    %fs:0x28,%rax
   0x0000000000401073 <+17>:	mov    %rax,0x18(%rsp)
   0x0000000000401078 <+22>:	xor    %eax,%eax
   0x000000000040107a <+24>:	callq  0x40131b <string_length>
   0x000000000040107f <+29>:	cmp    $0x6,%eax
   0x0000000000401082 <+32>:	je     0x4010d2 <phase_5+112> # length = 6
   0x0000000000401084 <+34>:	callq  0x40143a <explode_bomb>
   0x0000000000401089 <+39>:	jmp    0x4010d2 <phase_5+112>
   0x000000000040108b <+41>:	movzbl (%rbx,%rax,1),%ecx # ecx = (%rbx) = input[0]
   0x000000000040108f <+45>:	mov    %cl,(%rsp) # rsp[0] = input[0]
   0x0000000000401092 <+48>:	mov    (%rsp),%rdx # rdx = input[0]
   0x0000000000401096 <+52>:	and    $0xf,%edx # rdx = low 4 bits of input[0]
   0x0000000000401099 <+55>:	movzbl 0x4024b0(%rdx),%edx # dl = "maduiersnfotvbyl"[rdx]
   0x00000000004010a0 <+62>:	mov    %dl,0x10(%rsp,%rax,1) # rsp[0x10] = "maduiersnfotvbyl"[rdx]
   0x00000000004010a4 <+66>:	add    $0x1,%rax # rax++
   0x00000000004010a8 <+70>:	cmp    $0x6,%rax 
   0x00000000004010ac <+74>:	jne    0x40108b <phase_5+41> # if rax != 6, jmp, input_low_4_bits =[9, 15, 14, 5, 6, 7], answer should add high_4_bits to make characters visible.
   0x00000000004010ae <+76>:	movb   $0x0,0x16(%rsp) # rsp[0x16] = '\0'
   0x00000000004010b3 <+81>:	mov    $0x40245e,%esi # "flyers"
   0x00000000004010b8 <+86>:	lea    0x10(%rsp),%rdi # rdi = rsp[0x10]
   0x00000000004010bd <+91>:	callq  0x401338 <strings_not_equal>
   0x00000000004010c2 <+96>:	test   %eax,%eax
   0x00000000004010c4 <+98>:	je     0x4010d9 <phase_5+119>
   0x00000000004010c6 <+100>:	callq  0x40143a <explode_bomb>
   0x00000000004010cb <+105>:	nopl   0x0(%rax,%rax,1)
   0x00000000004010d0 <+110>:	jmp    0x4010d9 <phase_5+119>
   0x00000000004010d2 <+112>:	mov    $0x0,%eax
   0x00000000004010d7 <+117>:	jmp    0x40108b <phase_5+41>
   0x00000000004010d9 <+119>:	mov    0x18(%rsp),%rax
   0x00000000004010de <+124>:	xor    %fs:0x28,%rax
   0x00000000004010e7 <+133>:	je     0x4010ee <phase_5+140>
   0x00000000004010e9 <+135>:	callq  0x400b30 <__stack_chk_fail@plt>
   0x00000000004010ee <+140>:	add    $0x20,%rsp
   0x00000000004010f2 <+144>:	pop    %rbx
   0x00000000004010f3 <+145>:	retq
```

