# shark on wire 1

*Flag:* picoCTF{StaT31355_636f6e6e}

How you approached the challenge:

- step 1: So for this challenge we know that there are many protocols such as ssdp,udp,tcp etc... so first according to hints i searched up for streams in wireshark on google and 
And realised that we can follow protocol streams so i clicked on tcp and followed it but in all the 10 streams nothing was written and couldnt follow the arp streams but when i folllowed the udp streams and opened the 6th stream i got the flag!!
![image](https://github.com/user-attachments/assets/7c52a1ae-37f5-40b6-8c5e-497522e2ece0)

What you learned through solving this challenge:

1. How to follow streams
2. Different types of protocols

Other incorrect methods you tried:

- No incorrect methods tried

References

- https://www.wireshark.org/docs/wsug_html_chunked/ChAdvFollowStreamSection.html
