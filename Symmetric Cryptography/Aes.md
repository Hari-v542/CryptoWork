
# AES notes

https://www.youtube.com/watch?v=gP4PqVGudtg

- the plain text is seperated into 16 bytes or 128 bits, it is converted into its hexadecimal byte form and then added to a 4x4 matrix column by column (column major order).

``` python
def bytes2matrix(text):
    return [list(text[i:i+4]) for i in range(0, len(text), 4)]

def matrix2bytes(matrix):
    string =""
    for i in matrix:
        for j in i:
            string = string+ chr(j)
    return string
    

matrix = [ 
    [99, 114, 121, 112],
    [116, 111, 123, 105],
    [110, 109, 97, 116],
    [114, 105, 120, 125],
]

print(matrix2bytes(matrix))
```

Output - crypto{inmatrix}

--- 
Code:
``` python


state = [
    [206, 243, 61, 34],
    [171, 11, 93, 31],
    [16, 200, 91, 108],
    [150, 3, 194, 51],
]

round_key = [
    [173, 129, 68, 82],
    [223, 100, 38, 109],
    [32, 189, 53, 8],
    [253, 48, 187, 78],
]

def add_round_key(s, k):
    final=[]
    xored=[]
    
    for i in range(len(s)):
        row =[]
        for j in range(len(s[i])):
            xored = s[i][j]^k[i][j]
            row.append(xored)
        final.append(row)
    return final

def matrix2bytes(x):
    string =""
    for m in x:
        for n in m:
            string = string+ chr(n)
    print(string)

matrix2bytes(add_round_key(state,round_key))


```
Output - crypto{r0undk3y}
