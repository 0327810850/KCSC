




![image](https://user-images.githubusercontent.com/82592489/213141280-45d033a1-42ab-430b-900c-64cff66474c4.png)


Ý tưởng: lấy bitwise của 2 ảnh.


Code:

```py
from binascii import unhexlify

with open("1.jpg", mode='rb') as fl:
    lemur = fl.read()
    

with open("2.jpg", mode='rb') as ff:
    flag = ff.read()

d = b''
for b1, b2 in zip(lemur, flag):
    d += bytes([b1^b2])

with open("new.jpg", mode='wb') as fn:
    fn.write(d)
```
Vứt vào wireshank hay ida để lấy flag.
flag: KCSC{Da_bao_roi_cu_x%r_tung_byte_la_ra_ma_li}

