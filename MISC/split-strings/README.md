![image](https://user-images.githubusercontent.com/82592489/213146990-ef686632-f628-43fe-b4ab-fad480117364.png)





Ý tưởng: dùng hàm split() trong module wordninja.



```py
from pwn import *
import wordninja
r = remote("159.89.197.210",10463)
a = r.recvuntil(b'\n')
print(a)
c = " ".join(wordninja.split(a[9:].decode()))
print(c.encode())
r.sendline(c.encode())
while(1):
    # r.recvuntil(b":")
    r.recvline()
    a = r.recvuntil(b'\n')
    print(a)
    c = " ".join(wordninja.split(a[9:].decode()))
    print(c.encode())
    r.sendline(c.encode())
    
r.interactive()
```

flag: KCSC{Looks like you know how to use that tool, nice hecker}
