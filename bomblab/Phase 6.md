## Analyse

### phase_6

```assembly
   0x00000000004010f4 <+0>:	push   %r14
   0x00000000004010f6 <+2>:	push   %r13
   0x00000000004010f8 <+4>:	push   %r12
   0x00000000004010fa <+6>:	push   %rbp
   0x00000000004010fb <+7>:	push   %rbx
   0x00000000004010fc <+8>:	sub    $0x50,%rsp
   0x0000000000401100 <+12>:	mov    %rsp,%r13 # r13 = rsp
   0x0000000000401103 <+15>:	mov    %rsp,%rsi
   0x0000000000401106 <+18>:	callq  0x40145c <read_six_numbers>
   0x000000000040110b <+23>:	mov    %rsp,%r14 # r14 = rsp
   0x000000000040110e <+26>:	mov    $0x0,%r12d # r12 = 0
   0x0000000000401114 <+32>:	mov    %r13,%rbp # rbp = rsp
   0x0000000000401117 <+35>:	mov    0x0(%r13),%eax # rax = rsp[i]
   0x000000000040111b <+39>:	sub    $0x1,%eax # rax = rsp[i] - 1
   0x000000000040111e <+42>:	cmp    $0x5,%eax
   0x0000000000401121 <+45>:	jbe    0x401128 <phase_6+52> # 0 <= rax <= 5; 1 <= rsp[i] <= 6;
   0x0000000000401123 <+47>:	callq  0x40143a <explode_bomb>
   0x0000000000401128 <+52>:	add    $0x1,%r12d # i = r12 += 1
   0x000000000040112c <+56>:	cmp    $0x6,%r12d 
   0x0000000000401130 <+60>:	je     0x401153 <phase_6+95> # if r12 == 6; jmp
   0x0000000000401132 <+62>:	mov    %r12d,%ebx # rbx = r12 = i
   0x0000000000401135 <+65>:	movslq %ebx,%rax # rax = rbx = j = i
   0x0000000000401138 <+68>:	mov    (%rsp,%rax,4),%eax # rax = rsp[j]
   0x000000000040113b <+71>:	cmp    %eax,0x0(%rbp) 
   0x000000000040113e <+74>:	jne    0x401145 <phase_6+81> # rsp[j] != rsp[i]
   0x0000000000401140 <+76>:	callq  0x40143a <explode_bomb>
   0x0000000000401145 <+81>:	add    $0x1,%ebx # rbx = j = i + 1
   0x0000000000401148 <+84>:	cmp    $0x5,%ebx 
   0x000000000040114b <+87>:	jle    0x401135 <phase_6+65>
   0x000000000040114d <+89>:	add    $0x4,%r13 # r13 = rsp + 4
   0x0000000000401151 <+93>:	jmp    0x401114 <phase_6+32> # each num [1,6], and each num different. 
   0x0000000000401153 <+95>:	lea    0x18(%rsp),%rsi # rsi = rsp + 0x18
   0x0000000000401158 <+100>:	mov    %r14,%rax # rax = rsp
   0x000000000040115b <+103>:	mov    $0x7,%ecx # rcx = 7
   0x0000000000401160 <+108>:	mov    %ecx,%edx # rdx = rcx = 7
   0x0000000000401162 <+110>:	sub    (%rax),%edx # rdx = 7 - rsp[0]
   0x0000000000401164 <+112>:	mov    %edx,(%rax) # rsp[0] = 7 - rsp[0]
   0x0000000000401166 <+114>:	add    $0x4,%rax # rax = rsp + 4
   0x000000000040116a <+118>:	cmp    %rsi,%rax
   0x000000000040116d <+121>:	jne    0x401160 <phase_6+108> # each num = 7 - num
   
   # (rsp+0x20+k*8) store a point to a node of linkedlist
   0x000000000040116f <+123>:	mov    $0x0,%esi # rsi = 0
   0x0000000000401174 <+128>:	jmp    0x401197 <phase_6+163>
   0x0000000000401176 <+130>:	mov    0x8(%rdx),%rdx # rdx = (0x6032d0 + 0x8)
   0x000000000040117a <+134>:	add    $0x1,%eax # rax += 1
   0x000000000040117d <+137>:	cmp    %ecx,%eax 
   0x000000000040117f <+139>:	jne    0x401176 <phase_6+130> # if rsp[k] != rax, rax++; rdx = (rdx + 0x8);
   0x0000000000401181 <+141>:	jmp    0x401188 <phase_6+148> # if rsp[k] == rax, (rsp+0x20+k*8) = rdx;
   0x0000000000401183 <+143>:	mov    $0x6032d0,%edx 
   0x0000000000401188 <+148>:	mov    %rdx,0x20(%rsp,%rsi,2) # (rsp + 0x20 + k * 8) = 0x6032d0
   0x000000000040118d <+153>:	add    $0x4,%rsi # rsi = 4;
   0x0000000000401191 <+157>:	cmp    $0x18,%rsi
   0x0000000000401195 <+161>:	je     0x4011ab <phase_6+183>
   0x0000000000401197 <+163>:	mov    (%rsp,%rsi,1),%ecx # rcx = rsp[k]
   0x000000000040119a <+166>:	cmp    $0x1,%ecx 
   0x000000000040119d <+169>:	jle    0x401183 <phase_6+143> # if rsp[k] <= 1, (rsp + 0x20 + k * 8) = 0x6032d0
   0x000000000040119f <+171>:	mov    $0x1,%eax # rax = 1
   0x00000000004011a4 <+176>:	mov    $0x6032d0,%edx # rdx = 0x6032d0
   0x00000000004011a9 <+181>:	jmp    0x401176 <phase_6+130>
   
   # arrange linkedlist
   0x00000000004011ab <+183>:	mov    0x20(%rsp),%rbx # rbx = (rsp + 0x20)
   0x00000000004011b0 <+188>:	lea    0x28(%rsp),%rax # rax = rsp + 0x28
   0x00000000004011b5 <+193>:	lea    0x50(%rsp),%rsi # rsi = rsp + 0x50
   0x00000000004011ba <+198>:	mov    %rbx,%rcx # rcx = (rsp + 0x20)
   0x00000000004011bd <+201>:	mov    (%rax),%rdx # rdx = (rsp + 0x28)
   0x00000000004011c0 <+204>:	mov    %rdx,0x8(%rcx) # (0x8 + (rsp + 0x20)) = (rsp + 0x28)
   0x00000000004011c4 <+208>:	add    $0x8,%rax # rax += 0x8
   0x00000000004011c8 <+212>:	cmp    %rsi,%rax
   0x00000000004011cb <+215>:	je     0x4011d2 <phase_6+222> # loop, jmp if rax = rsp + 0x50
   0x00000000004011cd <+217>:	mov    %rdx,%rcx # rcx = (rsp + 0x28)
   0x00000000004011d0 <+220>:	jmp    0x4011bd <phase_6+201>
   
   
   0x00000000004011d2 <+222>:	movq   $0x0,0x8(%rdx) # (rsp + 0x50) = 0
   0x00000000004011da <+230>:	mov    $0x5,%ebp # rbp = 5
   0x00000000004011df <+235>:	mov    0x8(%rbx),%rax # rax = ((rsp + 0x20) + 0x8)
   0x00000000004011e3 <+239>:	mov    (%rax),%eax # rax = list1.val
   0x00000000004011e5 <+241>:	cmp    %eax,(%rbx) 
   0x00000000004011e7 <+243>:	jge    0x4011ee <phase_6+250> # list0.val >= list1.val >= list2.val ...
   0x00000000004011e9 <+245>:	callq  0x40143a <explode_bomb>
   0x00000000004011ee <+250>:	mov    0x8(%rbx),%rbx
   0x00000000004011f2 <+254>:	sub    $0x1,%ebp
   0x00000000004011f5 <+257>:	jne    0x4011df <phase_6+235>
   0x00000000004011f7 <+259>:	add    $0x50,%rsp
   0x00000000004011fb <+263>:	pop    %rbx
   0x00000000004011fc <+264>:	pop    %rbp
   0x00000000004011fd <+265>:	pop    %r12
   0x00000000004011ff <+267>:	pop    %r13
   0x0000000000401201 <+269>:	pop    %r14
   0x0000000000401203 <+271>:	retq
   
   # Answer is "4 3 2 1 6 5"
```

| index | address  | value | next     |
| ----- | -------- | ----- | -------- |
| 0     | 0x6032d0 | 332   | 0x6032e0 |
| 1     | 0x6032e0 | 168   | 0x6032f0 |
| 2     | 0x6032f0 | 924   | 0x603300 |
| 3     | 0x603300 | 691   | 0x603310 |
| 4     | 0x603310 | 477   | 0x603320 |
| 5     | 0x603320 | 443   |          |

