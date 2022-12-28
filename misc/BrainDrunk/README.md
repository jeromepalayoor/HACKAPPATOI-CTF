![image](https://user-images.githubusercontent.com/63996033/209690293-25ae32c4-a4e4-453b-9909-9eb7cf786374.png)

If you notice the emojis in the attachment, there is only siz types of them, and the title indicates that it is Brainfuck language which has similar usage. So probably we need to figure out which emoji is which character and replace it and run the brainfuck code?

After trial and error, I got thi combination and put it in a script.

```py
with open('attachment.txt', 'r', encoding='utf8') as f:
    data = f.read()

for i in data:
    if i == '🥂':
        print('>', end='')
    elif i == '🍾':
        print('.', end='')
    elif i == '🍷':
        print('-', end='')
    elif i == '🍸':
        print('[', end='')
    elif i == '🍹':
        print('<', end='')
    elif i == '🍺':
        print('+', end='')
    elif i == '🥃':
        print(']', end='')
```

![image](https://user-images.githubusercontent.com/63996033/209690842-6b2b3cf5-69e0-4769-b0ea-33bca1b5ce82.png)

I put it in an online compiler.

![image](https://user-images.githubusercontent.com/63996033/209827722-c6f4f93f-56ff-4790-ba63-31aef715b5d0.png)

However the output does not give the flag, but the memory does.

![image](https://user-images.githubusercontent.com/63996033/209827800-5c956e50-e674-4327-9329-46bea73fa3e8.png)

The memory shows part of the flag but it is changed to show the output so need to view memory in real time while program is running.

Can use [this](https://brainfuck.michd.me/) tool to stop mid way to find the memory which reveals the flag.

Flag: HCTF{D0nt_c0d3_1f_y0u_4R3_s0b3R}
