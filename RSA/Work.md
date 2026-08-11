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


- Because Euler's totient becomes

<img width="501" height="85" alt="image" src="https://github.com/user-attachments/assets/aaaf1e84-d081-40bc-969a-321a83c86644" />

## More about N

<img width="785" height="322" alt="image" src="https://github.com/user-attachments/assets/950f6002-d30a-4f9c-a87e-dd432f97682f" />


<img width="755" height="487" alt="image" src="https://github.com/user-attachments/assets/cfb45afe-3d1f-4ddc-a443-76ee613b38b3" />

<img width="750" height="155" alt="image" src="https://github.com/user-attachments/assets/1228cf5c-89b7-41f7-a819-95a34149dadd" />


- In rsa usually n has two factors , but in case n hase multiple factors, we calculate euler's totient this way
-
- <img width="704" height="155" alt="image" src="https://github.com/user-attachments/assets/2b7a075c-ad39-474b-a5b9-fec8e8068dba" />

Code for multiple factors, used factordb to get the factors of N
```python
from Crypto.Util.number import long_to_bytes
primes =[9282105380008121879,9303850685953812323,9389357739583927789,10336650220878499841,10638241655447339831,11282698189561966721,11328768673634243077,11403460639036243901,11473665579512371723,11492065299277279799,11530534813954192171,11665347949879312361,12132158321859677597,12834461276877415051,12955403765595949597,12973972336777979701,13099895578757581201,13572286589428162097,14100640260554622013,14178869592193599187,14278240802299816541,14523070016044624039,14963354250199553339,15364597561881860737,15669758663523555763,15824122791679574573,15998365463074268941,16656402470578844539,16898740504023346457,17138336856793050757,17174065872156629921,17281246625998849649]

n = 580642391898843192929563856870897799650883152718761762932292482252152591279871421569162037190419036435041797739880389529593674485555792234900969402019055601781662044515999210032698275981631376651117318677368742867687180140048715627160641771118040372573575479330830092989800730105573700557717146251860588802509310534792310748898504394966263819959963273509119791037525504422606634640173277598774814099540555569257179715908642917355365791447508751401889724095964924513196281345665480688029639999472649549163147599540142367575413885729653166517595719991872223011969856259344396899748662101941230745601719730556631637

p = 1
for i in primes:
    p = p*(i-1)

e = 65537
ct = 320721490534624434149993723527322977960556510750628354856260732098109692581338409999983376131354918370047625150454728718467998870322344980985635149656977787964380651868131740312053755501594999166365821315043312308622388016666802478485476059625888033017198083472976011719998333985531756978678758897472845358167730221506573817798467100023754709109274265835201757369829744113233607359526441007577850111228850004361838028842815813724076511058179239339760639518034583306154826603816927757236549096339501503316601078891287408682099750164720032975016814187899399273719181407940397071512493967454225665490162619270814464

d = pow(e,-1,p)
print(long_to_bytes(pow(ct,d,n)))
```

## When e is small

<img width="763" height="762" alt="image" src="https://github.com/user-attachments/assets/97ca7c49-a95d-4463-a9be-3cd6a3b668b8" />

when e is small, the plain text doesn't change because it is smaller than n so it doesn't wrap around it.

## How to find roots of large integers in python

<img width="717" height="30" alt="image" src="https://github.com/user-attachments/assets/ffc22ccf-9bb6-49f3-b0c5-31848a4c2eb9" />

use gmpy2 , it returns a tuple which contains the root value and a boolean showing whether the root was exact.


## More NOTES

<img width="1037" height="328" alt="image" src="https://github.com/user-attachments/assets/90a134f5-b510-4ffc-aa61-c630a8bb3d32" />

<img width="1002" height="399" alt="image" src="https://github.com/user-attachments/assets/102215d2-cbd1-4902-9413-5bfe3a5207e9" />

<img width="756" height="280" alt="image" src="https://github.com/user-attachments/assets/6339b68c-d764-4545-9f72-70b7c4388cc0" />

## Simple(imp) Concept

- When you are working in a finite field $\mathbb{F}_p$ (which just means modular arithmetic with a prime modulus $p$), you are restricted to the numbers from $1$ to $p-1$.

<img width="766" height="261" alt="image" src="https://github.com/user-attachments/assets/0cb733b0-ca79-4e81-9b56-4dfa1a7a708f" />

for an equation

<img width="310" height="46" alt="image" src="https://github.com/user-attachments/assets/d236b50c-fb2b-4195-9e5e-ddc0effc7aed" />

we use fermats little theorm to solve it
