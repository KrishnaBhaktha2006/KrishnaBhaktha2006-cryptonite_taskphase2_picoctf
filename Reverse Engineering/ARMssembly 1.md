# ARMssembly 1 

*Flag:* picoCTF{000000e8}

How you approached the challenge:

- step 1: Actually i Refered a link provided in pdf which i will mention in reference to get basics after that when i read the program step by step i got the flag!!!
- step 2:
```
str	w0, [sp, 12]
mov	w0, 87
str	w0, [sp, 16]
mov	w0, 3
str	w0, [sp, 20]
mov	w0, 3
str	w0, [sp, 24]
```
from this we can say that w0(1) = 87,w0(2) = 3, w0(3) = 3
and later w0 = 3 and w1 = 87
```
ldr	w0, [sp, 20]
	ldr	w1, [sp, 16]
	lsl	w0, w1, w0
	str	w0, [sp, 28]
```
When i read hint it said shift so i thought this might be bitwise shift
now acc to this code we did left shift of w1 w0 times and stored it in w0 which is in turn stored in sp+28 posiition
87 shifted to left 3 times gives 696
```
ldr	w1, [sp, 28]
	ldr	w0, [sp, 24]
	sdiv	w0, w1, w0
	str	w0, [sp, 28]
``` 
now they divided to get 696/3 = 232

```
ldr	w1, [sp, 28]
	ldr	w0, [sp, 12]
	sub	w0, w1, w0
```
Now we shoulg subtract
so the func returns 232-87 = 145

```
cmp	w0, 0
	bne	.L4
	adrp	x0, .LC0
```
he it compares and says if 0 == returned stuff then it will go to .LC0 and in LC0 we have you win
but we didnt get it
so to obtain 0 we need to subtract 232 from 232 therefor answer is 232 convert it in required format and enclosing it in picoCTF will give me the answer.
terminal output

What you learned through solving this challenge:

1. Experience of Tracing a ARMassembly code

Other incorrect methods you tried:

- I thought the answer was 145 and it didnt work so when i saw question again i understood we had to print the stuff that would make us go to .LC0 and not the output of program
  
References

- https://www.youtube.com/watch?v=1d-6Hv1c39c
