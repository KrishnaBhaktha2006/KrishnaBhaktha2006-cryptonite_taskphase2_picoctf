# Custom encryption.md

*Flag:* picoCTF{custom_d2cr0pt6d_e4530597}

How you approached the challenge:

- step 1: Ye this question i opened the 2 files and i was like sigh this is a question where we have to make a decryption algorithm again this is because i was horrified btw the attempts 
i did while solving challenges in niteCTF and ok this question was very easier. So i saw there are 2 encrypt functions so i made 2 decrypt functions for them.

```
def encrypt(plaintext, key):
    cipher = []
    for char in plaintext:
        cipher.append(ord(char) * key * 311)
    return cipher


def decrypt(ciphertext, key):
    plain = []
    for bruh in ciphertext:
        plain.append(chr(int(bruh / key / 311)))
    return plain
```
So as u can see that The decryption algorithm is the same thing as encrypt just some variables are different. 

- step 2:
and there was the xor decrypt too

```
def dynamic_xor_encrypt(plaintext, text_key):
    cipher_text = ""
    key_length = len(text_key)
    for i, char in enumerate(plaintext[::-1]):
        key_char = text_key[i % key_length]
        encrypted_char = chr(ord(char) ^ ord(key_char))
        cipher_text += encrypted_char
    return cipher_text


def dynamic_xor_decrypt(ciphertext, text_key):
    plain_text = ""
    key_length = len(text_key)
    for i, char in enumerate(ciphertext):
        key_char = text_key[i % key_length]
        decrypted_char = chr(ord(char) ^ ord(key_char))
        plain_text += decrypted_char
    return plain_text
``` 
And ye this is also the same thing but with variables changed and the full program is

- step 3:
```
from random import randint
import sys


def generator(g, x, p):
    return pow(g, x) % p


def encrypt(plaintext, key):
    cipher = []
    for char in plaintext:
        cipher.append(ord(char) * key * 311)
    return cipher


def decrypt(ciphertext, key):
    plain = []
    for num in ciphertext:
        plain.append(chr(int(num / key / 311)))
    return plain


def is_prime(p):
    v = 0
    for i in range(2, p + 1):
        if p % i == 0:
            v = v + 1
    return v <= 1


def dynamic_xor_encrypt(plaintext, text_key):
    cipher_text = ""
    key_length = len(text_key)
    for i, char in enumerate(plaintext[::-1]):
        key_char = text_key[i % key_length]
        encrypted_char = chr(ord(char) ^ ord(key_char))
        cipher_text += encrypted_char
    return cipher_text


def dynamic_xor_decrypt(ciphertext, text_key):
    plain_text = ""
    key_length = len(text_key)
    for i, char in enumerate(ciphertext):
        key_char = text_key[i % key_length]
        decrypted_char = chr(ord(char) ^ ord(key_char))
        plain_text += decrypted_char
    return plain_text


def test(cipher_text, text_key):
    p = 97
    g = 31
    if not is_prime(p) or not is_prime(g):
        print("Enter prime numbers")
        return
    a = 97  
    b = 22  
    print(f"a = {a}")
    print(f"b = {b}")
    u = generator(g, a, p)  
    v = generator(g, b, p)  
    key = generator(v, a, p)  
    b_key = generator(u, b, p)  

    if key == b_key:
        print("Shared key established successfully!")
        shared_key = key
    else:
        print("Invalid key")
        return

    
    semi_cipher = decrypt(cipher_text, shared_key)
    plain = dynamic_xor_decrypt(semi_cipher, text_key)
    print(f'Plaintext is: {plain[::-1]}')


if __name__ == "__main__":
    message = [151146, 1158786, 1276344, 1360314, 1427490, 1377108, 1074816, 1074816, 386262, 705348, 0, 1393902, 352674, 83970, 1141992, 0, 369468, 1444284, 16794, 1041228, 403056, 453438, 100764, 100764, 285498, 100764, 436644, 856494, 537408, 822906, 436644, 117558, 201528, 285498]
    test(message, "trudeau")
```
And ye running this on visual studio code and boom! got the flag.

![WhatsApp Image 2024-12-22 at 18 42 20_1a3f089f](https://github.com/user-attachments/assets/5ca7ae48-542d-4be2-ad04-b10e8086d0cc)

What you learned through solving this challenge:

1. Learnt how to make a new decryption algorithm for questions.

Other incorrect methods you tried:

- I think while copying the code from terminal instead of __name__ it comes as _name_ i took some time to get that because i was like whats wrong with my code

References

- No reference
