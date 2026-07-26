# Quadratic residue - perfect square

## equation [ a**2 = x mod (y) ]

 <img width="690" height="49" alt="image" src="https://github.com/user-attachments/assets/bb6c929b-66a3-4916-b8e4-6797e1412e87" />



- a is the number from 0 to y-1 and if any of those numbers after equating  equals to x, x is a quadratic residue. and its square root is a.



<img width="1013" height="112" alt="image" src="https://github.com/user-attachments/assets/82b7b45e-c509-4ba6-9de5-151eeef92700" />
<img width="1080" height="242" alt="image" src="https://github.com/user-attachments/assets/4f307cc7-4f39-4d0c-8bf4-0c80791e2f16" />
# Eulers Criterion
- 

<img width="464" height="98" alt="image" src="https://github.com/user-attachments/assets/aff611ee-a73b-4578-8df3-8204e381d885" />
- This works only if the exponent (P+1)/4 is an integer

### Code
```python
a = [14,6,11]
count =0
for x in a:
    for i in range(29):
        if (i**2)%29 == x:
            print (i,x)
            break
```
### Output

<img width="757" height="36" alt="image" src="https://github.com/user-attachments/assets/5b653d6c-99fd-46f1-bfab-151ebc453197" />


--- 

# Congruence

<img width="862" height="587" alt="image" src="https://github.com/user-attachments/assets/0d004cef-b062-406b-8250-abe171f76afc" />
<img width="827" height="350" alt="image" src="https://github.com/user-attachments/assets/03996e87-ee46-4b86-b013-2f9bbd588186" />


We can say 40 and 16 are congruent since they both leave the same remainder(residue) after division by 3 (moduluo 3)

---

# Tonelli-Shanks Algorithm

- While we use derivations from fermats little theorm to find sqaure roots of quadratic residue of the form p = 3 (mod 4)
- we have to use tonelli's algorithm to find square roots for equations of the form p = 1 (mod 4)
- Note - these are only possible if p is a prime number
  
### Code
<img width="689" height="122" alt="image" src="https://github.com/user-attachments/assets/731e9d8a-c294-431e-a9b7-3cae526c17ae" />
---

# Chinese remainder theorm

- Used when problems that have  very large numbers , break them down to simple identical problems using smaller numbers and reconstruct the final large answer.
---
# Adrien's signs

