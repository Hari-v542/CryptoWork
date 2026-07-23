# Quadratic residue - perfect square

## equation [ a**2 = x mod (y) ]


a is the number from 0 to y-1 and if any of those numbers after equating  equals to x, x is a quadratic residue. and its square root is a.



<img width="1013" height="112" alt="image" src="https://github.com/user-attachments/assets/82b7b45e-c509-4ba6-9de5-151eeef92700" />



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


