# Trivial flag transfer protocol

*Flag:* picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}

How you approached the challenge:

- step 1: I opened the file in wireshark and exported it in tftp file because it saved itself as tftp.pcap when i downloaded the file and i saw that there were 7 files in that. 

![image](https://github.com/user-attachments/assets/84ea76f1-da4d-4c48-90ee-9437e60c1d32)


- step 2: So now i opened the instructions txt file and it gave a text which i put to a cipher identifier online and it said caesar cipher or also called as rot 13 so i went to rot 13 website and it said this
![image](https://github.com/user-attachments/assets/c5f4fed8-42ef-4cb4-93f9-b091a3c03e88)

-step 3: It clearly said to check for the plan so i went to plan file and again i there was some encrypted thing so i put in cipher identifier and it said caesar again and this time it said this
![image](https://github.com/user-attachments/assets/a9b924a4-a526-407c-8c31-e47704980cb1)

-step 4:It said to check out for the photos and so i knew something is hidden in photos so i opened all photos seemed normal and so i went to chatgpt and asked "how to access information from photos hidden with due dillengence in ctfs" and it said to use
exiftool image.jpg
or
steghide extract -sf image.jpg

-step 5: the first thing didnt help but the second command it asked me password and when i entered "DUEDILIGENCE" it worked but it said
```
steghide: could not extract any data with that passphrase!
```
when i tried the same for other photos and reached picture3.bmp Boom!! i said it "wrote extracted data to "flag.txt"."
![image](https://github.com/user-attachments/assets/f6b45eef-11b7-4709-bdba-0eac05b9194a)


-step 6: Then i did cat flag.txt
LESS GO!!!! i got the flag
![image](https://github.com/user-attachments/assets/fc396956-e663-4b26-ba82-e94d6e2d8a5a)

I LOVED THIS QUESTION IT WAS PLAYING TREASURE HUNT!!

What you learned through solving this challenge:

1. How to access hidden files.
2. Little more experience in WireShark.

Other incorrect methods you tried:

- Tried directly opening the file they had given.

References

- https://www.boxentriq.com/code-breaking/cipher-identifier
