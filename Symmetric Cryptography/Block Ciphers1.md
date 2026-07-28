# ECB ORACLE ATTACK (ECB -byte-at-a-time Decryption)  

Vulnerability - encrypts identical plainttext blocks to identical ciphertext blocks.(AES.MODE_ECB)--> (DOESNNOT USE INITIALIZATION VECTOR - to randomize block)

<img width="894" height="506" alt="image" src="https://github.com/user-attachments/assets/9fefa469-3835-4f11-8b97-c52ffe8b840b" />

From the code , we see that the plaintext is added directly infront of the flag  and split into 16 byte blocks and encrypted.
