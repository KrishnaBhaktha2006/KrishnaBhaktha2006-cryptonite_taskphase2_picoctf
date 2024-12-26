# b00tl3gRSA3

*Flag:* picoCTF{too_many_fact0rs_4025135}

How you approached the challenge:

- step 1: This was a heck of a Question and took me so much time and sucked the whole energy out of me.Well this is normal rsa but with many p and q so i went to a factor calculator to get the factors of n.

![image](https://github.com/user-attachments/assets/4968b357-c7d0-4e02-b762-91f5beb0572a)

Then i wanted a modinv function in python like in code so i searched for it and refered stackoverflow

Then since we know factors and if reduce the last digit by 1 we can can phi and and get lambda and from there get d and we know e,c,n and d so we get m and so we get the flag!!

```
def egcd(a, b):
    if a == 0:
        return (b, 0, 1)
    else:
        g, y, x = egcd(b % a, a)
        return (g, x - (b // a) * y, y)

def modinv(a, m):
    g, x, y = egcd(a, m)
    if g != 1:
        raise Exception('modular inverse does not exist')
    else:
        return x % m

n=1152161961952280455708561918838153640718922268137072963058306595885196482412302684106039477338494880761302319275222
306907649554663465907466806797850356971843829270543201762433600957653085387238119674342704399489684467855848161719388
67856677295745824193370221689045737093016427767489940684053720403056902270627186322163474496418384019726869649893
phi=8995675300*9345347386*9509285748*9524193240*10851531400*11537259652*11937659380*12127452670*12205591996*
12238496242*12386371272*12649030230*13110549138*13204271986*13311449998*13373796412*13522884558*13591845610*
13624244686*13961218318*14036304432*14108289160*14254720552*14485685742*14793322960*14925487656*14982919848*
15159137532*15275670198*15570037866*15670931592*16141001518*16152481002*16614756492
c=6690986590141316616992685072074090428241602859544836568957340485582103362583268980968379536133417819022474232827878
255483640493276565634612412697500659981519117949829850937380079269184263244714921895715905357100583742194867849181689
1659593912780928572063508779250188093833824540380377459863826667259175387349973423617885074219221223697262223834
e=65537
d=modinv(e,phi)
plain=pow(c,d,n)
print(hex(plain))
``` 
```
root@Krish:~# python3 script.py
0x7069636f4354467b746f6f5f6d616e795f666163743072735f343032353133357d
```
And then put this in hex converter and u get the flag!

![image](https://github.com/user-attachments/assets/6e933359-f2fa-435e-a405-490e953ebcc2)

What you learned through solving this challenge:

1. Solving Rsa Questions when there are many factors.

Other incorrect methods you tried:

- I tried to manually calculate lamda or d and all but it was hard and it didnt work also

References

- https://www.alpertron.com.ar/ECM.HTM
- https://www.rapidtables.com/convert/number/hex-to-ascii.html
- https://stackoverflow.com/questions/4798654/modular-multiplicative-inverse-function-in-python
