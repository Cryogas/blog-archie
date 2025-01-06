+++
title = "DownUnderCTF24 Writeup"
date = '2024-07-07T09:13:25+08:00'
draft = false
description = ""
tags = ["CTF", "Cybersecurity", "Writeup"]

+++

{{< callout emoji="⚡️" text="DownUnderCTF, the Largest CTF in the Southern Hemisphere!" >}}


The challenges in this CTF are hard! But I managed to solve some of the easier challenges, so here is my writeup for DownUnderCTF!

# MISC

## Discord

The challenge requires us to get the flag in Discord server. 

To do this, we just search for "DUCTF" in the Discord chat.


{{< figure src="content/ductf24/discord1.png" title="Found Part 1" >}}

Looking around for some time, but could'nt find the second part.. 

Wait a minute, might be sent by the same guy..
{{< figure src="content/ductf24/discord2.png" title="Gotcha!" >}}

FLAG: DUCTF{f1r57_0f_m4ny}

---



## tldr please summarize

A docx file is attached, might be hiding some kind of secret message.

{{< figure src="content/ductf24/tldr1.png" title="Test" >}}

{{< figure src="content/ductf24/tldr2.png" title="Some of the content in the docx file" >}}

The passage is so long, so I did not bother to read. 

As I scroll through the document, something caught my attention. Abnormal tiny wavy lines at the bottom. 

{{< figure src="content/ductf24/tldr3.png" title="Sus..." >}}

I selected all and changed the font color, which reveals the actual hidden text. 
{{< figure src="content/ductf24/tldr4.png" title="" >}}

Looks like a shell script. After executing the script in Kali Terminal, the flag is found!

{{< figure src="content/ductf24/tldr5.png" title="Open /temp.sh " >}}

FLAG: DUCTF{chatgpt_I_n33d_2_3scap3}

---

# Crypto


## Sun Zi's Perfect Math Class 

A webpage link is embedded, which brings us to a webpage to solve a math question.

{{< figure src="content/ductf24/sz1.png" title="" >}}


{{< figure src="content/ductf24/sz2.png" title="The question" >}}

Sun zi reminds me of Chinese Remainder Theorem I read the other day. I have put the solution below,
{{< figure src="content/ductf24/sz3.png" title="How I get the minimum value of n" >}}

The question states that the number of soldiers is between 1000 and 1100, in order to find n, we can keep adding (3 * 5 * 7) to 194, so that n fulfills the 3 modulo equations.

We will get 194, 299 ... 929, 1034, 1139,....

Therefore the answer is 1034 😊

{{< figure src="content/ductf24/sz4.png" title="The answer is correct!" >}}

Wait, there is a part 2...


---

## shufflebox

For this challenge, a shuffled code is given to us to recover the message

{{< figure src="content/ductf24/shuffle.png" title="The answer is correct!" >}}
I have done a challenge which looks like this before: [awa-jelly](https://cryogas.github.io/content/vsctf/)

Therefore, I'll just find out the sequence and recover the flag.

FLAG: DUCTF{udiditgjwowsuper}

---

# OSINT

## offtheramp

This is an easy challenge, but for some reason, I am stuck for at least 5 hours...  🤦🏻 (Please read till the end to see how I wasted 5 hours 👍)



An image of a dock is given, requiring us to discover the name of the structure.


{{< figure src="content/ductf24/ramp1.png" title="" >}}
{{< figure src="content/ductf24/offtheramp.jpeg" title="" >}}

It all started when I saw hundreds of solves within the first few hours of the challenge's release...

Should be an easy question, right?

{{< figure src="content/ductf24/nope.jpg" title="(For me 🤡)" >}}

First approach:

Just look around the whole Australia for docks on Google Maps, because how hard can it be? 

Turns out it is very hard... and not very practical..

Second approach: 

Google Lens

It doesn't really return good results until I found the small image in this article: 

{{< figure src="content/ductf24/frankston.png" title="" >}}

Frankston.. let me look around the area..

After some searching around, I found the exact view from Google Maps.



{{< figure src="content/ductf24/ramp3.png" title="" >}}
{{< figure src="content/ductf24/ramp4.png" title="The exact same spot?" >}}

I entered State_Road_3 as the flag, but the answer is wrong.. damn


I asked the mods for help, turns out I was at the right place all along, now I just need to find the name of the STRUCTURE.

{{< figure src="content/ductf24/rm.png" title="" >}}

{{< figure src="content/ductf24/rm2.png" title="The struggle is REAL" >}}

After changing it back to street view, I finally found the "structure"...

{{< figure src="content/ductf24/ramp5.png" title="" >}}
{{< figure src="content/ductf24/rm3.png" title="FINALLY!" >}}




>After reading the official writeup,   
> Turns out the exact coordinates of the location can be found using EXIF Tools..  
>   GOD WHYY U DO THIS TO ME??

{{< figure src="content/ductf24/exif-ramp.png" title="How to save 5 hours of life" >}}

{{< figure src="content/ductf24/why.jpg" title="This is me after reading the writeup" >}}
{{< figure src="content/ductf24/raccoon.jpg" title="I am a clueless rakun" >}}

> Pondering life and the decisions that led you to this point.    
>-sir nosurf  
>
>Now I understand what you meant by then 🤡

FLAG: DUCTF{Oliver_Hill_Boat_Ramp}

--- 

## cityviews

An image is given to determine where the photo is taken.


{{< figure src="content/ductf24/cityviews.jpeg" title="" >}}


First thing I noticed is the brand logo that looks like a blue palm.

By utilizing Google Images, I found a [page](https://grimshaw.global/projects/workplace/699-bourke-street/) which resembles the logo, and the address is at 699 Bourke Street, and the logo is AGL's logo.
{{< figure src="content/ductf24/city1.png" title="" >}}

After fiddling around with Google Maps Satelite View, I managed to get an angle that resembles the image, with the advertisement screen and the old building.

{{< figure src="content/ductf24/city2.png" title="" >}}

Looking at the picture, there is this high-arch windows, which can be found on the street view of 575 Flinders Ln.
{{< figure src="content/ductf24/city4.png" title="Almost there!" >}}

I tried using Holiday Inn as the flag, but it was wrong. 

After a few guesses, I found the flag!


{{< figure src="content/ductf24/city6.png" title="" >}}

FLAG: DUCTF{Hotel_Indigo}

---

## Bridget Lives 

An image was given for us to find where the photo is taken.

{{< figure src="content/ductf24/bridget.png" title="" >}}

By using Google Images, the most relevant result is Jiak Kim Bridge in Singapore, but after closely examining it, the bridge in the given image is completely different from the Jiak Kim Bridge. 

Just keep looking.. 

Finally I found a result, which may be the solution!

{{< figure src="content/ductf24/bridge1.png" title="" >}}

After watching the video, I am now 100% sure this is the place!
{{< figure src="content/ductf24/bridge2.png" title="Robertson Bridge" >}}
So the flag is the building next to it, which is Four Points by Sheraton.

{{< figure src="content/ductf24/bridge3.png" title="A better view" >}}

FLAG: DUCTF{Four_Points}

--- 

## back to the jungle

MC Fat Monke just dropped a new track???

I googled online for this infamous artist, and here are the results.

{{< figure src="content/ductf24/back1.png" title="" >}}

The YouTube [Link](https://www.youtube.com/watch?v=jmhn3IMLQyM) leads us to a sick mixtape. 

The key to the flag is at 2:34 of the video, where there is a [link](https://average-primate-th.wixsite.com/mc-fat-monke-appreci) to another website.

{{< figure src="content/ductf24/back2.png" title="" >}}
The flag is in plain sight after the page is loaded!

{{< figure src="content/ductf24/back3.png" title="" >}}

FLAG: DUCTF{wIr_G0iNg_b4K_t00_d3r_jUNgL3_mIt_d15_1!!111!}

--- 

## They're Making Decoys

This is my favorite OSINT challenge because it is relatively hard.

An image is given for us to find the coordinates of the location (rounded in 4 decimal places) of the "fake" emus.

{{< figure src="content/ductf24/decoys.png" title="" >}}

I have searched for some keywords such as "fake emus", "emu metal statue" and "emu metal", but it doesn't give me any significant results, until I found this post...
{{< figure src="content/ductf24/emu.png" title="" >}}
{{< figure src="content/ductf24/emu1.png" title="Cool looking decorations" >}}

Looks like what we are looking for..

The post says the sculptures are at East of Tailem Drive, therefore, I used Google Street View to search the area, till I found the exact spot! 

{{< figure src="content/ductf24/emu2.png" title="Found them!" >}}

FLAG: DUCTF{-29.5506,153.2777}

---

## marketing 

{{< figure src="content/ductf24/mkt1.png" title="" >}}

Google for MC Fat Monke again, this time we found a X (Twitter) Post under DownUnderCTF's account.

The flag is actually here if you observe carefully...

{{< figure src="content/ductf24/mkt2.png" title="" >}}

Can't see it? Let me show you.
{{< figure src="content/ductf24/mkt3.png" title="Top left corner" >}}

FLAG: DUCTF{doing_a_bit_of_marketing}

### Perfect clear for OSINT challenges!
{{< figure src="content/ductf24/all.png" title="🥳" >}}

# Conclusion

The challenges this year were fantastic, especially 'offtheramp', which is an experience I will never forget for the rest of my life (and all the time spent on it that I'll never get back 🥲).


Its a long writeup, I hope you enjoyed reading them! 







