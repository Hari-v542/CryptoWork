
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
