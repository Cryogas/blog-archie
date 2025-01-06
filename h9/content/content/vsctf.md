+++
title = 'VSCTF Awa-Jelly Writeup'
date = 2024-06-20T11:32:57+08:00
draft = false
description = 'Awawa'
pygmentsstyle = "monokai"
pygmentscodefences = true
pygmentscodefencesguesssyntax = true
tags = ["Writeup"]

[params]
    author ="h9"

+++

For this CTF, I only solved one question by myself, so here is the writeup for awa-jelly (reverse engineering)


![Image](/content/vsctf/image.png)

Basically, the challenge is to recover the redacted input text so that the output is same as displayed.  



Although I know Python a little, I decided to use the traditional method: Excel 🤦🏻

Throughout my process, I tried to recover the scrambling algorithm by using Python, and I discovered some characters cannot be displayed after scrambling, which caused my natural approach to be weird due to some characters are missing.

![Image](/content/vsctf/image-1.png)


By removing those letters, I understood the scramble method, all that is left to do is to reassemble the sequence of the output text of the picture above. Here are the results.

![Image](/content/vsctf/image-2.png)

## Ps: Finally, I am able to code something that return the same results!

```python 
# Determine the sequence of indexes after scrambled

input = "1234567890_wrtyuioasdfghjlcbnm,."
output = "u_ioasd3fg6h9jwl52cb7nm,.t1480ry"


lis = []

# List of index after scrambled
seq = []

for i in input:
    lis += i 

for i in output:
    for j in lis:
        if i == j:
            seq.append(lis.index(j))

print(f"seq = {seq}")

loli = "1o1i_awlaw_aowsay3wa0awa!iJlooHi"

redacted = ""

o = 0

while o < len(loli) - 1:
    for i in seq:
        if i == o:
            redacted += loli[seq.index(i)]
            o += 1

print(f"Recovered string is {redacted}")    
```
Flag: vsctf{J3lly_0oooosHii11i_awawawawaawa!}