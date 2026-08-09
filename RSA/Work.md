# RSA(ASYMMETRIC CRYPTOGRAPHIC ALGORITHM)
- Rsa works on  MODULAR EXPONENTIATION
- it uses the idea of a trapdoor function
  <img width="852" height="277" alt="image" src="https://github.com/user-attachments/assets/fedcbbb0-20fb-49a2-b218-fb5b700ad0f4" />

- Plain text (M) must be smaller than modulus(N).
- Modulus N = p*q (P and Q are the primes)
- RSA Public key(N,e) . most common value of e - 65537.

## General notes
- Relatively prime(co primes) - GCD will be 1 for co primes.(That is given two numbers will be co primes if they have no common factor other than 1).
- Euler's totient(phi of N)- counts the no  positive integers from 1 to N , that are relatively prime to N.
<img width="832" height="60" alt="image" src="https://github.com/user-attachments/assets/89b67792-b732-4925-8622-3b14ec68bb16" />

<img width="841" height="439" alt="image" src="https://github.com/user-attachments/assets/7d3fcbd9-3180-4f0c-9a8c-d84c064d14ea" />


## Private key in Rsa
<img width="784" height="381" alt="image" src="https://github.com/user-attachments/assets/b94ef7a9-5096-4014-95eb-6a375b858909" />

## Encryption and Signing
<img width="919" height="326" alt="image" src="https://github.com/user-attachments/assets/b5e1a141-f8f7-4105-ad93-cfb592421b49" />
