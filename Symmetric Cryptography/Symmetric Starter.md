# 1. Understand how the website works and how it can be used

- First get the encrypted flag, decrypt it and finally decode it.


### Theory
- Symmetric encryption algorithms like AES  require keys of specific length(16,24,32 bytes). For maximum security , these bytes are generated using Cryptographically secure psuedo random number generator.(CSPRNG)
- Hashing is an IRREVERSIBLE process
- 
# 2 .

We are Brute-forcing to find the flag.
- The flag is encrypted using a hashed word (key).
- we need to find the key and the flag.
- From the wordlist provided, we are hashing all of them and checking to see if we get a readable flag after decryption.

Code:
``` python
import requests
import hashlib
from Crypto.Cipher import AES

ciphertext_hex = "c92b7734070205bdf6c0087a751466ec13ae15e6f1bcdd3f3a535ec0f4bbae66"
ciphertext = bytes.fromhex(ciphertext_hex)

url = "https://gist.githubusercontent.com/wchargin/8927565/raw/d9783627c731268fb2935a731a618aa8e95cf465/words"
response = requests.get(url)
words = response.text.splitlines()

for word in words:
    key = hashlib.md5(word.encode()).digest()
    cipher = AES.new(key, AES.MODE_ECB)
    
    try:
        decrypted = cipher.decrypt(ciphertext)
        
        if b"crypto{" in decrypted:
            print("keyword",word)
            print("FLag",decrypted.decode('utf-8', errors='ignore').strip())
            break
            
    except Exception as e:
        pass
```
Flag - crypto{k3y5__r__n07__p455w0rdz?}
