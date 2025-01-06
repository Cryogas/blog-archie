+++
title = "USC CTF Writeup"
date = '2024-11-03T07:32:05+08:00'
draft = false
description = "Writeup for USC CTF"
tags = ["CTF", "Cybersecurity", "Writeup"]

+++

# Introduction
{{< figure src="/content/uscctf24/logopic.png" title="" >}}

Over the weekend, I had participated in USC CTF hosted by University of Southern California.
Here are some writeup of challenges I managed to solve.
{{< figure src="/content/honest.jpg" title="It's honest work" >}}

# Concoction (rev)
Finally my first rev writeup! (it's a beginner's challenge 😅)  
{{< line_break >}}
An executable file is given, asking for some ingredients to craft a potion.

To solve the challenge, use Ghidra to view the decompiled code. There are a lot of if-else conditions. However,to print the flag, variable bVar1 must be true. 

{{< figure src="/content/uscctf24/con1.png" title="Standard input and the corresponding variables" >}}

{{< figure src="/content/uscctf24/con2.png" title="Condition to change bVar1 to true" >}} 

The conditions to get bVar1 == true is given, therefore, convert the hex values of each corresponding variable into decimal format and insert them when prompted. 

```
- local d0 (crypto crickets) = 7914
- local cc (forensic fungi) = 111100
- local c8 (osint oreos) = 2310
- local c4 (plants of pwn) = 51337
- local c0 (rev redcaps) = 42154142
- local bc (cobwebs) = 9111
- local b8 (ounces of water) = Any number greater than 1 will do  
```

Variable b8 is not a condition, therefore, any value will do as long as it is greater than 0.  
The string input prompt in the end must be "decompiler" as it is also one of the conditions.

Solved!

{{< figure src="/content/uscctf24/con3.png" title="Example of values input(ounces of water does not matter)" >}}

FLAG: CYBORG{RECIPE=7914-111100-2310-51337-42154142-9111-decompiler}

# Tommy's Artventures (Web)
{{< figure src="/content/uscctf24/tom1.png" title="" >}}

An URL is given, which redirects to an AI art page. In order to login to the page, create an temporary account. 
{{< figure src="/content/uscctf24/tom2.png" title="Login Page" >}}

During the navigation to "curate" page, a messaged shown indicating the login user must be admin.
{{< figure src="/content/uscctf24/tom3.png" title="Message in Curate page" >}}

Based on the secret key attached in the challenge, it is clear that reforging of the session cookie is required. Firstly, copy the cookie from "Inspect > Application and decode the cookie to check the format. (There is another way using Burpsuite, but I am not sure how 😅)

{{< figure src="/content/uscctf24/tom4.png" title="Find the cookie in \"Inspect\"" >}}


To create a new cookie, I used this [website](https://book.hacktricks.xyz/network-services-pentesting/pentesting-web/flask) as a reference, and the CLI command is attached below. (Remember to install the tool first)

```
pip3 install flask-unsign

flask-unsign --sign --cookie "{'user': 'admin'}" --secret 'THE-SECRET-KEY'
```

After changing the forged cookie, the session is currently logged in as admin, and the flag is found in the 'curate' page.

{{< figure src="/content/uscctf24/tom5.png" title="Decode and sign cookie using flask-unsign tool" >}}

{{< figure src="/content/uscctf24/tom6.png" title="Successfully logged in as admin" >}}

{{< figure src="/content/uscctf24/tom7.png" title="Flag is shown in \"Curate\" page." >}}

FLAG: CYBORG{oce4n5_auth3N71ca7i0N}


# Buildings (OSINT)
A pdf file was attached with contents of buildings, and I assumed that these buildings are in USC.

The flag format is CRYPTO, therefore no investigation is needed for the first 6 pictures (pictures before the curly braces).

These are the names of the buildings for the flags, index them accordingly using their acronyms, and the flag is found!
{{< figure src="/content/uscctf24/building1.png" title="BRI" >}}
{{< figure src="/content/uscctf24/building2.png" title="CKS" >}}

FLAG: CRYPTO{BRICKS}

# RedWoods (misc)


{{< figure src="/content/uscctf24/red1.png" title="" >}}

A .jar file is attached.

Use WinRAR to unzip the jar file. There are 3 files inside.

To open the class file, use an [online Java decompiler](http://www.javadecompilers.com/) to decompile and view the Main.class file.

{{< figure src="/content/uscctf24/red2.png" title="Decompiled code" >}}


After going through the code, the code does nothing much by just printing out the message in the flags array. Therefore, the flag is assumed to be in this array.

```java
static String[] flags = new String[]{"ccccccccccagccccccchdbgdddehcccccagcccchdbgccehcccccagddddhdbgdddehgcccccccccccccecccedddddddd", "dddeagcgchhdbcccccagcccccccccchdbgccegcedddeddddeccccccccccccccccceddddddddddddddehhccccccaggccccchhdbggdddeddddddddddde", "ddehhccccccaggdddddhhdbggdeehhcccccccccccaggcccchhdbggehhcccccaggdddddhhdbggeagcgchhdbabccccccaggdddhhdbggehcccccceehhcce"};
```

Combine all three array elements together to form a long string. However, the string does not mean anything after analyzing with Cipher Identifier. 

Next, use AperiSolve to analyze the image. There is a hidden message. By looking at the symbols, it is easily identified as the Brainfuck cipher.
{{< figure src="/content/uscctf24/red3.png" title="Hidden message (Is it the reason of the naming for the challenge?)🤔" >}}

Use any word editor to replace the alphabets with the symbol given, and decrypt the new ciphertext. The flag is found!

Brainfuck message as below:
```
++++++++++[>+++++++<-]>---.<+++++[>++++<-]>++.<+++++[>----<-]>---.<>+++++++++++++.+++.-----------.[>+>+<<-]+++++[>++++++++++<-]>++.>+.---.----.+++++++++++++++++.--------------.<<++++++[>>+++++<<-]>>---.-----------.--.<<++++++[>>-----<<-]>>-..<<+++++++++++[>>++++<<-]>>.<<+++++[>>-----<<-]>>.[>+>+<<-][]++++++[>>---<<-]>>.<++++++..<<++.
```

{{< figure src="/content/uscctf24/red4.png" title="Decrypted Message" >}}

FLAG: CYBORG{HEARD_TR33_F4LL}

{{< line_break >}}

# Conclusion

Overall, the CTF contains various challenges suitable for players from different levels. Some challenges were really out of my knowledge.  I will try to understand them and do better next time. (I got rank 79th btw)
{{< line_break >}}
Anyway...
<!-- {{< figure src="/content/uscctf24/" title="" >}}
{{< figure src="/content/uscctf24/" title="" >}} -->
{{< figure src="/content/uwma.gif" title="" >}}