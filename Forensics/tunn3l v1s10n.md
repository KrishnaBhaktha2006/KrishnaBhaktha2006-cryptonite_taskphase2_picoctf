# tunn3l v1s10n

*Flag:* picoCTF{qu1t3_a_v13w_2020}

How you approached the challenge:

- step 1: Today we had cryptonite offline meeting in that they talked about headers.
So i downloaded a random sample bmp file in hxd hex editor and compared the header values and i realised that the file given to us had bad written in them so i changed only that part of it with the sample bmp file
code and ye i got the new file i renamed it as .bmp because when i put the header in chatgpt it said its bmp file but i noticed when i eoged the file that the height was fine but width wasnt fine so i clicked properties.


- step 2: when i check the height was like 306 so i opened python3 in terminal

![WhatsApp Image 2024-11-09 at 23 43 23_3ca35dcb](https://github.com/user-attachments/assets/2f1a8e23-9c83-4041-a928-14cd99a964f1)


so from seeing that and comparing hex value i understood it is entered as 32 01 so i searched up 800 and changed in hex but couldnt see and when i tried 825 i got the flag

![image](https://github.com/user-attachments/assets/0d6c4e58-a4d3-4db2-90f5-095a051a7cfc)

What you learned through solving this challenge:

1. about headers
2. changing height and width using hxd hex editor
3. kind of an idea of how files hex codes work

Other incorrect methods you tried:

- tried catting file

References

- https://filesamples.com/formats/bmp
