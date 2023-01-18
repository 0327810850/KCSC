![image](https://user-images.githubusercontent.com/82592489/213149310-ff7c6fd2-9623-4792-9b29-72670a636e89.png)



Ý tưởng: giống bài split-strings

code:

```py
from pwn import *
def printMaximum(num):

# Hashed array to store count of digits
    count = [0 for x in range(10)]

    # Converting given number to string
    string = str(num)

    # Updating the count array
    for i in range(len(string)):
        count[int(string[i])] = count[int(string[i])] +  1

    # Result stores final number
    result = 0
    multiplier = 1

    # traversing the count array
    # to calculate the maximum number

    for i in range(10):
        while count[i] > 0:
            result = result + ( i * multiplier )
            count[i] = count[i] - 1
            multiplier = multiplier * 10

    # return the result
    return result
# a = '14359125086763140301'

# print(printMaximum(a))

r = remote("146.190.115.228",10464)
a = r.recvuntil(b'\n', drop= True).decode()
print(a)
b = str(printMaximum(a[8:])).encode()
print(b)

r.sendline(b)
# print(r.recv())
while(1):
    r.recvline()
    a = r.recvuntil(b'\n', drop= True).decode()
    print(a)
    b = str(printMaximum(a[8:])).encode()
    print(b)
    r.sendline(b)

```


flag: KCSC{You will maximize yourself when participating in KCSC, G00d_j0b}
