![image](https://user-images.githubusercontent.com/63996033/207787919-fc983e55-f297-49f1-ba3a-cf2abce06bf2.png)

Connecting to the netcat server shows us a flag validation program, giving us a float percentage value for each character that we get correct. Basic bruteforce script needed for this.

![image](https://user-images.githubusercontent.com/63996033/207981103-b4af9379-0f95-4daa-b97c-4a37552d29cb.png)

I created a script using pwntools. It takes about 10 minutes to run.

```py
from pwn import *
context.log_level = 'error'

import string

a = string.digits + '{_}' + string.ascii_letters

flag = b'HCTF'
points = 0.11764705882352941

for i in range(100):
        for x in a:
                p = remote('hctf.hackappatoi.com', 9001)
                p.readline()

                p.writeline(flag + bytes(x, 'utf-8'))

                d = float(str(p.readline(),'utf-8'))
                if d > points:
                        points = d
                        flag += bytes(x, 'utf-8')
                        print(str(flag,'utf-8'))
                        break

                p.close()

                    
```

![image](https://user-images.githubusercontent.com/63996033/207983598-4a000d5a-6c67-4b98-9078-c726dc7b7598.png)

Flag: HCTF{wh4t5_yo0r_4lch0l_p3rc3nt4g3}
