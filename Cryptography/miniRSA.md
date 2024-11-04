# miniRSA

*Flag:* picoCTF{n33d_a_lArg3r_e_d0cd6eae}

How you approached the challenge:

- Step 1: Before actually satrting the cryptography section i had read the first two links and then started the question.So as soon as i saw the question title and the contents in the fiel ciphertext i came to know that this is a question uses rsa encryption.So i sent the three values given in the file to chtgpt to calculate the value of plaintext so chtgpt recommended me to find the cube root of the ciphertext.
so i searched for the code in python to find cube root of a large number in stack overflow i got the code.

```
def find_invpow(x,n):
    """Finds the integer component of the n'th root of x,
    an integer such that y ** n <= x < (y + 1) ** n.
    """
    high = 1
    while high ** n <= x:
        high *= 2
    low = high/2
    while low < high:
        mid = (low + high) // 2
        if low < mid and mid**n < x:
            low = mid
        elif high > mid and mid**n > x:
            high = mid
        else:
            return mid
    return mid + 1

print(find_invpower(2205316413931134031074603746928247799030155221252519872650080519263755075355825243327515211479747536697517688468095325517209911688684309894900992899707504087647575997847717180766377832435022794675332132906451858990782325436498952049751141,3))
```
on doing that i got an answer 13016382529449106065894479374027604750406953699090365388203722801043052339225981 after that when i put the number in chatgpt it said to use 
```
#Convert the integer to a byte string
plaintext_integer = 13016382529449106065894479374027604750406953699090365388203722801043052339225981
plaintext_bytes = plaintext_integer.to_bytes((plaintext_integer.bit_length() + 7) // 8, 'big')

# Decode the bytes to a string, assuming UTF-8 or ASCII encoding
plaintext_string = plaintext_bytes.decode('utf-8')
print(plaintext_string)
```
to get the decoded FLAG!!!

- step 2 : Here i will show the terminal commands i made use of 
i used the wget command to download the contents of the file
root@Krish:~# wget https://jupiter.challenges.picoctf.org/static/eb5e6df8e14c52873cf88c582a1a4008/ciphertext
--2024-11-04 23:01:29--  https://jupiter.challenges.picoctf.org/static/eb5e6df8e14c52873cf88c582a1a4008/ciphertext
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 884 [application/octet-stream]
Saving to: ‘ciphertext’

ciphertext                    100%[=================================================>]     884  --.-KB/s    in 0s

2024-11-04 23:01:30 (390 MB/s) - ‘ciphertext’ saved [884/884]
then used cat command to read the contents of file
root@Krish:~# cat ciphertext

N: 29331922499794985782735976045591164936683059380558950386560160105740343201513369939006307531165922708949619162698623675349030430859547825708994708321803705309459438099340427770580064400911431856656901982789948285309956111848686906152664473350940486507451771223435835260168971210087470894448460745593956840586530527915802541450092946574694809584880896601317519794442862977471129319781313161842056501715040555964011899589002863730868679527184420789010551475067862907739054966183120621407246398518098981106431219207697870293412176440482900183550467375190239898455201170831410460483829448603477361305838743852756938687673
e: 3

ciphertext (c): 2205316413931134031074603746928247799030155221252519872650080519263755075355825243327515211479747536697517688468095325517209911688684309894900992899707504087647575997847717180766377832435022794675332132906451858990782325436498952049751141

i even used the vi command which is a text editor to get the cube root of the ciphertext and to get the flag from the plaintext.
root@Krish:~# vi rsa.py
root@Krish:~# python3 rsa.py
13016382529449106065894479374027604750406953699090365388203722801043052339225981


root@Krish:~# vi plaintext.py
root@Krish:~# python3 plaintext.py
picoCTF{n33d_a_lArg3r_e_d0cd6eae}

What you learned through solving this challenge:

1. That if e value is small and c value is small then we can sometimes make the approximation pow(plaintext,3) = ciphertext
2. got an idea to approach question involving rsa encryption
3. to get the original message of plaintext u need to convert into to bytes and then those bytes into a string.

Other incorrect methods you tried:

- before using chatgpt for getting plaintext i tried to do calculation using calculator and all
- i tried to find e 

References

- https://stackoverflow.com/questions/356090/how-to-compute-the-nth-root-of-a-very-big-integer
- https://docs.python.org/3/library/stdtypes.html#int.bit_length
