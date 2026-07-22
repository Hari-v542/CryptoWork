# Quadratic residue - perfect square

## equation [ a**2 = x mod (y) ]

a is the number from 0 to y-1 and if any of those numbers after quating  equals to x, x is a quadratic residue. and its square root is a.

```python
a = [14,6,11]
count =0
for x in a:
    for i in range(29):
        if (i**2)%29 == x:
            print (i,x)
            break
```
output - <img width="757" height="36" alt="image" src="https://github.com/user-attachments/assets/8dd2cbee-b682-4e2f-8c2e-beab9211258e" />

