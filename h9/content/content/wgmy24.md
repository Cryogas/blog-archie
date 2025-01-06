+++
title = "WGMY 2024 Writeup"
date = '2024-12-29T09:16:50+08:00'
draft = false
description = ""
tags = ["CTF", "Cybersecurity", "Writeup"]

+++

# Introduction

{{< figure src="/content/wgmy24/logo.jpg" title="" >}}

This is my first time participating in wargames.my.  
{{< line_break >}}
Due to some time management issues, I started to solve the challenges 3 hours before the competition ends. Nevertheless, here are my write-ups for 2 easy challenges.
{{< figure src="/content/honest.jpg" title="It's honest work" >}}

# The DCM Meta (Easy)

This challenge was supposed to be easy, but I managed to not solve it because one minor error in my code. 🤦🏻 (I set i < 31 , which made my flag length is less by 1)

Here is the corrected code for your reference.

```python

scramble = "f63acd3b78127c1d7d3e700b55665354"

sequence = [25, 10, 0, 3, 17, 19, 23, 27, 4, 13, 20, 8, 24, 21, 31, 15, 7, 29, 6, 1, 9, 30, 22, 5, 28, 18, 26, 11, 2, 14, 16, 12]

# print(len(scramble))

i = 0 
seq_i = 0
solved = []

while i < 32:
    solved += scramble[sequence[seq_i]]
    seq_i += 1
    i += 1
    

solved = "".join(solved)
print(f"wgmy{{{solved}}}")
    

```

{{< line_break >}}

--- 

# Unwanted Meow (Medium, but actually easy)

After inspecting the bytes in the attached file, there are a lot of "meow"s which corrupts the file. I tried replacing them using hexed.io but it will take a long time.
{{< figure src="/content/wgmy24/meow-hex.png" title="So many meow meow" >}}

{{< line_break >}}

Then I realized.. why not use Cyberchef? 

{{< line_break >}}

By using the "Find/Replace" function and using the magic wand immediately, a sorta distorted image is recovered. I tried to submit the flag consisting of the viewable letters, and it's not the correct flag.
{{< figure src="/content/wgmy24/cacat-meow.png" title="Why u cacat bro?" >}}

The reason of this phenomenon is there are still "meow"s concealed due to the challenge creator's smart method of wrapping a meow within another meow.

{{< figure src="/content/wgmy24/concealedmeow.png" title="Meow in the meow!" >}}
{{< line_break >}}
To overcome this issue,  I tried to replace input with output first before rendering the image to ensure the outer layer "meow"s are also removed.

Finally the image is restored successfully.
{{< figure src="/content/wgmy24/ok-meow.png" title="Restored!" >}}



# Conclusion

I lied actually about the starting time in the introduction. I was stuck doing the blockchain challenge in the morning causing me to give up midway. However, I continued to solve challenges at night due to the love of the game (plus I can't sleep after a long nap in the afternoon)


{{< line_break >}}

See ya!
