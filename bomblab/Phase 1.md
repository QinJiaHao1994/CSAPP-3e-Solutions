## Analyse

### phase_1

```   assembly
   0x0000000000400ee0 <+0>:	sub    $0x8,%rsp
   0x0000000000400ee4 <+4>:	mov    $0x402400,%esi
   0x0000000000400ee9 <+9>:	callq  0x401338 <strings_not_equal>
   0x0000000000400eee <+14>:	test   %eax,%eax
   0x0000000000400ef0 <+16>:	je     0x400ef7 <phase_1+23>  # if eax = 0, defused.
   0x0000000000400ef2 <+18>:	callq  0x40143a <explode_bomb>
   0x0000000000400ef7 <+23>:	add    $0x8,%rsp
   0x0000000000400efb <+27>:	retq
```



### strings_not_equal:

  ``` assembly
   0x0000000000401338 <+0>:	push   %r12
   0x000000000040133a <+2>:	push   %rbp
   0x000000000040133b <+3>:	push   %rbx
   0x000000000040133c <+4>:	mov    %rdi,%rbx    # rbx = address of input
   0x000000000040133f <+7>:	mov    %rsi,%rbp    # rbp = 0x402400
   0x0000000000401342 <+10>:	callq  0x40131b <string_length>
   0x0000000000401347 <+15>:	mov    %eax,%r12d  # r12d = the length of input
   0x000000000040134a <+18>:	mov    %rbp,%rdi  # rdi = rsi = 0x402400
   0x000000000040134d <+21>:	callq  0x40131b <string_length> # rax = 52, length is 52
   0x0000000000401352 <+26>:	mov    $0x1,%edx
   0x0000000000401357 <+31>:	cmp    %eax,%r12d 
   0x000000000040135a <+34>:	jne    0x40139b <strings_not_equal+99> # if length isn't equal, boom 
   0x000000000040135c <+36>:	movzbl (%rbx),%eax # rax = input[0]
   0x000000000040135f <+39>:	test   %al,%al 
   0x0000000000401361 <+41>:	je     0x401388 <strings_not_equal+80> # impossible
   0x0000000000401363 <+43>:	cmp    0x0(%rbp),%al 
   0x0000000000401366 <+46>:	je     0x401372 <strings_not_equal+58> # if input[0] == 0x42, jmp
   0x0000000000401368 <+48>:	jmp    0x40138f <strings_not_equal+87> # else, boom
   0x000000000040136a <+50>:	cmp    0x0(%rbp),%al
   0x000000000040136d <+53>:	nopl   (%rax)
   0x0000000000401370 <+56>:	jne    0x401396 <strings_not_equal+94>
   0x0000000000401372 <+58>:	add    $0x1,%rbx 
   0x0000000000401376 <+62>:	add    $0x1,%rbp
   0x000000000040137a <+66>:	movzbl (%rbx),%eax # i++
   0x000000000040137d <+69>:	test   %al,%al
   0x000000000040137f <+71>:	jne    0x40136a <strings_not_equal+50> # compare input[i] and i(0x402400) until reach '\0', so the answer is "Border relations with Canada have never been better."
   0x0000000000401381 <+73>:	mov    $0x0,%edx
   0x0000000000401386 <+78>:	jmp    0x40139b <strings_not_equal+99>
   0x0000000000401388 <+80>:	mov    $0x0,%edx
   0x000000000040138d <+85>:	jmp    0x40139b <strings_not_equal+99>
   0x000000000040138f <+87>:	mov    $0x1,%edx
   0x0000000000401394 <+92>:	jmp    0x40139b <strings_not_equal+99>
   0x0000000000401396 <+94>:	mov    $0x1,%edx
   0x000000000040139b <+99>:	mov    %edx,%eax
   0x000000000040139d <+101>:	pop    %rbx
   0x000000000040139e <+102>:	pop    %rbp
   0x000000000040139f <+103>:	pop    %r12
   0x00000000004013a1 <+105>:	retq
  ```

### string_length

```assembly
	 0x000000000040131b <+0>:	cmpb   $0x0,(%rdi)
   0x000000000040131e <+3>:	je     0x401332 <string_length+23>
   0x0000000000401320 <+5>:	mov    %rdi,%rdx
   0x0000000000401323 <+8>:	add    $0x1,%rdx # rdx = 0x402401
   0x0000000000401327 <+12>:	mov    %edx,%eax # rax = 0x402401
   0x0000000000401329 <+14>:	sub    %edi,%eax # rax = 0x1
   0x000000000040132b <+16>:	cmpb   $0x0,(%rdx)
   0x000000000040132e <+19>:	jne    0x401323 <string_length+8>
   0x0000000000401330 <+21>:	repz retq
   0x0000000000401332 <+23>:	mov    $0x0,%eax
   0x0000000000401337 <+28>:	retq
```

