# RSA(ASYMMETRIC CRYPTOGRAPHIC ALGORITHM)
- Rsa works on  MODULAR EXPONENTIATION
- it uses the idea of a trapdoor function
  <img width="852" height="277" alt="image" src="https://github.com/user-attachments/assets/fedcbbb0-20fb-49a2-b218-fb5b700ad0f4" />

- Plain text (M) must be smaller than modulus(N).
- Modulus N = p*q (P and Q are the primes)
- RSA Public key(N,e) . most common value of e - 65537.

## General notes
- RSA with 2048 bit modulus is called RSA-2048.
- Some say that to really remain future-proof you should use RSA-4096 or even RSA-8192. However, there is a tradeoff here; it takes longer to generate large prime numbers, plus modular exponentiations are predictably slower with a large modulus.

- Relatively prime(co primes) - GCD will be 1 for co primes.(That is given two numbers will be co primes if they have no common factor other than 1).
- Euler's totient  $\phi(N)$. - counts the no  positive integers from 1 to N , that are relatively prime to N.
<img width="832" height="60" alt="image" src="https://github.com/user-attachments/assets/89b67792-b732-4925-8622-3b14ec68bb16" />

<img width="841" height="439" alt="image" src="https://github.com/user-attachments/assets/7d3fcbd9-3180-4f0c-9a8c-d84c064d14ea" />


## Private key in Rsa
<img width="784" height="381" alt="image" src="https://github.com/user-attachments/assets/b94ef7a9-5096-4014-95eb-6a375b858909" />

## Encryption and Signing
<img width="919" height="326" alt="image" src="https://github.com/user-attachments/assets/b5e1a141-f8f7-4105-ad93-cfb592421b49" />

```python
from Crypto.Util.number import bytes_to_long
import hashlib

N = 15216583654836731327639981224133918855895948374072384050848479908982286890731769486609085918857664046075375253168955058743185664390273058074450390236774324903305663479046566232967297765731625328029814055635316002591227570271271445226094919864475407884459980489638001092788574811554149774028950310695112688723853763743238753349782508121985338746755237819373178699343135091783992299561827389745132880022259873387524273298850340648779897909381979714026837172003953221052431217940632552930880000919436507245150726543040714721553361063311954285289857582079880295199632757829525723874753306371990452491305564061051059885803
d = 11175901210643014262548222473449533091378848269490518850474399681690547281665059317155831692300453197335735728459259392366823302405685389586883670043744683993709123180805154631088513521456979317628012721881537154107239389466063136007337120599915456659758559300673444689263854921332185562706707573660658164991098457874495054854491474065039621922972671588299315846306069845169959451250821044417886630346229021305410340100401530146135418806544340908355106582089082980533651095594192031411679866134256418292249592135441145384466261279428795408721990564658703903787956958168449841491667690491585550160457893350536334242689



msg = b"crypto{Immut4ble_m3ssag1ng}"


hashed_msg= hashlib.sha256(msg).digest()
hm = bytes_to_long(hashed_msg)
signature = pow(hm,d,N)
print(signature)
```
- We need to bytes_to_long becuase hashing produces bytes, while RSA requires integers.
- We use the concept of signature to make sure the message is from the original person itself since only they have the private key, and we use public key to decrypt and get the original message

# Theory
- The entire security of the RSA cryptosystem relies on the mathematical difficulty of factoring a large number into its constituent primes. This creates a "trapdoor"—easy to compute in one direction, but practically impossible to reverse without a secret piece of information.
- To generate the private decryption key ($d$), you need to calculate Euler's totient function, $\phi(N)$. For the product of two primes, this $\phi(N)$ = (p-1) * (q-1).
- There exist a vulnerability in RSA if Modulus N is a monoprime. It becomes easy to calculate the private key from the equation:
<img width="501" height="85" alt="image" src="https://github.com/user-attachments/assets/39ce7673-69fa-4837-8ce6-dabf3a07d97c" />
- Because Euler's totient
<img width="501" height="85" alt="image" src="https://github.com/user-attachments/assets/aaaf1e84-d081-40bc-969a-321a83c86644" />

